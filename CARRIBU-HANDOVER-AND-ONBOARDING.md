# Carribu: Team Handover, Onboarding and Six-Month Development Plan

**Prepared:** November 1, 2026

**Reference period:** November 2026-April 2027

**Audience:** Incoming full-stack and native-mobile developers, team leads, mentors and product owner

**Status:** Proposed programme; ownership, access, staffing and release arrangements require approval

## 1. Purpose and how to use this guide

This guide transfers Carribu's product knowledge and operational responsibilities while teaching junior developers the technical foundations and engineering habits needed to maintain it safely.

It contains two separate team plans:

- **Part A:** Full-stack team: backend, school admin, super-admin and related web/operational surfaces.
- **Part B:** Native-mobile team: driver and parent Android applications.
- **Part C:** Shared engineering practices, TDD, product rules, coordination and operational safeguards.
- **Part D:** Reusable task, review, readiness and handover templates.

Team leads should turn their plan into a prioritized backlog, assign a primary and backup owner to each area, and review individual readiness monthly. Learning exercises should lead to small, reviewed contributions, not unreviewed production changes.

### 1.1 Outcomes expected after six months

| Outcome | Evidence |
|---|---|
| Understand the product | Explain a morning and afternoon trip from setup to completion, including parent communication |
| Work reproducibly | Set up the owned applications using documented steps and synthetic data |
| Deliver safely | Complete a bounded change with acceptance criteria, relevant tests, review and documentation |
| Diagnose issues | Reproduce a problem, isolate its cause and distinguish client, backend and provider failures |
| Operate responsibly | Follow an approved release procedure and escalate high-risk decisions |
| Transfer knowledge | A backup teammate can maintain the area without undocumented assistance |

Six months is a development target, not an automatic grant of unrestricted production access. High-risk work retains experienced review.

### 1.2 Assumptions and decisions required

| Decision | Proposed approach | Who approves |
|---|---|---|
| Team size and starting skills | Assess individuals in week one; combine roles where staffing is limited | Engineering owner |
| Start date | Use the reference months below; shift the programme if onboarding starts later | Product and engineering owners |
| Mentoring capacity | Named experienced mentor for each team; protected pairing and review time | Engineering owner |
| Product priorities | Choose real tasks from the approved backlog; exercises below are examples | Product owner |
| Staging and training data | Dedicated non-production setup with synthetic accounts and contacts | Engineering/operations owner |
| Public website ownership | Full-stack ownership unless another team is explicitly assigned | Product owner |
| Traccar operations | Full-stack coordination with a named experienced operational owner | Engineering/operations owner |
| Existing Expo applications | Decide continued support, transition or retirement explicitly | Product and engineering owners |
| Native distribution | Confirm internal APK, managed distribution and/or store requirements | Product and mobile owners |
| Repository and release controls | Inventory existing controls before proposing changes | Repository administrators |

This document does not configure repository protections, CI, deployment environments, account ownership or signing. Source publication does not establish production readiness or prove real-device notification delivery.

### 1.3 Preparation before the first onboarding day

| Preparation | Required result |
|---|---|
| Name owners | Lead, backup, mentor and escalation contact assigned for each team |
| Inventory systems | Repositories, deployments, database, Traccar, Firebase, Maps and distribution accounts recorded |
| Arrange access | Developers receive only the access needed for their current training stage |
| Prepare safe environments | Local/staging configuration and synthetic data are available |
| Prepare demonstrations | Working morning and afternoon journeys can be shown without real student data |
| Select starter tasks | Small, independently reviewable tasks with written acceptance criteria |
| Establish baseline | Record current build/test commands and distinguish existing issues from new regressions |
| Prepare recovery information | Backup, restore, incident escalation and release ownership are documented |

Do not put passwords, service-account contents, device tokens, signing keys or real student/guardian records in this guide, issues, screenshots or training recordings.

---

# Part A. Full-Stack Team Plan

## A1. Mission, scope and ownership

**Mission:** Maintain Carribu's server-owned business rules and web applications, deliver compatible features, and support routine operations with appropriate escalation.

| Repository/component | Team responsibility | Important boundary |
|---|---|---|
| `carribu_backend` | APIs, authorization, tenancy, database, trip lifecycle, location ingestion and notifications | Backend remains the authority for domain rules |
| `carribu_admin_app` | School operations, forms, trips, maps, history and diagnostics | UI must not invent a competing trip plan |
| `carribu_super_admin` | Cross-school administration, monitoring and resource management | Broad administration does not bypass safe trip completion |
| `carribu` | Public site and application-download presentation | Coordinate release/download metadata with mobile |
| `traccar-railway` | Deployment/configuration coordination and tracker troubleshooting | Production changes need the operational owner |

The workspace contains separate repositories and dependency installations. It is not a shared-package monorepo.

### A1.1 Team roles

| Role | Responsibility |
|---|---|
| Team lead | Break down work, manage dependencies, coordinate reviews and track readiness |
| Backup lead | Reproduce setup and release procedures; cover the primary owner |
| Experienced mentor | Teach foundations, review high-risk changes and lead escalation |
| Developers | Own bounded tasks, tests, documentation and demonstrations |
| Product owner | Set priorities, acceptance criteria and user-facing expectations |

Assign roles explicitly even if one person holds more than one role. A junior developer should not be the sole approver of their own high-risk work.

## A2. Technical curriculum

Teach foundations before expecting framework fluency. Combine explanation, exercises, pairing and progressively larger Carribu tasks.

