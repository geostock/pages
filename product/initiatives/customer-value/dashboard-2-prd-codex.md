# GeoStock Dashboard 2.0 PRD

**Status:** Draft<br>
**Owner:** Product<br>
**Target users:** Existing GeoStock merchants operating more than one inventory location<br>
**Product promise:** Availability you can trust

## 1. Overview

### Problem

Merchants configure GeoStock but cannot quickly answer:

1. Is location availability working now?
2. What is wrong?
3. Who is responsible for fixing it?
4. What should I do next?

Current product evidence supports reliability and inventory freshness as the strongest recurring problem. It does not support merchant-facing claims about recovered revenue, saved orders, avoided cancellations, or support time saved.

### Product outcome

Give merchants a trustworthy operational view of GeoStock's delivery and surface problems before they discover them through shopper complaints.

### User outcome

A merchant can understand current availability health and reach the correct recovery action in under one minute.

### Business outcome

Improve confidence in GeoStock's continuing value, reduce preventable configuration failures, and test whether visible reliability improves activation and retention.

## 2. Scope

### Must have

1. **Current status:** one plain-language health statement with the highest-priority problem and one CTA.
2. **Next issues:** remaining problems ranked by shopper exposure, with explicit owner.
3. **Coverage:** locations, products and purchase protection currently verified.
4. **Reliability history:** time below the approved target and meaningful incidents.
5. **Diagnostics:** collapsed technical proof for support and advanced merchants.
6. **Proactive alerts:** problems, recovery, configuration gaps and weekly value delivery.
7. **Data states:** healthy, incident, partial data, no data, instrumentation failure and first-use preview.

### Should have

- Seven-day and 30-day views.
- Location and product drill-downs.
- Previous-period comparison after definitions are stable.
- Links from alerts to the affected dashboard state.

### Could have

- Ninety-day history.
- Custom alert thresholds.
- Export and scheduled reports.
- Advanced country, distance and location analysis.

### Out of scope

- Recovered revenue.
- Orders saved or cancellations avoided.
- Back-in-stock notifications and attribution.
- Individual shopper identity.
- A claim that freshness alone proves inventory accuracy.
- New billing infrastructure.

## 3. Experience requirements

### Information hierarchy

1. Current health and primary action.
2. Remaining problems.
3. Coverage.
4. Reliability history.
5. Technical verification details.

### Copy rules

- State observed conditions: “74 variants may show old stock.”
- State ownership: “GeoStock is reconnecting this location” or “Your setup needs attention.”
- Do not convert protected attempts into orders, cancellations or revenue.
- Show “Not enough data yet” when telemetry is absent.
- Explain preview data wherever examples appear.

### Base and Plus

**Base includes:** current health, affected locations/products, core coverage, setup/failure alerts and seven-day history.

**Plus may include:** 90-day history, custom thresholds, exports, advanced breakdowns and scheduled reports.

Core reliability and incident visibility cannot be withheld from Base.

## 4. Functional requirements

### Dashboard

- Scope every result to the authenticated shop.
- Exclude staging and test shops from merchant production totals.
- Display the metric definition and last refresh time.
- Preserve an incident after recovery in reliability history.
- Link every actionable problem to the narrowest corrective screen.
- Label GeoStock-owned problems without asking the merchant to repair them.

### Alerts

- Require repeated confirmation before alerting on transient failure.
- Deduplicate alerts for the same unresolved condition.
- Escalate by severity and duration.
- Send recovery notification when service returns.
- Provide one CTA only when the merchant owns an action.
- Simulate alerts without contacting a real merchant.

### Security and privacy

- Enforce tenant isolation at the query and API layers.
- Do not expose shopper identity, addresses or raw personal data.
- Use the billing entitlement source for plan access; analytics events do not prove payment.
- Record metric version so definitions can change without silently rewriting history.

## 5. Non-functional requirements

- Dashboard response target: to be set by engineering after source design.
- Data freshness target: unapproved until baseline measurement exists.
- Availability target: unapproved until baseline measurement exists.
- Accessible on desktop and mobile with keyboard-operable controls.
- Partial source failure must degrade honestly instead of displaying zero.

## 6. Success framework

### Launch gates

- Metrics reconcile within 5% of their authoritative source for three test shops.
- Seven consecutive days of production telemetry pass completeness checks.
- Zero cross-shop data exposure in security testing.
- All alert types can be simulated without external delivery.
- Empty, partial, incident and recovery states pass product/design review.

### Product success

Targets require baselines before approval.

| Outcome | Measure | Baseline |
| --- | --- | --- |
| Faster diagnosis | Median time from dashboard open to corrective CTA | Required |
| Better activation | Share of new merchants reaching verified healthy coverage | Required |
| Useful alerts | Share of merchant-owned alerts followed by corrective action | Required |
| Trust | Support contacts caused by unclear or false dashboard claims | Required |
| Retention | 60/90-day retention for eligible exposed vs comparable unexposed merchants | Required |

### Guardrails

- No financial claims without order-level attribution.
- No increase in merchant alerts caused by transient incidents.
- No hidden instrumentation failure represented as healthy or zero.
- No core reliability visibility gated behind Plus.

## 7. Dependencies

- Live webhook and subscription health telemetry.
- Processing and publish outcome records.
- Storefront verification or an explicitly labeled weaker substitute.
- Eligible location-product denominator.
- Authenticated shop scoping.
- Billing entitlement source.
- Alert delivery and suppression system.

## 8. Risks

| Risk | Response |
| --- | --- |
| Freshness presented as accuracy | Use “verified current” only when storefront verification exists; otherwise label freshness explicitly. |
| False alarms reduce trust | Require repeated checks, suppression and recovery messages. |
| Undefined denominator improves scores artificially | Version and publish eligibility rules in the measurement contract. |
| Dashboard becomes a feature grid | Preserve one status, one action and one operational workspace. |
| Plus weakens the core promise | Keep reliability and failures in Base. |
| Retention appears improved through selection bias | Use comparable cohorts and report limitations. |

## 9. Open decisions

1. What evidence qualifies as storefront verification?
2. What is the actual freshness distribution by shop, location and catalog size?
3. Which conditions can merchants fix without support?
4. Which alert channels already have consent and delivery infrastructure?
5. What eligibility rules define monitored locations and products?
