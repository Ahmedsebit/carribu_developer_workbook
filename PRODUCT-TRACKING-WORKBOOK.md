# Carribu Product Tracking Workbook

**Status:** Reusable template; no live work has been entered.

Use this workbook to answer: **What are we working on, why does it matter, who owns it, what is blocked, and what is actually delivered?**

The [Developer Playbook](DEVELOPER-PLAYBOOK.md) defines contribution and review rules. This workbook connects product outcomes to that engineering work. It does not configure GitHub Projects, synchronize issues automatically or establish release approval.

Use the [Product Manager Workbook](PRODUCT-MANAGER-WORKBOOK.md) for whole-product strategy, portfolio priorities, quarterly expectations and launch decisions; link its product/objective IDs to delivery outcomes here.

## 1. How to use this workbook

1. The product owner records an outcome and creates a backlog item with a stable ID.
2. Before selecting work, agree its priority, acceptance criteria, accountable owner, affected components and dependencies.
3. Link implementation issues in their owning repositories. Use full GitHub URLs so identical issue numbers in different repositories are unambiguous.
4. At planning, select a realistic set of ready items and record the cycle goal. Do not treat the whole backlog as committed work.
5. Owners update status, blockers and the next action when something changes; check active items each working day.
6. During review, record acceptance evidence and release state separately. Archive completed cycles without deleting their decisions or evidence.

**Source of truth:** This workbook owns day-to-day cross-team work priorities within the agreed product direction, delivery outcomes, cycle planning and delivery summaries. The Product Manager Workbook owns portfolio priorities, quarterly expectations and launch decisions. Linked GitHub issues own implementation detail, discussion and acceptance criteria; PRs own code review evidence. If an issue does not exist yet, use the work-item template here. Link rather than maintaining competing copies of detailed checklists. Correct stale summaries when updating the workbook.

Use ISO dates (`YYYY-MM-DD`). Write `Not agreed` for an unapproved target, `Not assigned` for an unassigned owner, and `Not applicable` only when genuinely irrelevant. A target is a forecast, not an approved promise. Do not put credentials, real student/guardian records or sensitive customer/incident details in this file; link approved restricted records instead.

## 2. Ownership and current planning cycle

Fill these fields before treating the tracker as an active plan:

| Field | Value |
|---|---|
| Product owner / prioritization decision-maker | Not assigned |
| Delivery coordinator / workbook maintainer | Not assigned |
| Engineering leads / component owners | Not assigned |
| Cycle name and start/end dates | Not agreed |
| Cycle goal / intended user outcome | Not agreed |
| Available capacity and planned absences | Not agreed |
| Agreed work-in-progress limit | Not agreed |
| Last reviewed date | Not recorded |
| Next planning / review date | Not agreed |

The product owner orders the backlog and accepts product outcomes. Engineering owners assess feasibility, dependencies and risk. Each selected item needs one accountable delivery owner even when several developers contribute. The coordinator keeps the summary current; they do not replace item ownership.

## 3. Product outcomes and milestones

Track observable user outcomes rather than lists of screens or commits. Agree a success measure and baseline where useful; do not invent customer metrics or delivery dates.

| Outcome ID | User problem and intended outcome | Success measure / baseline | Accountable owner | Target milestone/date | Linked work IDs | Confidence and evidence |
|---|---|---|---|---|---|---|

Use stable IDs such as `OUT-001` for outcomes and `WORK-001` for work items. Allocate the next unused number; never recycle IDs or change them when priority changes. A milestone groups work around a demonstrable outcome, not merely a calendar deadline.

## 4. Product backlog

Keep one row per independently acceptable feature, bug, investigation or maintenance item. Split large initiatives into smaller items linked to a common outcome. Live tracking tables intentionally start empty; populated examples are kept separately in section 10.

| Work ID | Title / user value | Outcome ID | Type | Priority | Status | Owner | Components | Target milestone/date | Issue / detail link |
|---|---|---|---|---|---|---|---|---|---|

**Types:** Feature, Bug, Investigation, Maintenance, Documentation.