| Area | Topics | Practical evidence |
|---|---|---|
| Programming basics | Types, variables, conditionals, loops, functions, collections, modules, exceptions and basic complexity | Explain and test a small transformation or validation function |
| JavaScript execution | Scope, mutation, closures, promises, `async/await` and asynchronous failure handling | Handle a rejected request without hiding the error |
| Web foundations | Semantic HTML, CSS layout, accessibility, browser tools, forms, HTTP and JSON | Build an accessible form and inspect its requests |
| React | Components, props, state, hooks, effects/cleanup, routing and controlled inputs | Demonstrate loading, success, empty and failure states |
| Express | Route/controller/service boundaries, middleware, validation, authorization and error responses | Trace a request from route to database and back |
| SQL/PostgreSQL | Keys, relationships, joins, constraints, indexes and transactions | Write a school-scoped query and explain a transaction |
| Sequelize/migrations | Associations, generated queries, migration ordering and data preservation | Review a bounded schema change and its recovery implications |
| Domain modelling | State transitions, frozen plans, idempotency and concurrency | Explain why duplicate actions must not duplicate effects |
| Realtime/providers | Socket events, polling, GPS timestamps, outbox processing and delivery diagnostics | Distinguish fresh location, last-known position and provider acceptance |
| Developer tools | PowerShell, npm, Git, diffs, PRs, debugging, environment configuration and logs | Produce a reproducible, reviewable contribution |
| Operations | Deployment, health checks, backups, restore, monitoring and escalation | Follow a supervised staging release and incident exercise |

**Learning resources:** MDN Core Curriculum and JavaScript learning modules; official React Learn; Express documentation; PostgreSQL Tutorial; Sequelize documentation; Jest Getting Started. Use resources matching the repository's installed versions, not an assumed latest API.

## A3. First four weeks

| Week | Learning and hands-on work | Exit evidence |
|---|---|---|
| 1 | Product walkthrough; assess foundations; establish local setup; learn Git/HTTP/JavaScript; begin a small test-first exercise | Applications run safely; developer explains the product and a simple test |
| 2 | Trace login and school-scoped requests; practise SQL; trace scheduling, start and student actions | Developer explains route/controller/service/database boundaries |
| 3 | Pair on a bounded bug or UI improvement; write a regression test; submit a small PR | Reviewed change with acceptance criteria and understandable evidence |
| 4 | Demonstrate in staging; trace a complete trip; practise debugging and teach back setup steps | Another teammate can reproduce the work from its documentation |

A developer still learning programming fundamentals may require more paired time. Do not skip foundational gaps to meet the calendar.

## A4. Six-month milestones

| Month | Technical learning | Delivery and practice | Readiness gate |
|---|---|---|---|
| November 2026 | JavaScript, HTML/CSS, HTTP, Git, local setup and introductory tests | Tested exercises, first supervised PR and corrected onboarding notes | Can explain their code and run the owned applications safely |
| December 2026 | React, Express, SQL and asynchronous errors | Bounded API/UI fixes, test-first bug reproduction, validation and explicit errors | Can diagnose a small issue and preserve tenancy boundaries |
| January 2027 | Transactions, trip plans, idempotency, contracts and integration tests | Small approved end-to-end feature; compatibility and failure-case demonstration | Can identify affected clients and test success, rejection and retry cases |
| February 2027 | Migrations, deployment, tracking and notification operations | Supervised staging release; migration/recovery checklist and exercise | Can distinguish code rollback from database recovery |
| March 2027 | Query performance, logs, outbox/provider diagnosis and safe refactoring | Operational improvement; incident simulation; updated runbooks | Can isolate root cause and implement a regression safeguard |
| April 2027 | Bounded subsystem ownership and knowledge transfer | Routine approved release; backlog maintenance; backup-owner training | Can deliver with limited supervision and hand over reproducibly |

### A4.1 Suitable initial work

Start with a bounded validation, filtering, accessibility, diagnostic-message or documentation issue. Then progress to a small API/UI change.

Do not start by rewriting authentication, the trip workflow, database migrations or notification architecture. Existing functionality should be understood and covered before it is extended.

## A5. TDD and test strategy

Use the shared red-green-refactor workflow in C2 from month one. Extend the existing suites instead of creating a parallel test framework.

| Test layer | Carribu behaviors to cover | What it establishes |
|---|---|---|
| Unit | Trip transitions, completion eligibility, timestamps and pure ETA rules | Domain decisions behave at exact boundaries |
| API/integration | Authorization, school isolation, validation and conflicting assignments | Real components reject unsafe requests |
| Transaction/concurrency | Simultaneous starts, GPS/outbox rollback and matching retries | No partial state or duplicate business effects |
| React UI | Loading, empty/error states, freshness labels and action availability | Users see accurate state and recoverable errors |
| End-to-end | Morning and afternoon journeys with parent-visible outcomes | Components agree across a complete scenario |
| Operational exercises | Migration, restore, failed provider submission and tracker interruption | Release and recovery procedures are usable |

Database, transaction and concurrency requirements cannot be established solely with mocked database calls. Conversely, unit tests should not need external tracking or notification services.

### A5.1 Full-stack TDD exercise

**Scenario:** A driver already assigned to an active trip cannot start another trip.

| Step | Action |
|---|---|
| Define | Write expected rejection, unchanged scheduled trip and no partial start notification |
| Red | Add an integration case with disjoint rosters so the test isolates driver exclusivity |
| Green | Make the smallest change preserving the existing transactional workflow |
| Refactor | Improve structure without weakening locks, constraints or tenancy |
| Extend | Add vehicle conflict, concurrent starts and a matching retry scenario |

For existing behavior, first confirm the case is already covered. Do not intentionally break working code to manufacture a red test.

