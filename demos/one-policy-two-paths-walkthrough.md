# One Policy, Two Paths — Synthetic Walkthrough

This demo uses invented routes, identities, receipts, and runtime values. It demonstrates why a safety policy must be verified across every reachable path to the protected effect.

## Policy

A synthetic worker may submit work only after this invariant is proven:

```text
REFRESH CURRENT AUTHORITY
→ VERIFY RECEIPT
→ RE-READ SIGNED HEALTHY STATE
→ SUBMIT
```

## Route A — ordinary path

Route A follows the invariant correctly:

```text
state: STALE
refresh: PASS
receipt: VERIFIED
post_state: HEALTHY + SIGNED
submit_allowed: true
```

Its tests pass.

## Route B — marked path

A second reachable route uses a shortcut:

```text
state: DEGRADED
fence_metadata: MATCH
refresh: NOT PERFORMED
receipt: NOT VERIFIED
post_state: NOT PROVEN HEALTHY
submit_allowed: true   # bug
```

The route reaches the same protected effect but enforces a weaker predicate.

## Falsifier

Construct the negative test directly from the invariant:

```text
INPUT:
  degraded authority state
  matching metadata
  no verified refresh receipt

EXPECTED:
  submit_allowed = false

ACTUAL:
  submit_allowed = true
```

The falsifier exposes route-parity failure even though Route A and the broad common-path suite are green.

## Repair shape

Do not invent another policy service. Refactor both routes to call the same governed verifier:

```text
Route A ─┐
         ├─> ONE POLICY OWNER / VERIFIER ─> protected effect
Route B ─┘
```

Re-run positive and negative tests for both routes. A degraded state must remain blocked until the declared freshness evidence is proven.

## Useful rule

```text
ONE POLICY TEXT IS NOT ENOUGH.
EVERY REACHABLE PATH TO THE EFFECT MUST PROVE THE SAME INVARIANT.
```

## Claim boundary

This synthetic walkthrough is defensive and educational. It does not expose a real production route, grant authority, or establish universal authorization safety.