| Priority | Meaning |
|---|---|
| P0 - Critical | Active safety, privacy, security or service incident; escalate through incident ownership immediately |
| P1 - High | Essential to the agreed near-term outcome or a serious defect; product owner explicitly prioritizes it |
| P2 - Normal | Valuable planned work, ordered against available capacity |
| P3 - Later | Candidate improvement; not a delivery commitment |

Priority is not status. A high-priority item can still need clarification; do not start an unsafe or undefined implementation simply because it is urgent.

## 5. Status and readiness rules

| Status | Meaning / condition |
|---|---|
| Backlog | Captured but not yet selected or sufficiently defined |
| Ready | Acceptance criteria, owner, scope, dependencies and needed access are clear; delivery is feasible |
| In progress | An owner has started active implementation or investigation |
| In review | Relevant PRs or investigation results are ready for review, with evidence |
| In validation | Engineering review is complete; required integrated, product, staging or device acceptance remains |
| Done | Agreed acceptance criteria and applicable engineering gates are met, with evidence and acceptance recorded |
| Cancelled | No longer planned; record who decided and why |

Treat **blocked** as a flag alongside status, not a replacement for it: an item can be `In review` and blocked on a decision. Record each blocker below with an owner and next action. Reopen an item at the appropriate status when acceptance fails.

Before moving to Ready, confirm the problem, acceptance criteria, affected clients, dependencies, risk and verification approach. Before Done, link acceptance evidence and the accepting owner. A discovery task may finish with an agreed decision/report; a feature needs its specified behavior demonstrated. Release readiness still follows the playbook.

## 6. Current-cycle delivery board

Reference backlog IDs instead of duplicating titles and requirements. Add only items selected for this cycle. Update this summary and the backlog status together when changes occur.

| Work ID | Status | Owner | Next action | Blocked? / blocker ID | Latest issue/PR/evidence link | Last updated |
|---|---|---|---|---|---|---|

Respect the agreed work-in-progress limit. Finish or unblock started work before taking more items. If an urgent item displaces planned work, record which item moved and the decision-maker; do not silently expand the commitment.

### Blockers and dependencies

| Blocker ID | Affected work IDs | Dependency / decision needed | Resolving owner | Next action | Needed-by date | Status / resolved date |
|---|---|---|---|---|---|---|

Use `BLK-001` style IDs. Name dependencies precisely, including linked work IDs or external issue URLs. Escalate promptly when a blocker threatens the cycle goal; do not leave rows indefinitely at "waiting" without an accountable next action.

## 7. Work-item detail template

Copy this into the owning GitHub issue, or below this section while refining a new item. Replace placeholders before marking it Ready.

```markdown
### WORK-NNN: Short, outcome-focused title
Outcome ID:
Type / priority / status:
Accountable owner / contributors:
Affected components:
Problem and user value:
In scope:
Out of scope:

Acceptance criteria:
- Given [context], when [action], then [observable result].
- Rejection/failure/boundary behavior:

Dependencies and linked work:
Risks, compatibility and rollout considerations:
Verification approach:
Target milestone/date and assumptions:
Implementation issues / PRs:
Next action / last updated:
Acceptance evidence / accepting owner / acceptance date:
Release state and deployment evidence:
```

For cross-component work, identify the backend, web and mobile tasks and rollout order. Do not mark the parent item Done merely because one PR merged. Technical tasks must still explain their product, reliability or operational value.

## 8. Acceptance and release record

Keep **Done** separate from **Released**. Done means the agreed work is accepted; Released means the intended environment or distribution channel has received the change and relevant verification has been recorded. Define a production-availability criterion explicitly if it is required for an item to be Done.

| Work IDs | Acceptance evidence / accepting owner / date | Release state | Component versions / PRs / commit or tag | Target environment/channel | Release owner | Deployment and verification evidence / date |
|---|---|---|---|---|---|---|

Release states: `Not scheduled`, `Scheduled`, `Partially released`, `Released`, `Rolled back`, or `Not applicable` for non-deployable work. Track component-level rollout when backend and mobile releases differ. A merged PR or provider acceptance is not evidence that a parent has received a working feature.