## A6. Setup and verified command reference

All examples below use Windows PowerShell. Run commands from the named repository. Configure local development and test credentials privately before starting anything.

| Repository | Development | Build/check |
|---|---|---|
| `carribu_backend` | `npm run dev` | `npm test` after safe database configuration |
| `carribu_admin_app` | `npm run dev` | Windows build/test commands below |
| `carribu_super_admin` | `npm run dev` | `npm run build`; `npm run lint` |
| `carribu` | `npm run dev` | `npm run build`; `npm run lint` |

Install dependencies independently using each repository's committed lockfile policy. Use `npm ci` where a compatible committed npm lockfile exists; otherwise follow the component README. Runtime versions must satisfy the actual manifests and build tools.

**Admin distinction:** `npm start` builds and launches its server; it is not the development command. Its build script uses Unix-style `CI=false`, so on Windows use:

```powershell
Set-Location C:\src\school-transport-app\carribu_admin_app
$env:CI='false'
node .\node_modules\react-scripts\bin\react-scripts.js build
```

Run selected existing admin tests with its installed runner:

```powershell
node .\node_modules\react-scripts\bin\react-scripts.js test --watchAll=false --runInBand --runTestsByPath src\pages\TripDetailsPage.test.js src\components\VehicleLocationCard.test.js
```

There is no admin package `test` script in the inspected manifest. Do not assume every repository exposes the same commands.

### A6.1 Database safety

The backend's integration setup recreates schema. Run it only on explicitly disposable local databases. Workflow/outbox/migration suites require the `carribu_workflow_*` naming pattern and host `127.0.0.1`; these guards are not permission to run other suites against shared data.

Before database tests:

- Create a disposable database, for example `carribu_workflow_onboarding`.
- Confirm the resolved database configuration points to that database on the local host.
- Supply local database credentials privately.
- Use a dedicated test terminal; do not reuse its environment for the normal development server.
- Keep database suites sequential.

Example after local credentials are configured:

```powershell
Set-Location C:\src\school-transport-app\carribu_backend
$env:DB_NAME='carribu_workflow_onboarding'
$env:DB_HOST='127.0.0.1'
$env:DB_PORT='5432'
$env:NODE_ENV='test'
$env:JWT_SECRET='onboarding-test-only-not-for-production'
npm test -- --runTestsByPath tests\tripPlan.test.js tests\tripWorkflow.test.js tests\tripWorkflowMigration.test.js tests\notificationOutbox.test.js tests\outboxPush.test.js
```

The sample contains no database password. Never paste production credentials into examples or shell history.

Backend startup applies migrations before listening. Leave `DB_SYNC` unset. Migration `0016` refuses overlapping active assignments; resolve the underlying conflict through an approved process rather than bypassing that protection.

Reversing `0016` removes new snapshots, outbox and idempotency metadata. A migration undo is not a generic safe application rollback.

### A6.2 Initial reading order

1. `carribu_backend\README.md`: setup, authoritative workflow, notifications and regression checks.
2. `carribu_backend\services\tripPlan.js`: pure trip rules, snapshots and freshness.
3. `carribu_backend\services\tripWorkflow.js`: transactional lifecycle and actions.
4. `carribu_backend\services\locationTracking.js`: authoritative sources and accepted positions.
5. `carribu_backend\services\notificationOutbox.js`: enqueue, leasing, retry and cancellation.
6. `carribu_backend\migrations\0016-trip-workflow-and-notification-outbox.js`: upgrade and recovery risks.
7. Admin trip/detail/location/diagnostic components and their existing tests.
8. Super-admin trips and public-site release/download behavior.

Use the component READMEs and manifests as the setup authority. The workspace README contains an older Expo-oriented layout and is not a complete current repository inventory.

## A7. Release and final handover gates

Before a supervised release, require relevant tests/builds, an approved contract/rollout plan, migration impact review, backup/recovery readiness, staging acceptance and a named release/escalation owner.

By the end of April, the full-stack team should demonstrate:

- Clean local setup and safe test database configuration.
- A compatible backend/web change delivered end to end.
- Morning and afternoon workflow understanding, including failed and retried actions.
- A supervised migration and recovery exercise.
- Diagnosis of simulated GPS and notification failures.
- A maintained ownership map, release checklist and operational runbook.
- A backup developer able to repeat a routine release.

Authentication, tenancy, state transitions, migrations, exclusivity, tracking policy and notification-delivery changes retain experienced review.

---

# Part B. Native-Mobile Team Plan

## B1. Mission, scope and ownership

**Mission:** Maintain the driver and parent native Android applications, consume backend contracts safely, and deliver controlled releases with reliable device behavior.

| Repository/component | Team responsibility | Important boundary |
|---|---|---|
| `carribu_driver_native_app` | Driver session, guidance, student actions, phone tracking, messaging and notifications | Consume server-owned itinerary and completion eligibility |
| `carribu_parent_native_app` | Parent session, children, active tracking, history, alerts and messaging | Present GPS/ETA freshness accurately |
| Native release process | Build identity, signing, versioning, installation, upgrades and distribution | No release without approved key custody and compatibility checks |
| Existing Expo apps | Support/transition only as explicitly agreed | Native ownership does not silently retire Expo |

Current native scope is Android. iOS development, framework migration and broad redesign require separate approval and estimation.

### B1.1 Team roles

| Role | Responsibility |
|---|---|
| Team lead | Plan bounded mobile work, coordinate backend contracts and organize device acceptance |
| Backup/release owner | Reproduce builds and approved release procedures |
| Experienced Android mentor | Teach foundations, review lifecycle/permissions/signing and support escalation |
| Developers | Own screen/state changes, regression coverage and reproducible demonstrations |
| Product owner | Approve user behavior, device support priorities and distribution requirements |

