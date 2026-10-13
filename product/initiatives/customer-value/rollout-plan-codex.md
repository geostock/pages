# Dashboard 2.0 rollout and experiment plan

**Status:** Draft. Dates and effort belong to engineering after technical design.

## Objective

Prove that the dashboard reports reliable information, prompts appropriate action, and improves merchant confidence without creating false financial claims or alert fatigue.

## Phase 0 — Definition and source audit

Deliverables:

- Approved metric eligibility rules.
- Source owner for each delivery stage.
- Current telemetry inventory.
- Baseline plan by catalog and location size.
- Threat model for tenant isolation.

Exit gate: every proposed metric is classified ready, partial or unavailable.

## Phase 1 — Shadow measurement

- Compute metrics internally without showing merchants.
- Run for at least seven consecutive production days.
- Compare against authoritative sources for three representative test shops.
- Measure missing data, false incidents and recovery behavior.

Exit gate: reconciliation is within 5%, no unexplained denominator drift, and incident states close correctly.

## Phase 2 — Internal and support pilot

- Expose dashboard to GeoStock team and approved test shops.
- Keep external email disabled.
- Simulate all alerts.
- Validate support handoff and ownership labels.

Exit gate: empty, partial, incident and recovery states pass PM/design review; zero cross-shop exposure.

## Phase 3 — Merchant beta

- Release to a bounded eligible merchant cohort.
- Use in-app alerts first.
- Enable email only for approved high-impact and merchant-owned conditions.
- Collect dashboard usefulness feedback after real incidents.

Exit gate: false-alert rate, action completion and support burden meet targets established from Phase 1 baselines.

## Phase 4 — General release

- Release Base reliability view to eligible merchants.
- Introduce Plus capabilities only after Base reliability is stable.
- Publish metric definitions and limitations.
- Review 30-, 60- and 90-day cohort outcomes.

## Experiment design

### Hypothesis

We believe showing verified availability health and giving merchants the correct next action will increase verified setup health and longer-term retention because merchants can see and protect the outcome they pay GeoStock to deliver.

### Primary measures

- Percentage of eligible shops reaching verified healthy coverage.
- Merchant-owned alert-to-corrective-action rate.
- Time from issue detection to verified recovery.
- 60/90-day retention for comparable eligible cohorts.

### Guardrails

- False merchant alerts.
- Support contacts caused by dashboard confusion.
- Instrumentation failure displayed as healthy.
- Cross-shop access failures.
- Core reliability accidentally gated by plan.

### Decision rule

Do not set an uplift target or sample size until eligibility volume, baseline rates and expected exposure are measured. If the eligible population is too small for a credible controlled experiment, use staged cohort evidence and report the limitation.

## RACI

| Work | PM | Design | Frontend | Backend | Analytics | Support |
| --- | --- | --- | --- | --- | --- | --- |
| Metric definitions | A/R | C | C | C | C | C |
| User experience | A | R | C | I | I | C |
| Source and API design | C | I | C | A/R | C | I |
| Instrumentation validation | C | I | C | C | A/R | I |
| Alert operations | A | C | C | R | C | C |
| Release approval | A/R | C | C | C | C | C |

## Rollback conditions

- Any cross-shop data exposure.
- A metric repeatedly fails reconciliation.
- Instrumentation failure displays healthy status.
- Merchant alerts fire for unconfirmed transient events.
- Alert ownership routes merchants to actions they cannot perform.