## 9. Planning, review and decisions

Use the team's agreed cycle length; weekly planning and review are a starting point, not a mandatory sprint framework. Keep a dated record here when each cycle closes:

| Cycle / dates | Goal and selected work IDs | Accepted work / evidence | Carryover and reason | Scope changes / decision links | Next-cycle action and owner |
|---|---|---|---|---|---|

At planning, check capacity, Ready criteria, blockers and priorities. At review, demonstrate accepted outcomes, explain carryover without blame, and agree the next action. Revisit priorities when evidence changes; retain the reason for cancellations or scope changes.

### Risks and decisions

| ID / date | Risk or decision | Affected work IDs | Impact / options | Owner / decision-maker | Mitigation or decision and rationale | Review/due date / status |
|---|---|---|---|---|---|---|

Use `RISK-001` and `DEC-001` style IDs. Link detailed architecture or restricted incident records rather than copying sensitive information.

### Useful progress signals

Report accepted outcomes, ageing active items, blocker age, carryover reasons and production verification. If counting completed items, separate types and scope so the number is not misleading. Do not use lines of code, commit counts or invented percentage-complete figures as measures of product progress.

## 10. Worked examples - illustration only

**Everything in this section is fictional planning data, including dates, roles, approvals and evidence descriptions. It is not a live commitment, verified defect, actual test result or current delivery status.** Use these examples to fill the empty tables above with approved work; do not count examples in reporting.

Example IDs use `EXAMPLE-` to avoid confusion with live IDs. Role labels stand in for people; real items need named accountable owners. Evidence labels such as "device report" describe what a real record should link to, not evidence that exists. Replace them with actual issue, PR and evidence URLs when using the templates.

### 10.1 Example cycle and outcomes

**Fictional snapshot:** end of day `2026-11-20`.

| Field | Example value |
|---|---|
| Cycle | Example cycle A, `2026-11-16` through `2026-11-20` |
| Goal | Demonstrate understandable stale tracking and document its support workflow |
| Product owner | Example product lead |
| Delivery coordinator | Example delivery lead |
| Capacity | One mobile contributor and part-time backend/support reviewers |
| Work-in-progress limit | Two started items, including review/validation and blocked items |
| Selected work | EXAMPLE-WORK-001 and EXAMPLE-WORK-002 |
| Next review | `2026-11-23` |

| Outcome ID | User problem and intended outcome | Success measure / baseline | Accountable owner | Target milestone/date | Linked work IDs | Confidence and evidence |
|---|---|---|---|---|---|---|
| EXAMPLE-OUT-001 | Parent understands when a displayed position is no longer live | All agreed fresh/stale/failure scenarios pass; baseline assessment recorded during refinement | Example mobile lead | Staging demonstration / `2026-11-20` forecast | EXAMPLE-WORK-001 | At risk: device acceptance remains |
| EXAMPLE-OUT-002 | Support can distinguish stale tracking from missing alert reports | A backup reviewer can follow both diagnostic guides using synthetic cases | Example support lead | Support walkthrough / `2026-11-20` forecast | EXAMPLE-WORK-002, EXAMPLE-WORK-003 | Partial: tracking guide accepted; alert investigation not selected |

The cycle commits to the tracking-guide portion of EXAMPLE-OUT-002, not the entire outcome. Do not mark the outcome achieved just because one linked task is Done.

### 10.2 Example backlog

