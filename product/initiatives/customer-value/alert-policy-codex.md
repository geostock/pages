# Dashboard 2.0 alert policy

**Status:** Draft. Trigger thresholds remain provisional until production baselines exist.

## Alert principles

1. Tell the merchant what shoppers may experience.
2. Name the owner of the recovery.
3. Give one CTA only when the merchant owns an action.
4. Suppress duplicates while the same incident remains open.
5. Notify recovery.
6. Never turn a transient signal into a merchant alarm after one check.

## Alert matrix

| Alert | Provisional trigger | Message | Owner | Channel | CTA | Recovery |
| --- | --- | --- | --- | --- | --- | --- |
| Inventory updates stale | Update path exceeds the approved freshness window across two checks | “Availability may be out of date at Downtown.” | GeoStock unless configuration caused it | In-app; email if sustained/high impact | `View affected products` | “Inventory updates are current again.” |
| Storefront mismatch | Published state and storefront verification disagree across two checks | “Some shoppers may see availability that does not match the latest verified stock.” | GeoStock or unknown during diagnosis | Internal immediately; merchant if confirmed | `View status` | “Storefront availability matches again.” |
| Connection lost | Enabled location stops receiving required updates | “South warehouse is not receiving stock updates. GeoStock is reconnecting it.” | GeoStock | In-app; email if sustained | No merchant CTA; `View status` only | “South warehouse is connected again.” |
| Setup incomplete | No eligible locations, inactive embed or unmatched imported locations after the onboarding grace period | “Finish setup before shoppers rely on location availability.” | Merchant | In-app and email | `Complete setup` | Remove alert after verification |
| Protection gap | Purchase protection configured for only part of the eligible scope | “Purchase protection is inactive at 2 eligible locations.” | Merchant | In-app; weekly email | `Enable protection` | “Purchase protection is active everywhere.” |
| Weekly value report | Shop has sufficient complete telemetry for the reporting window | “Your GeoStock reliability report is ready.” | GeoStock | Email and in-app | `View report` | Not applicable |

## Severity model

| Severity | Meaning | Merchant behavior |
| --- | --- | --- |
| Informational | No shopper impact; useful context | Dashboard only |
| Needs attention | Limited or configuration-owned risk | In-app; email after grace period |
| High impact | Confirmed broad shopper exposure | In-app and email; internal escalation |

## Suppression rules

- One open alert per shop, failure type and affected scope.
- Do not resend unless severity increases or the incident remains open past an approved reminder interval.
- Do not alert test or staging shops.
- Do not send merchant email until delivery is explicitly released after QA.
- If measurement fails, send an internal instrumentation alert; do not tell the merchant their store is unhealthy without product evidence.

## Threshold approval checklist

- Baseline distribution measured by catalog and location count.
- Expected update frequency understood for active and low-volume stores.
- False-positive rate reviewed.
- Incident and recovery windows approved together.
- Merchant channel consent confirmed.
