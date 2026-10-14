# Dashboard 2.0 measurement contract

**Status:** Draft. Thresholds and targets are not approved until baselines exist.

## Contract

| Metric | Previous proposal | Dashboard 2.0 definition | Formula | Authoritative source | Current readiness |
| --- | --- | --- | --- | --- | --- |
| Availability verified current | Inventory updated within 15 minutes | Eligible location-product pairs updated within the approved freshness window and successfully verified on the storefront | verified-current eligible pairs / all eligible pairs | Update receipt + processing result + publish result + storefront check | Not ready; continuous freshness and storefront telemetry not confirmed |
| Locations needing attention | Locations receiving valid updates | Enabled locations with repeated stale, failed or storefront-mismatched checks | distinct affected enabled locations | Location health ledger | Not ready; health ledger required |
| Affected products | Products showing current stock | Unique products that may currently show stale or unverified location availability | distinct affected products in active incidents | Incident state joined to product eligibility | Not ready |
| Time below target | Missing | Total duration verified coverage remained below the approved target | sum of below-target intervals | Versioned health snapshots | Not ready; target and snapshot source required |
| Protection coverage | Locations correctly protected | Eligible locations where purchase protection is configured and verified active on the storefront | verified protected eligible locations / eligible locations | Configuration + storefront behavior check | Partial; configuration may exist, verification not confirmed |
| Last verified update | Last successful inventory update | Most recent time the complete update path succeeded for the affected scope | max verified completion timestamp | End-to-end update ledger | Not ready |

## Required dimensions

- `shop_id`
- environment
- location ID
- product and variant ID
- metric definition version
- eligibility reason
- event/result timestamp
- failure stage
- owner: GeoStock, Shopify/upstream, merchant configuration or unknown

## Definitions that must be approved

### Eligible location-product pair

A pair is eligible only when the location and product are enabled for GeoStock storefront availability. Exclusions must be explicit and versioned. Changing eligibility cannot silently improve historical coverage.

### Verified current

“Verified current” requires proof that the accepted inventory state completed the delivery path being measured. A backend timestamp alone may be called “recently processed,” not “verified current.”

### Incident

An incident begins after the same qualifying failure is observed across the approved confirmation window. It ends after the required consecutive successful checks. Exact windows require baseline data.

## Data quality states

| State | Display behavior |
| --- | --- |
| Complete | Show value, scope, last refresh and definition |
| Partial | Show partial-data label and affected scope |
| Missing | Show “Not enough data yet” |
| Instrumentation failure | Show measurement unavailable; never show zero or healthy |
| Preview | Clearly label all values as examples |

## Reconciliation

- Validate three test shops representing small, medium and large catalogs.
- Reconcile every metric within 5% of the authoritative source.
- Investigate denominator drift separately from numerator drift.
- Preserve the metric version used for every historical point.

## Prohibited interpretations

- Freshness is not inventory accuracy.
- Protected purchase attempts are not saved orders.
- Storefront interactions are not revenue.
- Alert opens are not resolved incidents.
- Plan events are not payment evidence.
