# GitHub Project design — Dashboard 2.0

**Status:** Superseded on 2026-10-13<br>
**Project owner:** `geostock` organization<br>
**Project name:** `Dashboard 2.0`<br>
**Purpose:** Coordinate product, design, data, engineering, marketing, support and founder decisions across GeoStock repositories.

> **Superseded:** Dashboard 2.0 now uses the existing GEOS Jira project as its initiative record: [GEOS-18](https://otpcloud.atlassian.net/browse/GEOS-18). GitHub issues and pull requests remain the engineering execution record. Do not create this GitHub Project.

## Historical decision

Use one organization-level GitHub Project. Keep implementation truth in repository issues and pull requests. The Project is the cross-repository view; it must not become a second issue tracker.

Use the existing `geostock/pages#4` build issue as the parent delivery issue after its scope is reconciled with the Dashboard 2.0 PRD. Keep `geostock/pages#2` as the earlier proposal and link it as superseded context. Add `geostock/frontend#103` as the known instrumentation dependency. Review `geostock/backend#68` before adding it because its current scope is described as optional later work.

## Project README

> **Goal:** Show merchants whether GeoStock is delivering trustworthy location availability, what needs attention, who owns the fix, and the next action.
>
> **Current phase:** Phase 0 — definition and source audit.
>
> **Launch rule:** No merchant-facing financial claims without validated order-level attribution. Core reliability visibility stays in Base.
>
> **Source documents:** PRD · measurement contract · alert policy · rollout plan · evidence register · decision log.

Add links to the versioned files in `docs/initiatives/dashboard-2/` after the product pack is moved into the GeoStock repository.

## Work hierarchy

Use GitHub's native issue hierarchy:

1. **Parent issue — Feature:** Dashboard 2.0 delivery (`pages#4`, revised).
2. **Sub-issues — Features:** merchant-visible capabilities such as current health, coverage, reliability history and alerts.
3. **Sub-issues — Tasks:** source audit, metric definitions, telemetry, reconciliation, security, QA and release work.
4. **Bugs:** defects found during shadow measurement, beta or production.

Do not create a custom Epic type initially. Parent issue and sub-issue progress already provide the hierarchy and roll-up.

## Fields

### Native GitHub fields

| Field | Use |
| --- | --- |
| Assignee | One directly responsible person |
| Repository | Where the work will ship |
| Issue type | Feature, Task or Bug |
| Parent issue | Connect work to the Dashboard 2.0 delivery issue |
| Sub-issue progress | Automatic completion roll-up |
| Linked pull requests | Implementation and review state |

### Project fields

| Field | Type | Values |
| --- | --- | --- |
| Status | Single select | Backlog · Ready · In progress · In review · Validate · Done |
| Priority | Single select | P0 launch blocker · P1 required · P2 later |
| Phase | Single select | 0 Definition · 1 Shadow · 2 Internal pilot · 3 Merchant beta · 4 General release |
| Workstream | Single select | Product · Design · Data · Backend · Frontend · Marketing · Support · Release |
| Evidence | Single select | Unknown · Defined · Instrumented · Reconciled · Merchant-verified |
| Iteration | Iteration | Two-week delivery cycle |
| Target date | Date | Only for committed gates or external deadlines |

`Blocked` is not a Status value. Use GitHub's native issue dependencies so the board shows the real blocker and does not hide where work stopped.

Founder is an approver, not a delivery workstream. Mark founder decisions with the `founder-decision` label and assign the specific decision issue to the founder. This keeps executive approvals visible without routing ordinary delivery work through the founder.

## Saved views

| View | Layout | Configuration | Main use |
| --- | --- | --- | --- |
| **Now** | Board | Columns by Status; filter `status:Ready,"In progress","In review",Validate` | Daily execution |
| **Phase plan** | Roadmap | Group by Phase; use Iteration or Target date | Sequence and timing |
| **Evidence gates** | Table | Filter `-evidence:Reconciled -evidence:"Merchant-verified"`; group by Evidence | Prevent unsupported metrics from shipping |
| **Launch readiness** | Table | Filter `priority:"P0 launch blocker","P1 required" -status:Done`; group by Workstream | Release review |
| **My work** | Board | Filter `assignee:@me -status:Done`; columns by Status | Individual focus |

The founder uses **Launch readiness**, filtered to `label:founder-decision`, instead of maintaining a separate executive tracker.

## Built-in automation

Enable these first:

1. Set newly added items to `Backlog`.
2. Set closed issues and merged pull requests to `Done`.
3. Return reopened issues to `Ready`.
4. Auto-archive `Done` items after 30 days. Project Insights does not include archived items, so retain them until the post-launch review is complete.
5. Auto-add open issues carrying the `dashboard-2.0` label. If the GitHub plan allows only one auto-add workflow, use it for `geostock/pages` and add cross-repository items manually until the plan is confirmed.

Do not add custom GitHub Actions initially. Native workflows, linked pull requests and issue dependencies cover the first release with less maintenance.

## Initial backlog

| Proposed item | Type | Repository | Phase | Priority | Evidence exit |
| --- | --- | --- | --- | --- | --- |
| Dashboard 2.0 delivery | Feature / parent | `pages` | 0–4 | P0 | All launch gates passed |
| Approve eligible location-product rules | Task | `pages` | 0 | P0 | Defined |
| Design source and tenant-scoped API | Task | `backend` | 0 | P0 | Defined |
| Capture delivery-stage telemetry | Feature | `backend` | 1 | P0 | Instrumented |
| Instrument merchant dashboard actions | Task | `frontend` | 1 | P1 | Instrumented |
| Reconcile three test shops for seven days | Task | `backend` or analytics owner | 1 | P0 | Reconciled |
| Build current health, issues and coverage states | Feature | `frontend` | 2 | P0 | Reconciled |
| Build alert suppression, recovery and simulation | Feature | `backend` | 2 | P0 | Reconciled |
| Validate empty, partial, incident and recovery UX | Task | `frontend` | 2 | P0 | Merchant-verified or approved test-shop proof |
| Prepare support diagnosis and escalation playbook | Task | `pages` or confirmed support repository | 2 | P1 | Support simulation passed |
| Run bounded merchant beta and evaluate guardrails | Task | `pages` | 3 | P1 | Merchant-verified |
| Validate merchant-facing positioning and release message | Task | `pages` or confirmed marketing repository | 3 | P1 | Claims match reconciled evidence |
| Approve Base/Plus release packaging | Task | `pages` | 4 | P1 | Merchant evidence recorded |
| Approve general-release go/no-go | Task | `pages` | 4 | P0 | Founder decision recorded |

Repository assignments for analytics, marketing and support work must be confirmed before creating those issues. Do not invent repositories.

## Project Insights

Create only three charts:

1. **Launch blockers by workstream:** open P0 items grouped by Workstream.
2. **Evidence readiness:** item count grouped by Evidence and Phase.
3. **Burn-up:** open versus completed work over time.

These charts measure delivery health. Merchant value and product outcomes remain in PostHog or the approved analytics source, linked from the Project README.

## Operating rules

- Every active issue needs an assignee, acceptance criteria, Priority, Phase and Evidence state.
- An issue enters `Ready` only after dependencies and acceptance criteria are clear.
- `In review` means a pull request or explicit PM/design review exists.
- `Validate` means the change is built but its stated evidence or launch gate is not yet proven.
- Close as `not planned` when scope is rejected; do not relabel it Done.
- Post a short GitHub Project status update weekly: progress, current blockers, evidence gained and next gate.

## Stakeholder contract

| Stakeholder | Owns | Reviews in GitHub | Required decision or output |
| --- | --- | --- | --- |
| Development | Source design, telemetry, APIs, UI, alerts, security and fixes | Now · Evidence gates | Technical feasibility and verified implementation |
| Product | PRD, priority, metric definitions, acceptance and rollout | All views | Scope and launch-gate approval |
| Marketing | Positioning, plan packaging and evidence-safe release message | Launch readiness | Claims use only reconciled evidence |
| Support | Diagnosis steps, escalation ownership, merchant language and beta feedback | Now · Launch readiness | Support simulation and operating playbook |
| Founder | Value proposition, investment, Base/Plus boundary and go/no-go | Launch readiness filtered to `founder-decision` | Explicit decision recorded in its issue |

Design, Data and Release remain contributing workstreams. They support the five named stakeholder groups without requiring separate tracking systems.

## Creation checklist

1. Reauthenticate GitHub CLI with the GeoStock organization account.
2. Confirm organization owner permission and GitHub plan limits.
3. Create the organization Project and add its README.
4. Add fields, views and native workflows from this design.
5. Reconcile existing issues before creating the missing sub-issues.

## Official GitHub references

- [Best practices for Projects](https://docs.github.com/en/issues/planning-and-tracking-with-projects/learning-about-projects/best-practices-for-projects)
- [Using built-in automations](https://docs.github.com/en/issues/planning-and-tracking-with-projects/automating-your-project/using-the-built-in-automations)
- [Adding items automatically](https://docs.github.com/en/issues/planning-and-tracking-with-projects/automating-your-project/adding-items-automatically)
- [Parent issue and sub-issue progress fields](https://docs.github.com/en/issues/planning-and-tracking-with-projects/understanding-fields/about-parent-issue-and-sub-issue-progress-fields)
- [Project layouts](https://docs.github.com/en/issues/planning-and-tracking-with-projects/customizing-views-in-your-project/changing-the-layout-of-a-view)
- [Project Insights](https://docs.github.com/en/issues/planning-and-tracking-with-projects/viewing-insights-from-your-project/about-insights-for-projects)
