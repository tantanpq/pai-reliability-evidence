# When a Pointer Exists but Still Isn't Trustworthy

## Situation

A distributed system relied on durable source pointers. The pointer could still resolve successfully even when the referenced bytes had changed or the source no longer preserved the meaning expected by its consumers.

That creates a dangerous shortcut:

> “The pointer resolves, therefore the source is trustworthy.”

Those are different claims.

## Approach

A bounded source-binding candidate separated:

1. **semantic role** — what the source is supposed to mean;
2. **physical pin** — which durable source is referenced;
3. **immutable identity** — the bytes/fingerprint expected from that source;
4. **lifecycle state** — whether a candidate binding is merely staged or actually activated.

The candidate verified immutable inputs, surfaced pin drift, preserved the semantic reference explicitly, and failed closed when the observed source did not match the expected identity.

A small candidate change remained deliberately **not activated** until an existing authorized owner could perform the separate activation step.

## Verified result

Under its bounded candidate contract, source fingerprint checks, drift/reference-preservation checks, mismatch fail-closed behavior, and immutable-input verification passed. The candidate remained not activated.

## Why this matters

Three states are easy to collapse into one when humans are in a hurry, which history suggests is most of the time:

```text
REFERENCE EXISTS
STAGED CANDIDATE EXISTS
ACTIVE BINDING IS VERIFIED
```

Only the last one supports a claim about active behavior, and even then it should be backed by post-activation readback.

## Reusable lesson

```text
PIN DURABLE ID
→ VERIFY EXPECTED IDENTITY
→ PRESERVE SEMANTIC ROLE
→ SURFACE DRIFT
→ FAIL CLOSED ON MISMATCH
→ KEEP STAGED ≠ ACTIVATED
→ RE-READ AFTER AUTHORIZED ACTIVATION
```

## Claim boundary

This case study demonstrates bounded source-binding integrity and staged-versus-active discipline. It does not prove universal supply-chain integrity, live activation of any private candidate, or authority to rewrite canonical sources.

The public version excludes private IDs, source fingerprints, paths, code, runtime details, and internal implementation information.
