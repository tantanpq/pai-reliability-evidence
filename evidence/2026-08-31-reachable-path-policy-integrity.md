# Reachable-Path Policy Integrity — Bounded Evidence

## Why this evidence matters

A safety or authority policy can be implemented correctly on the ordinary path while a less-common but still reachable path uses weaker admission logic.

Broad test success on the common path does not prove policy closure across every route that can reach the protected effect.

## Verified result

In one bounded independent QA:

- candidate integrity recomputation passed;
- targeted and broad copied test suites passed;
- the ordinary route enforced the intended freshness sequence before permitting the protected action;
- route-level tracing identified another reachable path to the same effect;
- a negative falsifier showed that this alternate path could admit a degraded/stale authority state under a weaker predicate;
- the candidate also carried duplicated signer-capable refresh construction instead of proving one accountable owner for the signing/freshness boundary;
- QA therefore **rejected the candidate as a downstream dependency**;
- QA performed no live mutation.

## What was verified

The bounded result supports these statements:

1. policy correctness on one route is evidence for that route, not automatically for every reachable route;
2. route-level falsifiers can expose weaker special-path predicates that broad suites miss;
3. all paths to a protected effect should enforce the same invariant or fail closed;
4. signer/freshness construction should remain bound to one accountable owner rather than being reimplemented across paths;
5. successful common-path tests cannot override a demonstrated route-parity failure.

## What this does not prove

This result does **not** establish:

- a production exploit;
- universal authorization safety;
- formal verification;
- production readiness;
- automatic deployment or publication authority.

## Public provenance boundary

The public derivative excludes private route names, internal paths, hashes, hosts, identifiers, keys, receipts, source code, raw logs, and protected implementation details.

The reusable lesson is: **name the invariant once, enumerate every reachable path to the effect, and prove equivalent enforcement with positive tests and negative falsifiers**.