Keep a primary and backup for each app and for release operations. Do not leave signing knowledge with one unavailable person.

## B2. Technical curriculum

| Area | Topics | Practical evidence |
|---|---|---|
| Programming basics | Types, variables, conditionals, functions, collections, classes and interfaces | Explain a small Kotlin function and its tests |
| Kotlin | Nullability, data/sealed classes, lambdas, immutable state and exceptions | Model success/error state without unsafe null assumptions |
| Android foundations | Project structure, Gradle, resources, activities, lifecycle and navigation | Build and run both apps; explain background/foreground changes |
| Compose | Composables, state, recomposition, state hoisting, semantics and accessibility | Build an accessible screen with all relevant states |
| Architecture | DTOs, repositories, ViewModels, StateFlow and lifecycle-aware collection | Trace API data to displayed UI without duplicating domain rules |
| Asynchronous work | Coroutines, scopes, cancellation, race conditions and coroutine tests | Prevent an older request from replacing newer state |
| Networking/storage | HTTP/JSON, Retrofit/Moshi, API errors, session expiry and DataStore | Demonstrate expired-session and failed-request behavior |
| Device capabilities | Maps, permissions, foreground location service, notifications and battery constraints | Explain behavior when permission or connectivity changes |
| Quality tools | JUnit, coroutine tests, Compose tests, emulator/device debugging and sanitized diagnostics | Add a focused regression and reproduce a device issue |
| Releases | Build variants, signing, versions, installation, upgrades and distribution | Produce an approved internal release with repeatable steps |

**Learning resources:** Android Basics with Compose; Kotlin documentation; Android app architecture, testing, lifecycle and permissions documentation; Android app-signing guidance.

Use Carribu exercises alongside tutorial work. Do not mistake completion of a course for demonstrated maintenance readiness.

## B3. First four weeks

| Week | Learning and hands-on work | Exit evidence |
|---|---|---|
| 1 | Product walkthrough; Kotlin/Git assessment; configure safe backend; run both apps; begin a small unit-test exercise | Both apps run without contacting production; developer explains a simple test |
| 2 | Compose state, repository/ViewModel flow, HTTP errors and lifecycle | Developer traces an API-backed screen and its failure state |
| 3 | Pair on a bounded UI/state fix; write a regression case; submit a small PR | Reviewed change preserving server-owned behavior |
| 4 | Practise permission denial, interrupted connectivity, backgrounding and teach-back | Reproducible device exercise and troubleshooting notes |

Agree on an emulator/physical-device matrix based on supported users and available equipment. Do not promise universal device behavior from a single successful build.

## B4. Six-month milestones

| Month | Technical learning | Delivery and practice | Readiness gate |
|---|---|---|---|
| November 2026 | Kotlin, Git, Android Studio, basic Compose and JUnit | Tested exercises, both apps running, first supervised PR | Can explain state and make a small safe change |
| December 2026 | ViewModels, repositories, coroutines, networking and session errors | Bounded fixes; test-first state cases; controlled retry behavior | Can reproduce and explain a client/device failure |
| January 2027 | Server-owned trip state, navigation, tracking and API compatibility | Small approved mobile/backend feature; joint acceptance demo | Can handle loading, rejection, refresh and late responses |
| February 2027 | Permissions, notifications, signing and upgrades | Approved signing setup; signed internal release; install/update exercises | Can repeat the approved release procedure under supervision |
| March 2027 | Background behavior, interrupted connectivity and diagnostics | Tracking/notification incident simulation; agreed device matrix; runbooks | Can distinguish client, permission, backend and provider problems |
| April 2027 | Bounded app-area ownership and knowledge transfer | Routine approved release; backlog and documentation maintenance; backup training | Can deliver with limited supervision and transfer ownership |

### B4.1 Suitable initial work

Begin with a bounded label, error/retry presentation, validation, accessibility or existing freshness regression. Progress to a small API-backed change once the developer understands repository and ViewModel boundaries.

Do not begin with a broad architecture rewrite, a new local trip engine or unreviewed background-location/signing changes.

## B5. TDD and test strategy

Teach local tests and instrumented tests as different tools. Local JVM tests suit pure logic and controlled asynchronous state. Device/emulator tests establish Android/UI behavior that a JVM test cannot reproduce.

| Test layer | Carribu behaviors to cover | What it establishes |
|---|---|---|
| Pure unit | Validation, coordinates, freshness, trip presentation and version decisions | Local decisions handle boundaries and invalid input |
| Repository/ViewModel | Loading/success/error, expiry, retries, cancellation and response ordering | State changes are predictable |
| Contract/integration | DTO parsing, endpoint errors, phase-aware actions and backend compatibility | Client and server agree on meaning |
| Compose UI | Error/retry states, stale-location labels and action availability | Users receive accurate guidance |
| Device/operational | Permission denial, backgrounding, notifications, installation and upgrades | Platform and release behavior work in the agreed matrix |

Current source includes driver `TripLogicTest.kt`, parent `ModelLogicTest.kt` and parent `AuthValidationTest.kt`. Compose/device coverage is a curriculum deliverable, not an assertion that a complete instrumented suite is already configured. Add required tooling only for an approved test need.

### B5.1 Native-mobile TDD exercise

**Scenario:** A late response must not replace a newer accepted location.

