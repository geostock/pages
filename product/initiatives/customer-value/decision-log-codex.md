# Dashboard 2.0 decision log

## Approved direction from current evidence

| ID | Decision | Reason | Revisit when |
| --- | --- | --- | --- |
| D-001 | Lead with “Availability you can trust” | Reliability and freshness have the strongest recurring evidence and are prerequisites for location-aware availability | Freshness complaints fall materially while another problem becomes dominant |
| D-002 | Do not show recovered revenue, saved orders or avoided cancellations | No validated attribution or confirmed merchant dollar-loss evidence exists | Order-level attribution is designed and independently validated |
| D-003 | Core health and incidents belong in Base | Merchants should not pay extra to learn whether the core service is working | Never; this is a product-trust principle |
| D-004 | Plus may monetize depth and control | Longer history, custom thresholds, exports and advanced analysis add value without withholding core truth | Merchant evidence shows different willingness to pay |
| D-005 | Alerts must name the recovery owner | Merchants cannot act on GeoStock-owned infrastructure failures | Ownership classification proves unreliable |
| D-006 | Freshness alone cannot be labeled accuracy | A recent timestamp does not prove storefront output or correct inventory | End-to-end verification supports a stronger claim |
| D-007 | Targets remain unapproved before baselines | The proposed 15-minute and 99% values lack verified baseline and tolerance evidence | Baseline and service-objective review is complete |
| D-008 | Jira is the Dashboard 2.0 initiative record; GitHub remains the code-execution record | GEOS now has an Epic and initiative tickets while existing repository issues and pull requests remain the engineering source of truth | The team explicitly approves a different initiative system |
| D-009 | Defer merchant interviews; use the source audit for the next scope decision | Product needs to know which claims current data can support before testing a concrete V1 | Source audit defines a supportable V1 or merchant beta planning begins |

## Pending decisions

| ID | Decision needed | Owner | Blocking artifact |
| --- | --- | --- | --- |
| P-001 | Exact eligible product/location rules | PM + Engineering | Measurement contract approval |
| P-002 | Freshness and reliability targets | PM + Analytics + Engineering | Baseline report |
| P-003 | Storefront verification method | Engineering | Technical design |
| P-004 | Alert confirmation and recovery windows | PM + Analytics | Shadow-mode results |
| P-005 | Merchant email consent and release policy | PM + Operations | Alert launch approval |
| P-006 | Plus packaging and pricing | PM + Marketing | Merchant-value and willingness-to-pay evidence |

## Superseded proposals

- “Orders saved,” “cancellations avoided,” and “stock questions stopped” as live dashboard cards.
- Recovered revenue as the lead merchant value.
- Back-in-stock funnel reporting before the feature exists.
- A fixed 15-minute freshness or 99% reliability target without baseline evidence.
- A separate GitHub Project for Dashboard 2.0 delivery tracking. It is superseded by the GEOS Jira delivery design.
