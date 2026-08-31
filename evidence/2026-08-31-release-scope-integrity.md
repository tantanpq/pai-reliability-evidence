# Release-Scope Integrity — Bounded Evidence

## Why this evidence matters

A passing test suite answers whether the tested behavior passed. It does **not** prove that the complete release contains only the changes that were authorized.

This evidence records a bounded independent-QA result where a candidate passed its focused tests and current source pins were consistent, yet the candidate was correctly rejected because its complete tree contained material omissions outside the qualified change set.

## Verified result

At the captured QA checkpoint:

- the exact selected baseline and candidate trees were independently reconstructed and compared;
- the intended change boundary was narrow and separately represented;
- the focused test suite passed completely;
- current source-selection pins matched the recorded receipts, reducing the chance that stale baseline drift explained the discrepancy;
- complete-tree comparison found material omissions outside the authorized delta;
- the candidate was therefore **rejected for governed activation**;
- QA performed no activation or live mutation.

## What was verified

The bounded result supports these statements:

1. focused test success and release-scope integrity are distinct evidence classes;
2. a complete baseline/candidate set comparison can detect unauthorized additions, changes, or removals that focused behavior tests may miss;
3. authorized change scope should be represented independently from the candidate packaging narrative;
4. source-pin freshness helps distinguish candidate-scope failure from baseline-selection drift;
5. an uncovered release delta should fail closed before activation.

## What this does not prove

This result does **not** establish:

- universal supply-chain security;
- formal verification;
- production readiness;
- the operational significance of every omitted file;
- automatic deployment, activation, or publication authority.

## Public provenance boundary

The public derivative intentionally omits private paths, internal tree fingerprints, private file counts, host details, source code, raw logs, credentials, and protected implementation information.

The reusable lesson is simple: **green tests do not expand change authority**.
