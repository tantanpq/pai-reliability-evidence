# Deterministic Recovery from Stale Task Ownership — Verified Evidence

## Scope

This public snapshot summarizes a bounded, independently verified candidate recovery contract. It uses sanitized descriptions only and exposes no private source, infrastructure, credentials, raw logs, operational identifiers, or internal fingerprints.

## Verified outcome

Independent QA passed a candidate-only change for recovering stale execution ownership from durable lifecycle evidence.

The accepted evidence included a bounded production-code delta, repeated focused root-seam tests, and the broader regression package. Focused recovery and clean-core checks passed 32/32 twice, and the full package suite passed 129/129.

The tested candidate established that:

- terminal lifecycle evidence is reconciled before stale ownership is mutated;
- only the exact matching nonterminal claim can be completed from a terminal handoff;
- a dead nonterminal owner is recovered deterministically and idempotently;
- recovery failures are contained instead of becoming unhandled resident-loop failures;
- unrelated health fallback behavior remains intact;
- prior non-pass history is preserved rather than rewritten into success.

## Reliability pattern

A safe stale-owner recovery path should follow one evidence-bound sequence:

```text
stale ownership
  -> durable terminal evidence
  -> exact claim identity match
  -> local reconciliation
  -> idempotent recovery
  -> broader regression verification
```

The disappearance of an owner is not evidence that work completed, and it is not permission to invent a successor attempt.

## Why it matters

Blind retry or completion from local ownership state can create duplicate work, false completion, replay ambiguity, or retry cascades. Reconciliation from durable terminal evidence turns recovery into a deterministic state transition instead of a timing guess.

## Claim boundary

This evidence supports the tested candidate semantics under deterministic tests and independent QA. It does **not** prove production activation, live resident recovery, universal exactly-once behavior, or full Program completion.

## Publication safety

No credentials, private paths, host identifiers, runtime endpoints, proprietary source, sensitive logs, internal hashes, or third-party copyrighted material are included.
