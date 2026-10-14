# Dashboard 2.0 user stories

## US-01 — Understand current health

**As a merchant, I want one clear availability status so that I know whether shoppers can rely on GeoStock now.**

Acceptance criteria:

- Given complete telemetry, when the dashboard opens, then it shows one current health statement, last verified time and primary action.
- Given incomplete telemetry, then it shows “Not enough data yet” or “Measurement unavailable,” never a false zero or healthy state.
- Given an active issue, then the statement names the affected scope and owner.

## US-02 — Fix the highest-priority merchant problem

**As a merchant, I want the most important problem first so that I know what to fix before reviewing details.**

Acceptance criteria:

- Problems are ordered by confirmed shopper exposure, duration and scope.
- The primary CTA opens the narrowest corrective view.
- GeoStock-owned incidents do not ask the merchant to repair infrastructure.

## US-03 — See coverage

**As a merchant, I want to see which locations and products are verified so that I understand the limits of the status.**

Acceptance criteria:

- Every coverage value includes numerator, denominator and eligibility definition.
- Excluded locations or products can be inspected.
- Eligibility changes are versioned and do not rewrite past results silently.

## US-04 — Understand reliability over time

**As a merchant, I want a short reliability history so that I can see whether a problem is isolated or recurring.**

Acceptance criteria:

- The chart shows the approved target, incidents and time below target.
- Recovered incidents remain visible in history.
- Partial-data periods are visually distinct from healthy periods.

## US-05 — Receive useful alerts

**As a merchant, I want alerts only when they are confirmed and meaningful so that I can act without alert fatigue.**

Acceptance criteria:

- A transient single failure does not send a merchant alert.
- Repeated alerts for one open incident are suppressed.
- Merchant-owned alerts have one CTA.
- GeoStock-owned incidents state that GeoStock is working on them.
- Recovery produces a closure message.

## US-06 — Troubleshoot with support

**As a support operator, I want technical verification details so that I can diagnose the delivery stage without making the merchant interpret infrastructure.**

Acceptance criteria:

- Diagnostics are collapsed by default.
- The view distinguishes receipt, processing, publishing and storefront verification.
- Failure stage and timestamps can be copied into an engineering issue.
- No cross-shop data is visible.

## US-07 — Understand plan access

**As a merchant, I want core reliability included in my plan so that I am not charged extra to learn whether GeoStock works.**

Acceptance criteria:

- Base shows current health, affected scope, core coverage and incident alerts.
- Plus gates only advanced history, customization, exports and analysis.
- Entitlement comes from the billing source.
