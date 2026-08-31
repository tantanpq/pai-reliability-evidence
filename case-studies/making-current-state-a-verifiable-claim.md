# Making “Current State” a Verifiable Claim

## Situation

A distributed automation system can accumulate many plans, checkpoints, handoffs, cached projections, and runtime signals. The problem is not necessarily lack of information. It is allowing different workers to infer “current” from different evidence.

Common failure modes include:

- newest filename wins;
- chat history is treated as authority;
- a cached snapshot outlives the runtime state it described;
- missing source becomes an implicit default;
- two contradictory sources are silently reconciled by guesswork.

## Approach

A bounded resolver was treated as a **read-only projection**, not a new authority layer.

Its job was to:

1. pin a small declared set of authoritative durable sources;
2. validate their identity before interpretation;
3. resolve the durable context deterministically;
4. emit source provenance with the projection;
5. fail closed when required evidence was missing, malformed, mismatched, or contradictory;
6. leave volatile runtime facts to a separate just-in-time read from their owning layer.

## Verified result

The candidate reached terminal `DONE` under its bounded contract. Its acceptance fixtures, canonical-input projection, source identity checks, and machine-readable output parsing passed.

That result did not activate the resolver or prove current runtime health.

## Why this matters

The useful distinction is:

```text
“What durable source context should I use?”
```

versus:

```text
“What is true in the runtime right now?”
```

Trying to answer the second question from the first creates stale-state confidence. Refusing to guess turns “current” from a social convention into a reproducible evidence claim.

## Reusable lesson

```text
PIN SOURCES
→ VERIFY IDENTITY
→ APPLY DECLARED PRECEDENCE
→ EMIT PROVENANCE
→ FAIL CLOSED ON CONTRADICTION
→ FETCH VOLATILE TRUTH JIT
```

Interpretation may be automated. Authority must not be invented.

## Claim boundary

This public case study covers a generic deterministic source-resolution pattern. It does not expose private PAI continuity machinery, prove live activation, or establish current runtime health.
