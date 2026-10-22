# Dashboard 2.0 merchant validation

**Owner:** Product  
**Status:** Ready to run  
**Participants:** 3 existing multi-location GeoStock merchants  
**Session length:** 25 minutes each

## Decision to make

Does the reliability-first dashboard help merchants understand GeoStock's value and take the correct next action?

## What we need to learn

1. Can a merchant explain the current status without help?
2. Can they find the highest-priority problem and correct owner?
3. Does the dashboard increase trust in GeoStock's continuing value?
4. Which alert would be useful enough to act on?
5. What important question remains unanswered?

## Participant mix

- One merchant with a recent sync or freshness problem.
- One merchant with several active locations.
- One merchant with no recent reported incident.

Use existing customers. Do not recruit only friendly or highly engaged merchants.

## Session script

### 1. Current behavior — 5 minutes

- How do you check whether GeoStock is working today?
- What usually tells you something is wrong?
- What happens next, and who handles it?

### 2. First-look test — 5 minutes

Show the mockup without explanation. Ask:

- What is this page telling you?
- Is anything wrong right now?
- What would you do next?
- Who do you think owns the problem?

### 3. Value and trust — 8 minutes

- Which part is useful? Which part is noise?
- Would this page give you a reason to keep paying for GeoStock? Why?
- What proof would you need before trusting the status?
- Which one alert would you want GeoStock to send?
- Which alert would annoy you?

### 4. Priority test — 4 minutes

Ask the merchant to rank:

1. Current availability health.
2. Products or locations affected.
3. Reliability history.
4. Recovery alerts.
5. Advanced reports and exports.

### 5. Close — 3 minutes

- What is missing?
- What would make this page worth opening every week?
- May we follow up after a real availability incident?

Do not pitch features or explain the intended answer during the test.

## Scorecard

Record observed behavior before opinions.

| Test | Pass rule | Merchant 1 | Merchant 2 | Merchant 3 |
| --- | --- | --- | --- | --- |
| Understands status | Correctly explains health without help |  |  |  |
| Finds next action | Selects intended action in under 60 seconds |  |  |  |
| Identifies owner | Correctly says merchant or GeoStock |  |  |  |
| Sees ongoing value | Gives a concrete reason this supports renewal |  |  |  |
| Wants an alert | Chooses at least one useful trigger |  |  |  |
| Trusts the proof | Names no unresolved proof blocker |  |  |  |

For every failure, capture the merchant's exact words and the screen element involved.

## Decision rule

**Proceed to product build:** at least 2 of 3 merchants pass status, action and owner tests; at least 2 give a concrete renewal-value reason; no repeated trust blocker appears.

**Revise and retest:** the reliability problem is relevant, but copy, hierarchy or evidence causes repeated confusion.

**Stop or reposition:** fewer than 2 merchants recognize the problem or connect the dashboard to ongoing value.

Three interviews provide directional evidence, not market proof. Use them to decide the next product iteration, not to publish broad customer or revenue claims.

## Output

Product records one page after all sessions:

- Result: proceed, revise or stop.
- Pass count for each test.
- Repeated merchant language.
- Required product changes.
- New evidence, assumptions and unknowns for the evidence register.