| Step | Action |
|---|---|
| Define | Describe two refreshes and their reverse completion order |
| Red | Use controlled fake responses to reproduce regression in request/state handling |
| Green | Preserve the newest eligible state using the existing architecture |
| Refactor | Improve readability without changing cancellation, selection or freshness rules |
| Extend | Add selected-trip change, completed trip, API failure and stale timestamp cases |

Do not solve stale ordering by accepting all responses, clearing useful error state, or suppressing failed requests.

## B6. Setup and verified command reference

Use each native component README and `app\build.gradle.kts` as the configuration authority. The inspected projects use Kotlin/Compose, compile/target SDK 36, minimum SDK 26 and JVM target 17. These are project settings, not a recommendation to upgrade tools blindly.

**Critical training safeguard:** both native builds default to a deployed backend URL. Set `API_BASE_URL` explicitly to local/staging before running a training build. The base URL must include the API path.

For an Android emulator using a backend on the development computer, configure local properties as documented:

```properties
API_BASE_URL=http\://10.0.2.2\:5000/api/
```

A physical device needs the agreed reachable local/staging address, not the emulator-host alias.

Copy `local.properties.example` to `local.properties`, configure the SDK and restricted Maps key privately, and use app-specific Firebase configuration only when needed. Never copy service-account secrets into a mobile project.

Run from the workspace in PowerShell, adapting local tool paths:

```powershell
Set-Location C:\src\school-transport-app
$env:JAVA_HOME='C:\Program Files\Android\Android Studio\jbr'
$env:ANDROID_HOME='C:\Users\your-name\AppData\Local\Android\Sdk'
$env:ANDROID_SDK_ROOT=$env:ANDROID_HOME
.\carribu_driver_native_app\gradlew.bat -p .\carribu_driver_native_app :app:compileDebugKotlin :app:testDebugUnitTest --quiet --console=plain
.\carribu_parent_native_app\gradlew.bat -p .\carribu_parent_native_app :app:compileDebugKotlin :app:testDebugUnitTest --quiet --console=plain
```

Build an installable debug APK from the relevant native repository:

```powershell
.\gradlew.bat :app:assembleDebug --console=plain
```

Debug output is under `app\build\outputs\apk\debug`. Firebase-free builds can compile, but this does not validate FCM tray delivery. Maps also need the configured key to display tiles.

### B6.1 Signing and distribution readiness

At the document preparation date:

- Parent Gradle release signing is conditional on four environment variables: `CARRIBU_RELEASE_KEYSTORE`, `CARRIBU_RELEASE_STORE_PASSWORD`, `CARRIBU_RELEASE_KEY_ALIAS` and `CARRIBU_RELEASE_KEY_PASSWORD`.
- Driver Gradle does not configure an equivalent release signing setup. Establish and review an approved mechanism before the signed-release milestone.
- Existing release artifacts do not establish a repeatable release process.

The release owner must record application identity, approved signing method, key custodian, protected backup/recovery process, version policy and distribution channel. Preserve the signing identity needed for upgrades; do not generate a replacement production key as an onboarding shortcut.

Verify signed output, installation and upgrade behavior. A successful release build without configured signing is not evidence of a signed, distributable package.

### B6.2 Initial reading order

1. Both native READMEs and `app\build.gradle.kts`.
2. API/model and session layers; authentication failure handling.
3. Repositories and ViewModels; loading/error/refresh behavior.
4. Driver `TripLogic.kt` and trip screen; canonical actions/navigation.
5. Parent model logic and tracking/trip screens; freshness and response ordering.
6. Location service, push registration and notification rendering.
7. Existing unit tests and approved build/distribution procedures.

## B7. Release and final handover gates

Before release, require relevant tests/builds, agreed device checks, backend compatibility, verified target environment, approved signing/versioning and installation/upgrade evidence.

By the end of April, the mobile team should demonstrate:

- Reproducible builds of both applications using safe configuration.
- A mobile/backend change accepted jointly.
- Correct presentation of unavailable/stale location and failed requests.
- Permission, backgrounding and interrupted-connectivity exercises.
- Real-device notification checks in the approved environment.
- Controlled signing, installation, updates and distribution.
- A backup owner able to repeat the approved release procedure.

Authentication/session storage, background location, permissions, DTO contracts, notification behavior and signing retain experienced review.

---

# Part C. Shared Engineering and Operational Standards

## C1. Carribu domain rules everyone must understand

| Area | Invariant and onboarding expectation |
|---|---|
| Tenancy/roles | Access is scoped to the permitted school and role; UI visibility is not authorization |
| Scheduling/start | Scheduling does not freeze the roster; start captures the ordered plan, guardian information and destinations |
| Morning | Resolve home pickup/absence before school drop-off; school destination is the final outbound waypoint |
| Afternoon | Explicitly board or mark absent every student at school before reversed home drop-offs |
| Student progress | Normal path is pending, arrived pickup, on bus, arrived drop-off, dropped off; absence is only before boarding |
| Arrival | Arrival alone does not resolve/advance a stop; boarding, absence or drop-off does |
| Canonical plan | Use backend `phase`, `currentStop`, `nextStop`, `pickupList` and `canEnd` |
| Idempotency | Matching retries must not duplicate business effects; phase-aware keys distinguish actions |
| Exclusivity | Active driver/vehicle assignments are protected by transactions and database constraints |
| Completion | Every role must resolve all students as dropped off or absent before ending |
| Active route changes | Active routes cannot be edited/deactivated in ways that bypass the workflow |
| History | Frozen historical membership is not replaced by today's route membership |
| GPS source | Linked vehicles use Traccar; unlinked vehicles can use phone tracking; no automatic fallback for a linked offline tracker |
| GPS validity | Eligible fixes must not predate the trip, regress position order or violate timestamp/coordinate validity |
| GPS freshness | Age window is -30,000 through 120,000 milliseconds; excessive future timestamps and stale fixes are not fresh |
| Last-known position | An admin reference snapshot may predate the trip; it is not actual trip history or an ETA/proximity input |
| ETA | Approximate straight-line estimates; suppress stale/invalid inputs and afternoon boarding ETAs |
| Notifications | Business mutation and outbox persistence are transactional; realtime delivery may repeat stable event IDs |
| Delivery meaning | Provider acceptance is not handset receipt or parent read |
| Legacy data | Existing active afternoon trips need boarding reconciliation; a lazy snapshot cannot recreate immutable pre-upgrade history |

