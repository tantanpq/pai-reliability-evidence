# Attempt Identity Continuity Across Restart — Verified Evidence

## Scope

This public snapshot summarizes a bounded, independently verified restart/replay contract. It uses sanitized descriptions only and exposes no private source, infrastructure, credentials, raw logs, or internal fingerprints.

## Verified outcome

Independent QA verified a candidate that preserves the authoritative execution-attempt identity across restart.

The accepted evidence included complete source-pin reread, focused owner tests, and inherited regression tests. The tested behavior established that:

- restart restores the exact persisted attempt identity into resumed ownership and completion;
- missing, legacy, or foreign attempt identities fail closed instead of being invented;
- same-attempt, same-result replay is idempotent;
- same-attempt, conflicting-result replay is rejected;
- one accepted terminal result cannot unlock the same downstream dependency twice.

## Reliability pattern

A restart-safe execution path should preserve one identity chain:

```text
claim
  -> ownership
  -> attempt
  -> restart/recovery
  -> completion
  -> replay handling
```

Recovery may restore execution, but it must not mint a new story about which attempt performed the work.

## Why it matters

Loose identity reconstruction after interruption can turn duplicate completion, false attribution, replay ambiguity, or double-unlock into something that looks successful. Persisting and verifying the exact attempt identity makes restart recovery evidence-bound rather than timing-bound.

## Claim boundary

This evidence supports candidate semantics under deterministic tests and independent QA. It does **not** prove production activation, live cutover, universal distributed exactly-once behavior, or full Program completion.

## Publication safety

No credentials, host identifiers, private paths, runtime endpoints, proprietary source, raw sensitive logs, or internal hashes are included. No third-party copyrighted material is reproduced.
