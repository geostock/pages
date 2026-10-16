# GeoStock Dashboard 2.0 product package

**Status:** Jira delivery structure is live; product artifacts remain draft for review<br>
**Prepared:** 2026-10-13<br>
**Canonical destination:** `geostock/pages/product/initiatives/customer-value/`

## Why this package exists

Existing GitHub issues describe an early value dashboard, but no current PRD consolidates the reliability-first direction, revised metrics, alerts, plan access, and launch proof.

## Artifacts

| Artifact | Purpose | Status |
| --- | --- | --- |
| [Dashboard 2.0 PRD](dashboard-2-prd-codex.md) | Product problem, scope, requirements, success and boundaries | Draft |
| [Measurement contract](measurement-contract-codex.md) | Exact metric definitions, evidence and known gaps | Draft |
| [Alert policy](alert-policy-codex.md) | Trigger, message, owner, channel, CTA and recovery | Draft |
| [User stories](user-stories-codex.md) | Merchant and operator behavior with acceptance criteria | Draft |
| [Rollout and experiment plan](rollout-plan-codex.md) | Phases, release gates, success measures and rollback rules | Draft |
| [Evidence register](evidence-register-codex.md) | Verified facts, reported evidence, assumptions and unknowns | Draft |
| [Decision log](decision-log-codex.md) | Durable product decisions and unresolved decisions | Draft |
| [Jira delivery design](jira-design-codex.md) | GEOS Epic, filter-backed Kanban board, operating fields and work packages | Implemented; board quick filters pending Jira capability |
| [GitHub Project design](github-project-design-codex.md) | Earlier cross-repository tracker proposal | Superseded by Jira delivery design |

## Dashboard mockups

**Design status:** Draft. Requirements review is in progress; these files do not represent implementation approval.

- [Interactive HTML](mockups/dashboard-2-codex.html)
- [Desktop review render](mockups/dashboard-2-desktop-codex.png)
- [Mobile review render](mockups/dashboard-2-mobile-codex.png)

Mockup values are illustrative. They are not live merchant results or approved metric targets.

## Current source links

- GitHub product issue: https://github.com/geostock/pages/issues/2
- GitHub build issue: https://github.com/geostock/pages/issues/4
- GitHub instrumentation issue: https://github.com/geostock/frontend/issues/103
- Jira initiative Epic: https://otpcloud.atlassian.net/browse/GEOS-18

## Approval sequence

1. PM approves the PRD and evidence boundaries.
2. Engineering confirms telemetry feasibility and source ownership.
3. Design confirms empty, partial-data, incident and recovered states.
4. Analytics establishes baselines before targets are approved.
5. PM reconciles the existing GitHub issues before creating any new implementation issue.
