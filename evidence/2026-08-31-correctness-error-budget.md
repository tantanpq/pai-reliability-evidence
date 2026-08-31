# Correctness Error Budget — Verified Evidence

## Scope

This public snapshot summarizes a bounded, verified reliability-governance contract. It intentionally omits private source code, internal paths, task identifiers, host details, raw logs, credentials, and internal hashes.

## Verified outcome

The candidate contract and its advisory evaluator passed focused contract checks, the broader reliability regression, and a clean-room contract-copy verification.

The verified contract separates ordinary availability or latency misses from correctness failures that should consume a hard-zero budget. The tested hard-stop classes included:

- duplicate effects;
- lost result evidence;
- unauthorized effects;
- stale replay;
- false PASS;
- trace gaps;
- rollback without verification.

The evaluator remained advisory-only. It consumed supplied evidence and produced deterministic recommendations without creating runtime authority, a scheduler, queue, database, claim path, monitoring plane, or graph effect.

## Reliability pattern

A useful correctness budget should:

1. define measurable lifecycle or observation objectives rather than a vague `healthy` state;
2. enumerate correctness failures that cannot be normalized into ordinary error allowance;
3. require evidence verification followed by a fresh current-state read before resolution;
4. bound change rate per mutable scope so repair activity cannot become an endless patch loop;
5. require consecutive healthy evidence cycles before stability is claimed;
6. keep policy evaluation separate from effect authority.

## Claim boundary

This evidence supports only a bounded static-contract claim. It does **not** prove live enforcement, a completed sustained reliability window, production certification, or activation of any reliability-only operating mode.

## Publication safety

This document is a sanitized derivative of verified internal evidence. It contains no private implementation source, customer data, sensitive logs, real credentials, private infrastructure identifiers, or internal provenance fingerprints.
