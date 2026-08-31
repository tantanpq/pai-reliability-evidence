# When “No Errors” Is Not a Reliability Metric

## Situation

A reliability layer needed to distinguish ordinary service misses from correctness failures that should never be absorbed into a normal availability budget.

A system can remain responsive while still doing something unacceptable: duplicating an effect, losing terminal evidence, replaying stale work, reporting a false PASS, or claiming rollback without proving restoration.

## Approach

The bounded contract treated reliability as an evidence problem rather than a process-presence problem:

1. define measurable lifecycle and observation objectives;
2. separate ordinary availability/latency misses from hard-zero correctness events;
3. make correctness violations exhaust their budget immediately;
4. require evidence verification before a fresh current-state reread;
5. require that reread before `RESOLVED`;
6. bound change rate per mutable scope;
7. require consecutive healthy evidence cycles before declaring stability;
8. keep the evaluator advisory and leave enforcement with the existing governed authority owner.

## Verification

The candidate passed focused contract checks, the broader reliability regression, and a clean-room contract-copy verification. A mechanism review also confirmed that the evaluator produced recommendations without creating a scheduler, queue, database, claim path, writer, monitoring plane, or runtime authority.

## Why this matters

Availability answers whether a service responded. A correctness budget asks whether the response can still be trusted.

That distinction matters most in automation systems, where a responsive process can still duplicate an external action, lose evidence, or silently replay stale state.

## Limits

This case study does not claim live policy enforcement, production certification, or a completed sustained reliability window. It describes a verified static contract pattern and uses only sanitized public-safe language.