Never bypass a rule to make a demo succeed. Use a valid synthetic scenario and explain rejection behavior.

## C2. TDD: red-green-refactor in daily work

TDD guides implementation through expected behavior. Writing tests only after implementation is not the same practice.

1. **Define:** write acceptance criteria and a short list of relevant scenarios.
2. **Red:** select a small behavior, write a focused test and confirm failure for the expected reason.
3. **Green:** implement the simplest complete change that passes without a risky shortcut.
4. **Refactor:** improve structure, naming and duplication while preserving passing behavior.
5. **Extend:** add the next scenario and relevant integration/UI/device coverage.

For a bug, first reproduce it and write a test that fails because of the bug. For an already-working requirement, confirm existing coverage and add meaningful missing cases; do not break code merely to stage a red demonstration.

### C2.1 Test quality rules

| Practice | Expectation |
|---|---|
| Observable behavior | Assert a meaningful result, rejected action or persisted effect, not only implementation details |
| Exact boundaries | Cover equality and just-outside values where thresholds matter |
| Independence | Tests do not rely on order, shared real accounts or external provider availability |
| Controlled time | Use fixed clocks and coroutine/test scheduling rather than arbitrary sleeps |
| Appropriate fakes | Fake remote providers for unit tests; use real disposable PostgreSQL for transaction/concurrency evidence |
| Useful failures | Assertions should identify what contract failed |
| Regression preservation | Do not weaken assertions or skip a test simply to make a change pass |
| Maintainability | Keep fixtures synthetic and small; avoid over-mocking internal implementation |

Do not require a fixed coverage percentage as proof of correctness. Review whether critical decisions, rejection paths, boundaries and failure recovery are meaningfully covered.

### C2.2 Concrete boundary exercises

| Scenario | Expected assertion |
|---|---|
| GPS age is 120,000 ms | Eligible timestamp is within the age boundary if all other requirements hold |
| GPS age is 120,001 ms | Not fresh; no stale ETA/proximity warning |
| GPS age is -30,000 ms | Within the clock-skew boundary if other requirements hold |
| GPS age is -30,001 ms | Excessively future timestamp; not a fresh trip fix |
| Same action/key is retried | No duplicate trip log or notification business event |
| Key reused for a different operation | Conflict, not silent success |
| Last student remains on bus | Completion rejected |
| Afternoon student is unresolved at school | Home drop-off guidance/ETA must not incorrectly begin |
| Two refreshes finish out of order | Older result does not overwrite the newer eligible selection/state |
| Provider accepts notification | Diagnostics do not claim parent read or guaranteed device delivery |

### C2.3 Exploratory work and tooling

Use test-first work for business logic and reproducible bugs. A short, time-boxed UI/hardware investigation is acceptable when behavior is not yet understood. Document findings and establish automated regression coverage where feasible, plus device acceptance where needed, before merging.

Reuse existing runners. Add dependencies or framework changes only for an approved need. CI checks and device suites are proposed deliverables unless their current configuration has been verified.

## C3. Daily engineering practices

| Practice | Required habit |
|---|---|
| Small changes | One coherent objective per PR; avoid unrelated fixes |
| Clear code | Meaningful names, cohesive functions, explicit errors and existing project conventions |
| Simple design | Preserve boundaries and reuse prior art; avoid speculative abstractions |
| Review | Explain behavior, risk, affected clients and evidence; address feedback constructively |
| Security/privacy | Least-needed access, synthetic fixtures, sanitized logs and no credentials in source |
| API design | Document meaning, nullability, errors, dates/timezones, compatibility and retries |
| Accessibility | Check labels, focus, readable status, contrast and touch interaction as relevant |
| Debugging | Reproduce, inspect evidence, isolate, fix, test and document |
| Documentation | Update setup/contracts/runbooks when behavior or procedures change |
| AI-assisted coding | Developer can explain submitted code, verify assumptions and inspect generated tests |
| Accountability | Report blockers and uncertainty; do not claim delivery from a successful build alone |

A developer should never approve generated code they cannot explain. Do not paste secrets, personal records or confidential operational data into unapproved tools.

## C4. Recommended learning and mentoring cadence

| Cadence | Activity |
|---|---|
| Daily | Brief progress/blocker check; protected focus time for learning and delivery |
| Weekly | Paired coding/TDD session, mentoring office hour and cross-team integration session |
| Every two weeks | Demonstrate an integrated user journey and discuss lessons from reviews/bugs |
| Monthly | Individual readiness assessment, ownership update and programme adjustment |
| Before releases | Risk review, staging/device acceptance and release-owner confirmation |

Suggested time allocation, adjustable to experience and staffing:

| Period | Structured learning | Paired/supervised delivery | Bounded independent delivery |
|---|---|---|---|
| Months 1-2 | 40% | 40% | 20% |
| Months 3-4 | 20% | 40% | 40% |
| Months 5-6 | 10% | 30% | 60% |

