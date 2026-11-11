# Carribu Product Manager Workbook

**Status:** Reusable planning template; no actual product commitments, launch approvals or quarterly results have been entered.

Use this workbook to manage **whole products from discovery to launch and measured adoption**, and to agree **what each quarter should achieve**. A product can span several repositories: define its user value and boundary rather than treating every app or backend as an independent product by default.

## 1. How the workbooks fit together

| Document | Source of truth for |
|---|---|
| This workbook | Product portfolio, strategic priorities, quarterly expectations, roadmap, launch readiness and post-launch results |
| [Product Tracking Workbook](PRODUCT-TRACKING-WORKBOOK.md) | Day-to-day work priorities within the agreed product direction, cycle plans, owners, blockers and delivery evidence |
| Owning repository issues and PRs | Implementation requirements, technical discussion, code review and checks |
| [Developer Playbook](DEVELOPER-PLAYBOOK.md) | Engineering contribution rules, release safeguards and incident responsibilities |

Link product and objective IDs to delivery outcomes/work IDs; do not copy all implementation tasks into this workbook. The product manager maintains the portfolio and forecasts. Product/business sponsors approve priorities and expectations; engineering and operational owners approve feasibility and readiness in their areas.

Use `YYYY-MM-DD` dates. Write `Not agreed`, `Not assigned` or `Not measured` instead of guessing. Treat target dates as forecasts unless an authorized commitment is explicitly recorded. Do not copy personal records, confidential customer details, credentials or sensitive incident evidence here; use approved restricted references.

## 2. Product portfolio dashboard

Keep one row per product or explicitly scoped launch initiative, not one row per feature.

| Product ID / name | Target users / problem | Accountable PM / sponsor | Lifecycle stage | Current-quarter objective IDs | Next milestone / forecast date | Health / reason | Biggest dependency / next decision | Last updated |
|---|---|---|---|---|---|---|---|---|

Allocate stable IDs such as `PROD-001`. Never recycle them. Define components in the product brief so a product spanning backend, admin, driver and parent apps is visible as one coordinated delivery.

| Lifecycle stage | Evidence needed to progress |
|---|---|
| Discovery | User problem, existing alternatives, baseline evidence and material unknowns captured |
| Defined | Sponsor agrees target users, value, launch scope, success measures and exclusions |
| Delivery | Owners, capacity, dependencies, acceptance criteria and feasible rollout plan agreed |
| Pilot | Controlled audience, operational safeguards, pilot acceptance and stop criteria approved |
| Launch preparation | Pilot findings addressed or explicitly accepted; launch gates and communications being completed |
| Live | Authorized launch completed for the defined audience with verification and monitoring |
| Optimization | Post-launch evidence drives adoption, quality or value improvements |
| Paused / Retired | Authorized decision, rationale and continuity/data/support obligations recorded |

Lifecycle is not delivery health. A product may be in Delivery and At risk.

**Health:** On track = evidence supports the current forecast; At risk = an unresolved risk threatens scope/date/outcome; Off track = an agreed expectation is already missed or no longer feasible; Not assessed = evidence is insufficient. Report the reason, next action and decision-maker, not a color alone.

## 3. Product brief template

Create one brief per product, here or in a linked maintained document:

| Field | Fill in |
|---|---|
| Product ID / name / PM / sponsor | |
| Target users and problem | |
| Evidence of need / current baseline | |
| Intended user and business outcomes | |
| Proposed value / alternatives considered | |
| Launch audience and supported platforms | |
| In-scope launch journeys | |
| Explicit exclusions and later opportunities | |
| Components, teams and accountable engineering owners | |
| Measures, data source, owner and measurement window | |
| Capacity, budget assumptions and constraints | |
| Dependencies, privacy/security considerations and risks | |
| Pilot approach and success/stop criteria | |
| Launch forecast, assumptions and decision authority | |
| Post-launch support and outcome-review owner | |
| Linked delivery outcome/work IDs | |

