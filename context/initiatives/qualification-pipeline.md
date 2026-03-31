# Initiative: Qualification Pipeline

## What it is

The pipeline that determines whether a caller qualifies for a given offer or service. It runs during a live call and feeds a decision to the AI agent in real time.

## Current status

V2 in active development. Core work: improving signal detection accuracy and reducing qualification latency.

## Key decisions

| Date | Decision |
|---|---|
| 2026-03 | Prescriptive and open-ended prompt variants going into A/B test |
| 2026-03 | SIGNAL INTERPRETATION as hard overrides is the correct architecture |

## Open questions

* Multi-device scenario handling (two phones, one qualifies)
* Household disambiguation (spouse on existing plan vs new caller)

## Links

* Jira epic: [add]
* Confluence: [add]