Reserve mentor time as part of capacity planning. Mentoring is not an extra task to fit around an already full delivery schedule.

## C5. API and cross-team agreement

| Agreement | Working rule |
|---|---|
| Domain authority | Full-stack owns server rules; all clients consume their meaning consistently |
| Contract changes | Propose schema/behavior changes before implementation; mobile and web owners review impact |
| Compatibility | Record required fields, nullability, errors, idempotency, time semantics and supported client versions |
| Rollout | Agree backend, migration and client order; prefer compatible additive changes where possible |
| Acceptance | Jointly demonstrate complete morning/afternoon journeys, not disconnected screens |
| Shared fixtures | Use the same approved synthetic trip scenarios across tests and staging |
| Blocking dependencies | Assign an owner and date; avoid undocumented temporary client workarounds |
| Releases/downloads | Coordinate published version metadata, package availability and public-site links |

For a breaking change, document affected deployed clients, transition strategy and release approval. A backend deployment must not assume every installed mobile app updates immediately.

## C6. Access and release progression

| Stage | Typical access/responsibility | Evidence before progression |
|---|---|---|
| Foundations | Local development, synthetic accounts, repository contributions | Safe setup and understanding of credentials/data |
| Supervised integration | Staging access and sanitized diagnostics | Reviewed change and successful acceptance cases |
| Supervised operations | Approved staging/release tasks with an experienced owner | Checklists and recovery/device exercises |
| Bounded ownership | Routine approved releases and first-line triage | Repeated demonstrated competence and backup coverage |
| High-risk operations | Only explicitly authorized production, database or signing actions | Experienced approval, impact plan and recovery readiness |

Store access instructions and secret references, not secret values. Production database write access, signing custody and incident authority are distinct permissions.

## C7. Operational runbooks and incident exercises

Prepare a concise runbook for each owned area containing symptoms, safe evidence collection, decision points, escalation, recovery and verification.

| Incident exercise | Safe initial investigation | Do not do |
|---|---|---|
| Tracker appears offline/no trip location | Confirm linked device, source, active trip, fix timestamp, ingestion/polling status and connectivity | Enable phone fallback or fabricate a fresh timestamp |
| Parent sees stale/no ETA | Check phase, eligible fix, response ordering, selection and error state | Relabel last-known position as live |
| Parent reports missing alert | Check outbox outcome, registration/configuration, provider response and device permissions in the approved environment | Claim acceptance proves delivery or resend blindly |
| Trip cannot start/end | Check eligibility, active assignments, student states and recorded rejection | Force-end a trip or remove constraints |
| Migration fails | Stop rollout, inspect conflict/status, consult recovery owner | Enable `DB_SYNC` or undo destructive metadata changes casually |
| Native install/update fails | Check package/version, signing identity, target configuration and approved distribution | Replace the production signing key as a shortcut |

### C7.1 Escalation expectations

Escalate suspected cross-school access, data loss, incorrect trip completion, inconsistent student state, exposed credentials, signing loss or an unsafe release immediately to the named experienced owner.

The exercise ends only when the team can explain the cause, perform an approved correction, verify the user journey and record a prevention measure. Do not perform destructive production drills.

### C7.2 Recovery planning

Record the approved backup owner, restore procedure, recovery objectives, verification steps and treatment of writes made after a backup. Confirm objectives with the business; do not invent recovery guarantees.

Separate application rollback, database forward-fix/restore and mobile distribution remediation. A successful backup job alone is not evidence that restoration has been rehearsed.

## C8. Handover package

| Artifact | Primary owner | Contents |
|---|---|---|
| Architecture/product map | Full-stack lead with mobile input | Components, dependencies, roles and complete user journeys |
| Repository/setup guide | Each team | Actual commands, prerequisites, configuration references and safe fixtures |
| Ownership/access register | Engineering owner | Primary/backup, systems, approved roles and escalation; no secrets |
| API contract register | Full-stack with mobile | Fields, behavior, error/retry semantics and compatibility |
| Domain-rule checklist | Both teams | Canonical trip, tenancy, GPS and notification invariants |
| Test/acceptance catalogue | Each team | Critical cases, runners, fixture safety and device matrix |
| Release/recovery runbooks | Release/operations owners | Steps, approvals, migration/signing impact and verification |
| Known-issues/backlog register | Product and team leads | Reproduction, impact, owner, priority and dependencies |
| Readiness scorecards | Mentors/leads | Demonstrated competencies, gaps and next exercises |
| Final acceptance record | Product/engineering owners | Evidence, unresolved risks and ownership approval |

Store maintained technical documents in an agreed version-controlled home. Store credentials and personal operational data only in approved protected systems. The workspace copy of this guide is not itself evidence of a committed organizational documentation repository.

---

# Part D. Reusable Templates and Acceptance

## D1. Work-item template

```text
Title:
Team / primary owner / reviewer:
User problem and expected outcome:
Acceptance criteria:
Affected repositories, clients and contracts:
Relevant Carribu invariants:
Test-first scenario and edge cases:
Implementation scope / explicit exclusions:
Privacy, migration, permissions or signing impact:
Staging/device acceptance evidence:
Release order and recovery considerations:
Documentation changes:
Dependencies / blockers:
```

## D2. Pull-request checklist