A brief is ready for delivery planning only when scope, measures, ownership and important unknowns are explicit. Discovery may conclude with a decision not to build.

## 4. Quarterly expectations

Agree expectations before the quarter starts and review them monthly. Label quarters with a year and exact dates. Calendar quarters are Q1 January-March, Q2 April-June, Q3 July-September and Q4 October-December; if the organization uses a fiscal calendar, record that calendar and use it consistently.

### Quarter agreement

| Field | Value |
|---|---|
| Quarter and start/end dates | Not agreed |
| Strategic theme / intended business outcome | Not agreed |
| Sponsor / accountable product manager | Not assigned |
| Available capacity / budget and constraints | Not agreed |
| Priority order across products | Not agreed |
| Agreed exclusions / work deliberately deferred | Not agreed |
| Sponsor and engineering feasibility approvals / date | Not recorded |
| Monthly checkpoints and quarter-end review | Not agreed |

### Objectives and measurable expectations

| Objective ID | Product ID | Intended outcome | Baseline / source | Quarter-end target / measurement window | Minimum / target / stretch | Accountable owner | Linked milestones / delivery outcomes | Health / evidence | Latest forecast |
|---|---|---|---|---|---|---|---|---|---|

Use IDs such as `OBJ-2027-Q1-001`. Separate:

- **Minimum:** The smallest approved useful outcome, not permission to waive safety or launch gates.
- **Target:** The agreed expected outcome for planning.
- **Stretch:** Optional upside if capacity and evidence allow; not a hidden commitment.

Define units, population, numerator/denominator where relevant, source and observation period. Pair speed/adoption targets with quality and safety guardrails. If no baseline exists, first agree a measurement task and when the target will be decided; do not invent a baseline.

An output such as "ship parent app" is a milestone, not sufficient proof of value. Pair it with an outcome such as successful completion of the agreed parent journey by the intended pilot audience. Targets require sponsor agreement and engineering feasibility review.

### Monthly expectation check

| Checkpoint date | Objective ID | Actual / evidence to date | Forecast against target | Risk / variance reason | Decision or corrective action / owner / due date |
|---|---|---|---|---|---|

Do not silently edit the original target when forecasts change. Record approved changes and their impact in the decision log.

## 5. Roadmap and product-to-launch milestones

Use one row per meaningful gate or integrated outcome. Link implementation details to the delivery tracker.

| Milestone ID / product ID | Outcome / exit criteria | Owner | Dependencies | Original target | Current forecast | Status / evidence | Linked delivery IDs |
|---|---|---|---|---|---|---|---|

Suggested milestones: validated problem, approved launch scope, integrated journey demonstrated, pilot entry approved, pilot exit accepted, launch decision, controlled rollout, post-launch outcome review. Adapt them to the product; they are not automatic approvals.

Milestone statuses: Not started, In progress, Blocked, Accepted, Cancelled. Accepted requires evidence and the accepting owner. A completed milestone is not proof every later launch gate is satisfied.

## 6. Launch readiness and go/no-go

Define the launch audience, scope, version set and decision date before collecting approvals. Product acceptance, engineering readiness and operational approval are distinct responsibilities.

| Gate | Required evidence | Accountable approver | Status / evidence link / date |
|---|---|---|---|
| User journeys and scope | Agreed end-to-end journeys pass, including relevant failure and accessibility scenarios | Product owner with affected component owners | Not assessed |
| Engineering quality | Relevant automated/integration/device evidence; defects triaged with explicit release impact | Engineering owner | Not assessed |
| Safety, tenancy and privacy | Required authorization, school isolation, student-state and data-handling checks; approved safeguards | Responsible engineering/security/privacy owners | Not assessed |
| Compatibility and data | Supported client versions, migrations and rollout order verified | Backend and client owners | Not assessed |
| Distribution and configuration | Correct environment, artifacts, signing/versioning and intended channels verified | Release/mobile owners | Not assessed |
| Operations and recovery | Monitoring, escalation, support coverage, backup/recovery and stop/rollback criteria ready | Operations/release owner | Not assessed |
| Product and support readiness | Pilot acceptance, training/support guidance and audience communications prepared | PM and support owner | Not assessed |
| Outcome measurement | Baseline, permitted data collection, measures and post-launch review scheduled | PM and measurement owner | Not assessed |