| Work ID | Title / user value | Outcome ID | Type | Priority | Status | Owner | Components | Target milestone/date | Issue / detail link |
|---|---|---|---|---|---|---|---|---|---|
| EXAMPLE-WORK-001 | Explain stale tracking without showing an invalid ETA | EXAMPLE-OUT-001 | Feature | P1 | In validation | Example mobile lead | Backend, parent native app | Staging demonstration / `2026-11-20` forecast at risk | Worked detail in section 10.5; replace with owning issue URL |
| EXAMPLE-WORK-002 | Add a stale-tracking support checklist | EXAMPLE-OUT-002 | Documentation | P2 | Done | Example support lead | Developer workbook | Support walkthrough / `2026-11-20` | Example walkthrough record; replace with issue/evidence URL |
| EXAMPLE-WORK-003 | Investigate why provider acceptance may not produce a visible alert | EXAMPLE-OUT-002 | Investigation | P2 | Ready | Example backend lead | Backend, parent native app | Not agreed; candidate for next cycle | Example investigation brief; replace with issue URL |
| EXAMPLE-WORK-004 | Show a useful retry state after a failed trip-history request | Not linked to an agreed outcome yet | Bug | P3 | Backlog | Not assigned | Parent native app | Not agreed | Example synthetic reproduction note; replace with issue URL |

EXAMPLE-WORK-004 illustrates a hypothetical bug report, not a finding about the application. EXAMPLE-WORK-003 is Ready only because its question, synthetic setup, access and owner are assumed agreed in this example. Neither is silently added to the current cycle.

### 10.3 Example current-cycle board and blocker

| Work ID | Status | Owner | Next action | Blocked? / blocker ID | Latest issue/PR/evidence link | Last updated |
|---|---|---|---|---|---|---|
| EXAMPLE-WORK-001 | In validation | Example mobile lead | Run remaining background/resume scenarios on the replacement device | Yes / EXAMPLE-BLK-001 | Example reviewed backend/mobile PRs and automated boundary report; replace with URLs | `2026-11-20` |
| EXAMPLE-WORK-002 | Done | Example support lead | No delivery action; revisit if tracking behavior changes | No | Example documentation PR and accepted backup-owner walkthrough; replace with URLs | `2026-11-19` |

| Blocker ID | Affected work IDs | Dependency / decision needed | Resolving owner | Next action | Needed-by date | Status / resolved date |
|---|---|---|---|---|---|---|
| EXAMPLE-BLK-001 | EXAMPLE-WORK-001 | Previously available test device became unavailable during validation | Example mobile lead | Arrange an approved replacement and repeat the remaining scenarios | `2026-11-20`; missed, escalated | Open; revised forecast awaits confirmed device availability |

This item stays In validation, with its blocker visible. Do not mark it Done, claim device acceptance from unit tests or move it back to Backlog to hide carryover. It still counts toward work in progress.

### 10.4 Example progress updates

These updates show how the same item moves through the cycle; they are not additional backlog rows.

| Date | EXAMPLE-WORK-001 status | Useful update |
|---|---|---|
| `2026-11-16` | Ready | Scope, contracts, synthetic scenarios, device access and owner agreed; selected for cycle A |
| `2026-11-17` | In progress | Parent presentation implemented against agreed backend freshness rules; boundary coverage in progress |
| `2026-11-18` | In review | Backend/mobile review requested with automated evidence; next action is address reviewer feedback |
| `2026-11-19` | In validation | Required engineering reviews complete; integrated device scenarios remain |
| `2026-11-20` | In validation, blocked | Test device became unavailable; replacement owner assigned; original forecast at risk |

Avoid updates such as "90% done" or "still working." State the remaining observable action, owner and obstacle.

### 10.5 Example filled work item

**EXAMPLE-WORK-001: Explain stale tracking without showing an invalid ETA**

| Field | Example value |
|---|---|
| Outcome | EXAMPLE-OUT-001 |
| Type / priority / status | Feature / P1 / In validation |
| Accountable owner / contributors | Example mobile lead / example backend reviewer and device tester |
| Components | Backend and parent native app |
| Problem and value | A parent should distinguish a reference position from a fresh trip fix instead of treating old data as live |
| In scope | Parent status labeling, existing freshness contract verification, relevant automated and device scenarios |
| Out of scope | New GPS providers, tracker fallback, routing changes or a new ETA algorithm |
| Dependencies | Backend freshness contract and approved staging/device configuration; EXAMPLE-BLK-001 now blocks remaining acceptance |
| Risk and compatibility | Preserve existing response fields and trip-phase semantics; no schema migration planned in this example |
| Target | Staging demonstration on `2026-11-20`; forecast missed pending device access |
| Implementation links | Replace with full backend/mobile issue and PR URLs; no real links are asserted here |