- [ ] The change has one clear objective and written acceptance criteria.
- [ ] Relevant existing patterns and tests were examined before implementation.
- [ ] Bug reproduction or test-first evidence is recorded where appropriate.
- [ ] Happy path, rejection, boundaries and retry/race cases are considered.
- [ ] Relevant tests/build/checks pass; existing failures are distinguished.
- [ ] School/role boundaries and server-owned trip rules remain intact.
- [ ] Errors are visible; no silent success-shaped fallback was added.
- [ ] Loading, empty, stale and lifecycle behavior is addressed where relevant.
- [ ] Secrets and real student/guardian data are absent from the diff and evidence.
- [ ] API/migration/device/release impacts are documented.
- [ ] Related documentation is updated.
- [ ] An experienced reviewer approved high-risk changes.

## D3. Definition of done

A task is done when the accepted behavior is implemented, persisted, reviewed and demonstrated in the appropriate environment; relevant regression coverage and documentation are maintained; and unresolved release risks are explicit.

A compiled app is not proof of device behavior. A passing unit test is not proof of database atomicity. A Git push is not a production deployment. A provider response is not proof a parent received an alert.

## D4. Individual readiness scorecard

Use evidence rather than course completion, commit counts or an arbitrary coverage target.

| Level | Meaning |
|---|---|
| 0 | Not yet introduced |
| 1 | Can explain with guidance |
| 2 | Can perform with pairing |
| 3 | Can perform independently in an approved environment |
| 4 | Can review, troubleshoot and teach the bounded skill |

| Competency | Evidence to record | Level |
|---|---|---|
| Programming foundations | Explained exercise and readable implementation | TBD |
| Owned stack/architecture | Traced request or screen/state flow | TBD |
| Product/domain rules | Morning/afternoon journey and rejection cases | TBD |
| TDD/test design | Red-green-refactor exercise and meaningful regression | TBD |
| Debugging | Reproduced issue and evidence-based diagnosis | TBD |
| Security/privacy | Safe configuration and data handling | TBD |
| Collaboration/review | Clear PR, useful feedback and contract coordination | TBD |
| Releases/operations | Approved supervised release/recovery or device exercise | TBD |
| Documentation/backup | Another teammate reproduced the procedure | TBD |

A proposed month-six target is level 3 in the skills needed for the developer's assigned area, with teach-back evidence and a backup owner. No average score should override an unresolved critical gap.

## D5. Monthly review template

```text
Month / developer / mentor:
Skills practised:
Changes delivered and acceptance evidence:
TDD/test-design evidence:
Debugging or incident exercise:
Review feedback and response:
Readiness levels and supporting examples:
Gaps / blocked access / dependencies:
Next month's learning and bounded delivery:
Changes to supervision or ownership:
```

## D6. Known-issue register template

```text
Issue:
Affected component and environment:
Reproduction and sanitized evidence:
User impact / severity:
Existing behavior or regression:
Owner / backup / dependency:
Approved workaround, if any:
Proposed fix and regression coverage:
Release risk:
Status / next review date:
```

## D7. Release checklist

- [ ] Named owner, backup and experienced escalation contact.
- [ ] Scope and supported backend/client combinations recorded.
- [ ] Correct target environment confirmed, especially native API configuration.
- [ ] Relevant automated checks and integrated acceptance completed.
- [ ] Synthetic fixtures removed from distribution/demo artifacts where applicable.
- [ ] Migration impact and recovery plan approved, if applicable.
- [ ] Signing, versioning and upgrade evidence verified, if applicable.
- [ ] GPS/notification behavior verified at the required environment/device level.
- [ ] Rollout order, monitoring and stop/rollback criteria agreed.
- [ ] Release notes, runbooks and download/version metadata updated as needed.
- [ ] Post-release behavior verified without exposing personal data.

## D8. Final handover acceptance

| Acceptance item | Full-stack evidence | Native-mobile evidence | Approver |
|---|---|---|---|
| Safe reproducible setup | Backend/web and disposable database | Both apps targeting local/staging | Team mentor |
| Domain understanding | Lifecycle, tenancy, transactions and outbox | Canonical state, freshness and device behavior | Engineering owner |
| Quality practices | Meaningful unit/integration/UI regression | Unit/state/UI/device evidence | Team mentor |
| Compatible delivery | Approved backend/web change | Joint mobile/backend acceptance | Product/engineering owners |
| Operational readiness | Supervised deployment, migration and recovery | Signing, install/update and device exercise | Release/operations owner |
| Incident readiness | Tracking/provider/database diagnosis | Client/permission/provider diagnosis | Experienced escalation owner |
| Sustainable ownership | Maintained runbooks and backup owner | Repeatable build/release and backup owner | Engineering owner |

Record any incomplete item with its risk, owner and remediation date. Do not label the entire handover complete while critical operational or compatibility gaps remain.

## D9. Document maintenance and learning references

Review this guide monthly during onboarding and whenever architecture, commands, contracts or release procedures change.

The repository-specific observations here were checked against component READMEs, package manifests, native Gradle files and existing test locations on November 1, 2026. They are a baseline to recheck, not permanent version guarantees.

Recommended primary learning materials:

- Mozilla MDN: Core Curriculum, JavaScript fundamentals and HTTP learning material.
- React: official Learn material.
- Express, PostgreSQL and Sequelize: official documentation matching installed versions.
- Jest: Getting Started, assertions, asynchronous tests and mocking documentation.
- Android Developers: Android Basics with Compose, testing fundamentals and Compose testing.
- Kotlin: official language and coroutine documentation.
- Android Developers: lifecycle, architecture, permissions, notifications and app signing.
- Martin Fowler: Test Driven Development, including red-green-refactor.
- GitHub Docs: pull-request review, code ownership, protected branches and deployment environments.

The programme proposes improvements and training; it does not claim those repository or deployment controls have already been configured.
