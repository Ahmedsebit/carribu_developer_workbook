# Carribu Developer Playbook

**Status:** Proposed team policy, pending engineering-owner approval.

**Scope:** All Carribu application repositories and this documentation repository.

This playbook defines day-to-day contribution rules. The [handover and onboarding guide](CARRIBU-HANDOVER-AND-ONBOARDING.md) remains the reference for domain invariants, learning plans and operational readiness. Component READMEs and manifests define actual setup/build commands. Existing component conventions take precedence over naming defaults below; agree changes with the component owner rather than renaming unrelated code.

These are documented requirements, not evidence that GitHub protections, CI, ownership or deployment gates have been configured. Repository administrators must inventory and activate applicable controls before calling them enforced.

## 1. Ownership and working agreements

| Rule | Expectation |
|---|---|
| Accountable ownership | Each repository has a named primary owner, backup and release owner recorded in its README or approved ownership directory |
| Work tracking | Start from an issue with purpose, acceptance criteria, risk and affected components; create an incident work item for urgent fixes |
| One objective | Keep each PR independently understandable; separate unrelated refactors, formatting and dependency upgrades |
| Coordination | Agree cross-repository API and rollout changes with backend, web and mobile owners before implementation |
| Blockers | Record impact and the decision needed in the work item; escalate blocked delivery or unsafe behavior promptly |
| Decisions | Record significant architecture, compatibility or operational decisions with context, alternatives and consequences in the owning repository |
| Exceptions | Record the rule, reason, approver, compensating safeguards, expiry and follow-up issue; do not silently bypass policy |

Use synthetic accounts and a local/staging environment for development. Do not run training or test automation against production.

## 2. Git workflow

Use short-lived branches into `main`. Do not introduce permanent `develop`, personal integration or release branches by default. Keep `main` releasable: merging code does not itself authorize a production release.

1. Confirm the repository, inspect local changes and fetch the latest remote state.
2. Create a branch from current `origin/main` for one tracked objective.
3. Implement a bounded change with relevant tests and documentation.
4. Push the branch and open a draft PR early when feedback or coordination is needed.
5. Mark ready only when acceptance evidence and review information are complete.
6. Resolve feedback, obtain required approvals and satisfy checks for the current PR head.
7. Squash merge through GitHub, then delete the remote branch. Record release status separately.

Aim to complete a branch within two working days. If work will take longer, agree reviewable slices or a disabled-by-default feature flag with the owner. Never merge incomplete unsafe behavior merely to meet this target. Track flag ownership and removal.

### 2.1 Branch names

Format: `<type>/<issue-number>-<short-kebab-case-description>`.

Use lowercase ASCII letters, numbers and hyphens within the description. Use the issue number in the repository containing the change; link related repositories' issues in the PR. If an external tracker is authoritative, use its agreed lowercase key instead of inventing a GitHub number.

| Type | Use | Example |
|---|---|---|
| `feat` | New capability | `feat/142-parent-trip-history` |
| `fix` | Correct existing behavior | `fix/156-reject-cross-school-access` |
| `hotfix` | Urgent production correction | `hotfix/161-notification-retry` |
| `refactor` | Restructure without intended behavior change | `refactor/170-extract-trip-validation` |
| `docs` | Documentation | `docs/175-driver-setup` |
| `test` | Tests without production behavior changes | `test/180-gps-age-boundaries` |
| `chore` | Maintenance or dependency updates | `chore/185-update-http-client` |
| `ci` | CI configuration | `ci/190-backend-checks` |
| `perf` | Performance improvement | `perf/195-index-trip-history` |
| `build` | Build or packaging configuration | `build/198-android-release-signing` |

Do not use names such as `ahmed-work`, `latest`, `final-fix` or `test-branch`. Do not include student, guardian, school customer or credential data in branch names.

### 2.2 Commits and PR titles

Use Conventional Commit format: `<type>(<scope>): <imperative summary>`. Scope is optional when no useful component scope exists.

Allowed types: `feat`, `fix`, `docs`, `refactor`, `test`, `chore`, `ci`, `perf`, `build`, `revert`. A `hotfix` branch still uses `fix` in the commit and PR title.

```text
feat(parent): add completed trip history
fix(api): reject trip completion with students on board
test(location): cover GPS freshness boundaries
docs(playbook): define branch and review rules
```

Use a specific imperative summary, no trailing full stop, and aim for a subject of at most 72 characters. Use a body for motivation, tradeoffs and issue references. Never put secrets or personal data in commit messages.

For a breaking contract change, use `!` after the scope/type and explain the impact and migration in a `BREAKING CHANGE:` body/footer:

```text
feat(api)!: replace legacy trip response

BREAKING CHANGE: remove legacy trip fields after the approved client transition.
```