Example acceptance criteria:

- Given a valid eligible fix at the 120,000 ms age boundary, when tracking refreshes, the position remains eligible as fresh if all other conditions hold.
- Given a fix aged 120,001 ms, when tracking renders, it is not labeled live and no stale ETA is shown.
- Given a fix 30,001 ms in the future, when eligibility is evaluated, it is not accepted as fresh.
- Given the app resumes after connectivity loss, when refresh fails, it shows the failure and distinguishes retained last-known data from live data.
- Given two refreshes complete out of order, the older result does not replace newer eligible state.
- Given afternoon boarding is unresolved, freshness alone does not enable an ETA that trip-phase rules suppress.

**Verification approach:** Automated boundary/state tests plus integrated fresh/stale, failed-refresh and background/resume scenarios using synthetic staging data. Compare actual rendered labels and ETA suppression, not just HTTP success.

**Snapshot evidence:** In this fictional scenario, code reviews and automated cases are complete. Remaining device cases have not been accepted; no acceptance date is recorded and release is Not scheduled. Real use must link the reports and record the actual accepting owner.

### 10.6 Example acceptance and release records

| Work IDs | Acceptance evidence / accepting owner / date | Release state | Component versions / PRs / commit or tag | Target environment/channel | Release owner | Deployment and verification evidence / date |
|---|---|---|---|---|---|---|
| EXAMPLE-WORK-001 | Pending device acceptance; no accepting owner/date recorded | Not scheduled | Example reviewed backend/mobile PRs; no release version assigned | Staging acceptance first; distribution plan not approved | Example release lead | No release claim; replacement device cases remain |
| EXAMPLE-WORK-002 | Example synthetic walkthrough completed by backup reviewer and accepted by example support lead / `2026-11-19` | Not applicable | Example documentation PR; replace with merged PR/commit URL | Not applicable; documentation task | Not applicable | No application deployment required |

**Separate teaching scenario, not the snapshot above:** If EXAMPLE-WORK-001 later passes device acceptance and the product owner accepts it, its status becomes Done. It may still be Not scheduled for release. If a subsequent approved rollout deploys the backend but the parent app has not yet been distributed, record Partially released, the backend version/evidence and the remaining mobile step. Mark Released only after the intended distribution and verification criteria are met.

### 10.7 Example cycle review, risk and decision

| Cycle / dates | Goal and selected work IDs | Accepted work / evidence | Carryover and reason | Scope changes / decision links | Next-cycle action and owner |
|---|---|---|---|---|---|
| Example cycle A / `2026-11-16` to `2026-11-20` | Stale-tracking demonstration and support guide; EXAMPLE-WORK-001, EXAMPLE-WORK-002 | EXAMPLE-WORK-002; example backup-owner walkthrough | EXAMPLE-WORK-001; device unavailable, so integrated acceptance incomplete | EXAMPLE-DEC-001; no extra backlog items pulled in | Example mobile lead confirms replacement device; product owner replans remaining validation |

| ID / date | Risk or decision | Affected work IDs | Impact / options | Owner / decision-maker | Mitigation or decision and rationale | Review/due date / status |
|---|---|---|---|---|---|---|
| EXAMPLE-RISK-001 / `2026-11-20` | Single-device availability delays validation | EXAMPLE-WORK-001 | Obtain approved replacement or move demonstration; unit tests do not replace device behavior | Example mobile lead | Arrange replacement and propose backup-device coverage for future cycles | `2026-11-23` / Open |
| EXAMPLE-DEC-001 / `2026-11-20` | Carry remaining validation into planning rather than waive acceptance | EXAMPLE-WORK-001 | Forecast changes; release remains unscheduled | Example product lead with example engineering lead | Keep scope and evidence requirements; prioritize unblocking before selecting new work | `2026-11-23` / Decision recorded; follow-up open |

The useful summary is: **one documentation item accepted, one feature awaiting blocked validation, no feature release claimed**. It is not "50% of the product complete"; these items differ in scope and do not represent the whole product.
