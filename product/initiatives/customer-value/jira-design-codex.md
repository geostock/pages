# Jira delivery design — Dashboard 2.0

**Status:** Epic, shared filter, Kanban board, and initiative tickets implemented on 2026-10-13<br>
**Initiative:** [GEOS-18 — Dashboard 2.0 — Availability you can trust](https://otpcloud.atlassian.net/browse/GEOS-18)<br>
**Owner:** Vijay until functional owners accept their work

## Delivery record

- Jira is the delivery home for the initiative, priorities, evidence gates and founder decisions.
- Shared filter: `Dashboard 2.0` (shared with all GeoStock project roles).
- Kanban board: [`Dashboard 2.0`](https://otpcloud.atlassian.net/jira/people/712020:fff16753-01fa-4a7d-b9f8-beb87c56569d/boards/135), backed by that filter.
- GitHub remains the source for engineering execution, implementation issues and pull requests.
- No new Jira code ticket duplicates `pages#2`, `pages#4`, `frontend#97` or `backend#68`; reconciliation is tracked in [GEOS-20](https://otpcloud.atlassian.net/browse/GEOS-20).
- Existing reliability work [GEOS-10](https://otpcloud.atlassian.net/browse/GEOS-10) and [GEOS-13](https://otpcloud.atlassian.net/browse/GEOS-13) are Epic children. Completed PostHog context [GEOS-11](https://otpcloud.atlassian.net/browse/GEOS-11) is related work. `GEOS-16` is intentionally excluded unless email alerts are approved.

## Active Jira fields

The GEOS project is team-managed. Both fields are active on the Task work type and values are set for every active Dashboard 2.0 record:

- `Phase`: Definition, Shadow measurement, Internal pilot, Merchant beta, General release
- `Evidence state`: Unknown, Defined, Instrumented, Reconciled, Merchant verified

## Remaining board configuration

The Jira board interface available to this project does not expose saved board quick-filter administration. Add the following filters when that control is available, then confirm access with one user from each stakeholder group:

```jql
project = GEOS
AND (key = GEOS-18 OR parent = GEOS-18)
ORDER BY Rank ASC
```

| Name | JQL |
| --- | --- |
| Founder decisions | `labels = founder-decision AND resolution IS EMPTY` |
| Evidence missing | `"Evidence state" NOT IN ("Reconciled", "Merchant verified")` |
| Marketing | `labels = ws-marketing` |
| Support | `labels = ws-support` |
| Development | `labels = ws-development` |

Keep the existing `To Do → In Progress → Done` workflow and leave sprints disabled.

## Work-package mapping

| Package | Jira records |
| --- | --- |
| Definition | GEOS-19 to GEOS-22 |
| Build and measurement | GEOS-20, GEOS-25 plus linked GitHub work |
| Alerts and operations | GEOS-23, GEOS-24, GEOS-26 |
| Launch | GEOS-27 to GEOS-29 |

Each active record includes an owner, outcome, acceptance criteria, dependency, evidence requirement, Phase and Evidence state. Phase and Evidence state are also structured Jira fields.

## Launch validation

- The filter-backed board must contain only GEOS-18 and its children.
- Stakeholder quick filters must be visible to founder, product, development, marketing and support.
- No unrelated GEOS ticket may change.
- Every Done ticket needs an evidence link or validation comment.
- The founder view must show only unresolved `founder-decision` work.
