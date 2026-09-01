# Case Study Draft: Why Self-Certification Is Not Proof

## Problem
A candidate can pass its own checks and still lack independent evidence that the result applies to the intended release, environment, scope, or current counterevidence. A permanent green badge is especially misleading after the runtime changes.

## Approach
The verified component separated candidate production from independent certification. The evaluator bound each certification to exact version, environment, scope, expiry, rollback, fixtures, and counterevidence while retaining no mutation authority over the candidate or runtime.

## Verified result
- RESULT_VERIFIED / LIVE_PROVEN_COMPONENT;
- 5/5 focused tests passed;
- 64 bounded candidates were certified in the verified fixture;
- self-certification was rejected;
- missing rollback or required fixture evidence was rejected;
- expired, stale-release, environment, scope, and counterevidence mismatches were inactive.

## Why it matters
The pattern prevents a historical PASS from being reused outside the evidence envelope that made it true. It also preserves separation of duties: certification can qualify knowledge without becoming repair or deployment authority.

## Evidence ceiling
This result does not prove permanent correctness, production readiness, or authorization to execute repairs. Material runtime change requires reevaluation.