Gate statuses: Not assessed, In progress, Passed, Blocked, Not applicable. A Not applicable entry requires rationale and responsible-owner approval. Critical safety/privacy requirements cannot be waived to meet a date; unresolved mandatory gates mean No-go.

### Launch decision record

| Product / launch scope and version set | Decision date | Decision: Go / No-go / Hold | Evidence / unresolved risks | Authorized decision-maker and required sign-offs | Rollout owner / window | Stop criteria and recovery owner | Next review |
|---|---|---|---|---|---|---|---|

Use Hold when a decision awaits evidence; use No-go when requirements are not met. Go applies only to its recorded audience, versions and window, not all future releases. The PM coordinates the decision but does not override technical safeguards. Keep restricted evidence in approved systems.

## 7. Post-launch adoption and value

Launch is not the end of product tracking. Schedule explicit early health checks and a later outcome review appropriate to the product. Distinguish artifact distribution, user adoption and achieved value.

| Product / launch reference | Measure / definition | Baseline | Target / observation window | Actual / sample size / evidence date | Data source / owner | Quality guardrail | Decision / next action |
|---|---|---|---|---|---|---|---|

Examples of measures to agree: eligible-user activation, successful completion of a critical journey, support demand, reliability and time saved. Record insufficient samples or unavailable data honestly. Do not infer receipt/read behavior from notification provider acceptance.

## 8. Quarterly review and next-quarter handoff

| Objective ID | Original target / approved changes | Actual result / evidence / measurement window | Assessment | Variance and learning | Next-quarter decision / owner |
|---|---|---|---|---|---|

Assess as Met, Partially met, Not met, Not measurable or Cancelled by approved decision. Link the original agreement and any approved revision. An unlaunched product can meet a discovery objective; a launched product can still miss its adoption target.

At quarter close, archive the agreement, evidence and decisions. Carryover needs a fresh priority and capacity decision, not an automatic commitment. Start the next quarter with updated baselines and explicit tradeoffs.

### Dependencies, risks and scope decisions

| ID / date | Product / objective IDs | Risk, dependency or requested change | Impact on scope/date/outcome | Accountable owner / decision-maker | Action or approved decision / rationale | Due/review date / status |
|---|---|---|---|---|---|---|

### Working cadence

| Cadence | PM action |
|---|---|
| Weekly | Review portfolio health, milestone forecasts and delivery blockers with owners; request specific decisions |
| Monthly | Compare objective evidence with quarterly expectations; agree corrective actions and preserve target history |
| Before launch | Complete readiness gates and record explicit go/no-go and operational ownership |
| After launch | Review health, adoption, support signals and user outcomes at the agreed checkpoints |
| Quarter end | Assess actual results, document learning and agree next-quarter priorities with sponsors and engineering |

## 9. Worked example - fictional, not a live plan

**All names, roles, dates, numbers, evidence descriptions and approvals below are illustrative. No actual Carribu launch, customer result or quarterly commitment is asserted.** Role labels must be replaced with accountable people; evidence descriptions must be replaced with real approved links. No personal data is needed.

### Example product and quarter agreement

