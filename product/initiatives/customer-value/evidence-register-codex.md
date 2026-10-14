# Dashboard 2.0 evidence register

**Evidence labels:** Verified, reported, inferred, unknown.

## Evidence supporting the direction

| Claim | Evidence | Label | Product implication |
| --- | --- | --- | --- |
| Inventory sync and freshness is the strongest recurring problem | Roughly 20–25 distinct merchants across outage, location-import, variant-staleness and third-party-location buckets, with overlap not fully deduplicated | Reported; highest confidence among reviewed problems | Lead with reliability and availability trust |
| A known webhook failure mode exists | Jira GEOS-9 is reported Done; GEOS-10 remains open with a title describing recurring webhook removal | Verified ticket existence/status; causal links inferred | Continuous webhook health is a dependency |
| Wrong-location risk occurs | 10 merchants and 11 incidents; one merchant cited two Shopify order numbers | Reported; orders not independently confirmed | Show exposure and protection, not saved orders |
| Dollar loss is known | Zero merchant-stated dollar-loss figures were found | Unknown, not zero economic impact | Do not show recovered revenue |
| GeoStock caused cancellations or refunds | Zero confirmed cases found | Unknown | Do not show cancellations avoided |
| Back-in-stock performance exists | Feature does not exist; no shopper funnel events | Verified absence in reviewed systems | Exclude from Dashboard 2.0 |
| Current continuous freshness metric exists | No usable current metric found; `inventory_sync_completed` was a discontinued five-week backfill event | Verified within reviewed PostHog evidence | Instrument before release |

## Coverage limits

- Support review covered 176 conversations in the 12-month window; 48 initially hit a 40-message cap and were re-fetched, but all additional earlier messages were not individually reread.
- Current partial month was excluded.
- Email, Shopify App Store reviews, calls, Slack and the product database were not searched.
- Jira ticket bodies were not fully reviewed in the support report.
- Shopify orders and raw production logs were not independently checked.
- True current sync architecture is not fully confirmed from support statements.

## Assumptions requiring validation

| Assumption | Required proof |
| --- | --- |
| A fixed freshness window works for all merchants | Production update-age distribution by store type and expected update frequency |
| 99% is the correct reliability target | Baseline reliability, merchant tolerance and engineering service objective |
| Storefront verification is feasible at required scale | Technical design, cost, sampling and failure-mode analysis |
| Dashboard exposure changes retention | Comparable cohort or controlled experiment |
| Email alerts are wanted and permitted | Channel consent, deliverability and merchant research |
| Plus merchants value advanced history and exports | Usage or willingness-to-pay evidence |

## Evidence still needed

1. Live webhook subscription status and time since last successful update by shop.
2. End-to-end update ledger from receipt through storefront result.
3. Eligible product/location denominator from the application database.
4. Incident owner classification and recovery timestamps.
5. Merchant interviews about the last concrete stale-stock or wrong-location incident.