Prefer compatible additive API changes; this syntax does not authorize breaking deployed clients.

Keep commits coherent. Local work-in-progress commits are acceptable on a feature branch, but clean up their titles before review. The PR title and final squash commit must follow the convention. The merger must inspect GitHub's generated squash message and remove misleading intermediate messages.

Link the issue in the PR. Use `Closes #142` only when that PR completes the issue; otherwise use `Refs #142`. For cross-repository work, use full issue URLs and do not close the parent delivery item until all required changes are accepted.

### 2.3 Safe Git habits

- Inspect `git status` and the diff before staging. Prefer explicit file paths and inspect `git diff --cached` before every commit.
- Never push directly to `main`, force-push protected branches, rewrite published tags or amend another developer's commits.
- Rebase only your own unshared feature branch. If it has already been pushed, coordinate first and use `--force-with-lease`, never plain `--force`. New commits invalidate previous review evidence where relevant.
- For a branch others use, merge `origin/main` instead of rewriting its history. Do not resolve conflicts by blindly taking one whole side; inspect intent and rerun affected checks.
- Never discard another person's changes. Avoid destructive reset/clean commands unless the exact scope and recovery plan are understood and approved.
- Use a reviewed revert PR to undo merged code. Do not erase shared history to hide a mistake.
- Commit source and required lockfiles, not `node_modules`, build outputs, local environment files, private signing material or production exports. Keep necessary exceptions explicit in the component README.

Example PowerShell workflow, run inside the relevant repository with a clean worktree. Replace the sample issue, branch and file names:

```powershell
git status --short --branch
git fetch origin
git switch --no-track -c feat/142-parent-trip-history origin/main

# Implement the change and run the component's documented checks.
git diff --check
git diff
git add -- src/screens/TripHistoryScreen.js
git diff --cached
git commit -m "feat(parent): add completed trip history"
git push -u origin feat/142-parent-trip-history
```

The explicit `--no-track` avoids configuring a new feature branch to track `origin/main`. If any command fails, stop and resolve it before continuing. After merge, fetch and prune remote references; delete the local branch only after confirming its changes were squash-merged. Git may not recognize a squash merge with `git branch -d`; do not force-delete an unverified branch.

## 3. Pull requests and reviews

### 3.1 PR description template

Copy this into the PR description and replace every placeholder:

```markdown
## Purpose and linked work
Issue:
Problem and intended outcome:

## Changes and boundaries
What changed:
What is intentionally not included:
Affected repositories/clients and linked PRs:

## Evidence
Checks run and their results:
Acceptance cases, including rejection/failure paths:
Sanitized UI/device evidence when relevant:
Checks not run, reason, risk and owner:

## Rollout and recovery
API/configuration/migration impact:
Deployment order and compatibility:
Rollback or forward-fix plan:
Monitoring and release owner:
```

### 3.2 Review rules

| Area | Requirement |
|---|---|
| Standard changes | At least one approval from someone other than the author; no self-approval |
| High-risk changes | Two distinct non-author approvals, including an experienced owner of the affected area |
| High-risk scope | Authorization/tenancy, student/trip state, database migrations, payments if introduced, background location, notifications, signing, production configuration and destructive operations |
| Cross-component contracts | Review from affected component owners; a qualifying owner can count toward the required approvals |
| Review freshness | Relevant approvals and required checks must cover the latest meaningful change, not an earlier version |
| Conversations | Resolve blocking feedback with an explanation or code change; the author must not dismiss a correctness concern without agreement |
| Missing checks | Explicitly record missing automation and equivalent evidence; this is not permission to skip an existing required check |
| Merge responsibility | Merger confirms acceptance evidence, approvals, compatibility and the final squash message |

Review correctness, scope, tenant/role boundaries, concurrent/retried operations, error paths, data handling, accessibility and maintainability. Do not turn optional style preferences into blockers when code follows the repository's formatter and conventions.

Aim for first review within one working day. An approval means the reviewer understands the relevant change and evidence, not merely that the diff looks tidy. If staffing cannot meet the required approvals, escalate to the engineering owner and document an exception rather than self-approving.

### 3.3 GitHub configuration checklist

Repository administrators should configure and record these controls for `main` and protected release tags:

- Require PRs, applicable approvals, resolved conversations and fresh approval after changes; require approval by someone other than the latest pusher where supported.
- Require verified, repository-specific build/test checks. Select actual check names after successful CI runs; do not invent required contexts that block every PR.
- Require an up-to-date branch or a configured merge queue appropriate to the repository. Use squash merging; disable merge-commit and rebase merge options for PRs.
- Block force pushes and deletion of `main`; restrict release-tag creation, updates and deletion to release automation or authorized owners.
- Apply protections to administrators where supported. Limit bypass rights to named emergency owners and audit each use.
- Define real team/user ownership in `CODEOWNERS`, require code-owner review where supported, and protect changes to ownership, workflows and repository configuration.
- Enable available secret scanning, push protection and dependency alerts; review workflow permissions and use least-privilege tokens.
- Protect production deployment environments with approved reviewers and environment-scoped credentials; do not make a branch merge an uncontrolled deployment authorization.

One global approval count cannot express every risk-based rule. Enforce extra high-risk/affected-owner reviews with available rulesets or automation, or record them as manual gates. Record unsupported controls and compensating measures; documentation alone does not enforce them.

## 4. Code, file and API naming

Preserve established local conventions. Apply these defaults to new code where no convention exists; keep renaming-only work separate.

| Surface | Convention | Example |
|---|---|---|
| JavaScript variables/functions | Descriptive `camelCase`; verbs for actions | `schoolId`, `completeTrip()` |
| React components and their files | `PascalCase`; follow the local JSX/JS extension | `TripHistoryScreen.js` |
| React hooks | `use` prefix and `camelCase` | `useTripHistory()` |
| Classes and Kotlin/Swift types | `PascalCase` | `TripRepository`, `TripViewModel` |
| Kotlin/Swift functions/properties | `camelCase`; follow platform-specific conventions | `refreshTrips()`, `isLoading` |
| True shared constants/environment keys | `UPPER_SNAKE_CASE` where the language/project uses it | `GPS_MAX_AGE_MS`, `API_BASE_URL` |
| Booleans | State/question prefix, not ambiguous nouns | `isLoading`, `hasPermission`, `canEnd` |
| JavaScript modules | Existing repository naming pattern; no mixed conventions in one area | Follow neighboring controller/service files |
| Database | Existing `snake_case` tables/columns; Sequelize maps camelCase fields using `underscored: true` | `school_id` maps to `schoolId` |
| New HTTP resource paths | Lowercase plural nouns; kebab-case multiword segments; follow existing action conventions | `/api/trips`, `/api/route-students` |
| JSON fields | Existing contract's `camelCase`; do not rename a deployed field casually | `currentStop`, `schoolId` |
| Tests | Runner/platform's discovery pattern and a behavior-focused name | `TripLogicTest.kt`; follow existing JS test suffixes |
| Documentation | Descriptive names consistent with repository documentation | `DEVELOPER-PLAYBOOK.md` |

Use domain terms consistently: school, guardian/parent, student, route, trip, vehicle and stop. Avoid vague names such as `data2`, `tempManager` and `handleEverything`. Do not change wire enum values, table names, package names or application identifiers merely to satisfy a naming preference.

## 5. Implementation standards

- Keep routes thin; business rules belong in the established controller/service/domain layer. Backend authorization and school scoping must apply to every protected query and mutation, not just UI visibility.
- Reuse existing helpers and patterns. Prefer small cohesive functions and explicit dependencies over speculative frameworks or duplicated rules.
- Validate untrusted inputs at boundaries. Use proper types and guards where supported; do not suppress type errors or invent success-shaped fallback data.
- Handle failures visibly using the component's established error/logging/UI mechanisms. Do not swallow errors or expose stack traces and sensitive request contents to users.
- Preserve transaction boundaries, idempotency, ordering and concurrency guarantees. Clients must consume canonical backend trip state rather than invent competing progress logic.
- Show loading, empty, success, stale and error states where relevant. Check labels, keyboard/focus behavior, readable status and mobile touch targets.
- Put configuration in approved environment/build mechanisms. Document non-secret examples; do not hardcode a production secret or make local training depend on production.
- Update contracts, setup instructions and runbooks in the same change when their behavior changes. Comment only non-obvious intent and constraints.

## 6. Testing and definition of done