| Field | Fictional example |
|---|---|
| Product | EXAMPLE-PROD-001: Coordinated school transport pilot |
| Audience / scope | Approved pilot operators and guardians; one morning and afternoon journey across admin, backend, driver and parent surfaces |
| PM / sponsor | Example PM / example product sponsor |
| Quarter | Calendar Q1 2027: `2027-01-01` to `2027-03-31` |
| Theme | Validate safe, understandable end-to-end pilot journeys before considering broader availability |
| Capacity assumption | One cross-functional team with part-time support/operations coverage; feasibility must be confirmed in a real plan |
| Exclusions | No broad public rollout, billing feature or automatic fallback for an offline linked tracker |
| Approval | Assumed sponsor and engineering agreement for teaching purposes only |

| Objective ID | Intended outcome | Baseline / source | Minimum / target / stretch and guardrails | Owner / linked delivery |
|---|---|---|---|---|
| EXAMPLE-OBJ-2027-Q1-001 | Pilot users can complete the agreed journeys successfully | No pilot observations yet; baseline collection is part of pilot setup | Minimum: approved staging demonstration. Target: at least 18 of 20 observed pilot sessions complete the predefined journey without intervention by `2027-03-31`. Stretch: all 20. Mandatory safety/tenancy gates pass regardless of success rate | Example PM / EXAMPLE-OUT-001 and owning delivery issues |

A session means one predefined role-specific journey under the pilot observation protocol. Success means completing its agreed steps without staff intervention; record failures and exclusions transparently. Twenty sessions are illustrative and do not establish population-wide reliability. Missing observations mean the target is not yet demonstrated, not automatic success.

### Example roadmap

| Milestone | Exit evidence | Original target / forecast at planning | Owner |
|---|---|---|---|
| EXAMPLE-MS-001: Scope approved | Pilot audience, journey definitions, metrics and exclusions accepted | `2027-01-15` / `2027-01-15` | Example PM |
| EXAMPLE-MS-002: Integrated staging acceptance | Relevant cross-app, rejection, tenancy and device cases accepted | `2027-02-12` / `2027-02-12` | Example engineering lead |
| EXAMPLE-MS-003: Pilot launch decision | All mandatory pilot gates passed and Go recorded | `2027-02-26` / `2027-02-26` | Example sponsor and responsible owners |
| EXAMPLE-MS-004: Pilot outcome review | Observed journey results and support findings reviewed | `2027-03-31` / `2027-03-31` | Example PM |

### Example checkpoint, launch hold and decision

At the fictional `2027-02-19` checkpoint, background/resume device evidence is missing. Portfolio health becomes At risk; the readiness gate remains Blocked, even if code has merged.

| Decision ID | Requested tradeoff | Decision / accountable owner | Forecast impact / next action |
|---|---|---|---|
| EXAMPLE-DEC-001 | Keep the pilot date or wait for mandatory device evidence | Hold launch; example sponsor and engineering lead retain the gate | Move forecast from `2027-02-26` to `2027-03-05`, subject to completed evidence; example mobile owner arranges validation |

The original target remains visible. In this fictional sequence, a later `2027-03-04` readiness review passes all mandatory pilot gates and authorizes Go for the limited pilot on `2027-03-05`. That decision does not authorize broader rollout.

### Example quarter-end assessment

Assume the fictional pilot completed 20 observed sessions during `2027-03-05` through `2027-03-31`. Seventeen completed without intervention; three needed help recovering from connectivity loss. The example evidence would be an approved aggregate observation report, not personal journey records in Git.

| Objective | Original target | Actual result | Assessment | Next-quarter expectation to propose |
|---|---|---|---|---|
| EXAMPLE-OBJ-2027-Q1-001 | At least 18/20 successful sessions, with all mandatory safeguards met | 17/20 (85%); limited pilot launched after the recorded hold; mandatory safeguards assumed passed in this illustration | Partially met: staging/pilot milestones achieved, target success rate missed | Prioritize connectivity recovery and agree a fresh observation window, sample and target; do not broaden rollout automatically |

The honest product summary is: **limited pilot launched; quarter-end outcome target missed; recovery improvements require prioritization**. It is not "product complete" merely because applications were distributed.