Use the [shared TDD and domain standards](CARRIBU-HANDOVER-AND-ONBOARDING.md#c2-tdd-red-green-refactor-in-daily-work). Reproduce bugs before fixing them; add a regression test that fails for the actual bug where feasible. Test observable outcomes, boundaries, rejected actions and recovery, not only happy paths.

| Changed surface | Expected evidence |
|---|---|
| Backend/domain | Relevant unit/integration cases; role and cross-school negative cases for access changes; real disposable PostgreSQL evidence for transaction/concurrency claims |
| Web/UI | Relevant tests/build and observed loading, empty and failure behavior; accessibility checks for affected interactions |
| Native/mobile | Relevant unit/build checks plus emulator/device acceptance for permissions, background execution, connectivity, signing, maps or push behavior as affected |
| Contract/migration | Compatibility evidence for supported clients, migration order and recovery evidence |
| Documentation only | Review accuracy, commands and internal links; run documentation checks if configured |

Use existing component scripts and committed lockfiles. Do not assume every repository has a test or lint script. Start with relevant checks and expand to affected builds/suites. Record pre-existing failures separately; do not hide new failures behind the baseline. Do not weaken assertions, disable checks or approve flaky tests as a substitute for diagnosis.

A change is done only when acceptance criteria are met, applicable evidence is recorded, required reviews are complete, documentation is current, and rollout/recovery responsibilities are explicit. If device or staging acceptance remains outstanding, label it accordingly; do not claim production readiness from a build alone.

## 7. Security, privacy and dependencies

Keep credentials, tokens, private keys, service-account files, signing material, production database exports and real student/guardian records out of Git, issues, PRs, logs, screenshots and unapproved AI tools. Use approved secret storage and least-privilege access. Sanitize diagnostic evidence before sharing.

If a secret is committed, stop distributing it and notify the responsible owner immediately. Revoke/rotate it first, assess exposure and dependent services, then coordinate repository-history cleanup if required. Deleting a file or reverting a commit does not remove a secret from history. Never rewrite shared history independently during an incident.

Commit required dependency lockfiles. Explain dependency additions, verify package identity and licensing, and review security/compatibility impact. Keep upgrades separate from feature changes unless required for that feature. Do not commit generated dependency directories or blindly accept automated upgrade PRs.

AI-assisted changes receive the same review and evidence as handwritten code. The submitting developer owns correctness and must be able to explain the code, tests and data flow.

## 8. Releases, tags and hotfixes

### 8.1 Version and release rules

Use SemVer release tags per application repository: `vMAJOR.MINOR.PATCH`, for example `v1.4.2`; use `v1.5.0-rc.1` for an explicitly identified prerelease. This documentation repository may tag approved policy snapshots if useful. Separate repositories version independently; do not imply that matching numbers make clients compatible.

Increment major for incompatible public contracts, minor for compatible features and patch for compatible fixes. For unreleased `0.x` components, explicitly document compatibility and breaking changes rather than implying stable guarantees. Mobile display versions and monotonically increasing build/version codes must also satisfy the relevant platform and store rules.

Only the designated release owner or approved automation creates and pushes an annotated release tag on the reviewed release commit. Confirm the tag matches the tested artifact and record the commit SHA. Never move or reuse a published tag; correct a release with a new version.

Before releasing, record:

- Included issues/PRs, affected components, supported clients and user-visible changes.
- Acceptance evidence, known limitations and the exact artifact/commit being released.
- Target environment, approvals, configuration and secret/signing references without values.
- Backend/migration/client rollout order and compatibility with apps already installed.
- Health signals, smoke checks, monitoring owner and criteria for stopping the rollout.
- Rollback or forward-fix steps, data implications and the responsible decision-maker.

Do not equate merging, tagging, deploying and user acceptance. Confirm the target deployment is healthy and the relevant user journey works. Database rollback may be destructive, and mobile users may retain old versions; plan recovery for each surface separately.

### 8.2 Hotfix procedure

Create `hotfix/<issue>-<description>` from `origin/main` when it is safe to release the current mainline. Keep the fix narrow, preserve review/check requirements and use an expedited review path with the incident owner.

If `main` contains changes that cannot safely ship, the release owner may approve a temporary branch from the deployed tag/commit. Record that exception and its exact base. Make the fix through a reviewed PR into that temporary branch, tag the new patch release, then promptly port the fix to `main` through a linked PR. Confirm both paths before removing the temporary branch.

An emergency does not authorize bypassing tenancy, forcing unsafe trip completion, exposing credentials or disabling constraints. Any protection bypass requires named authorization, an audit trail, recorded evidence and retrospective review by the next working day.

## 9. Incidents, communication and policy maintenance

Immediately escalate suspected cross-school access, exposed credentials, student-state corruption, incorrect trip completion, data loss, signing loss or unsafe deployment to the named incident/engineering owner. Record impact and sanitized evidence in the approved restricted channel. Preserve useful evidence; do not perform destructive production experiments or promise unverified recovery times.

The incident owner coordinates containment, customer communication, recovery approval and verification. Follow up with a blameless account of cause, impact, decisions and corrective actions with owners and dates. Use the [operational runbooks](CARRIBU-HANDOVER-AND-ONBOARDING.md#c7-operational-runbooks-and-incident-exercises), not improvised production edits.

Engineering owners review this playbook during onboarding, after significant incidents and when tooling or delivery practice changes. Changes to policy require a reviewed documentation PR. Record approval and effective date before treating this proposal as adopted, and track remaining GitHub/CI rollout work separately.
