# Recover the Claim, Not the Fiction

## Situation

A resident worker can disappear after taking ownership of work. The tempting shortcut is to infer completion, retry immediately, or create a successor from incomplete local state. Each shortcut can manufacture a story the durable evidence never supported.

## Approach

A bounded candidate recovery change was reviewed independently. The recovery path was constrained to its owning seam and required durable terminal lifecycle evidence before stale ownership could be changed.

The tested sequence was:

1. resolve the exact task/claim identity;
2. read terminal lifecycle evidence;
3. reconcile only the matching nonterminal claim;
4. recover stale ownership deterministically;
5. repeat recovery and require a no-op/idempotent result;
6. contain recovery exceptions rather than crashing the resident loop;
7. preserve historical non-pass evidence;
8. rerun focused and broad regression tests.

## Proof

Focused recovery and clean-core checks passed 32/32 twice, and the broader package suite passed 129/129. Independent QA also verified that the production-code change stayed bounded to the intended owner seam.

The verification remained candidate-only. No production activation was inferred from green tests.

## Lesson

Recovery should reconcile reality, not manufacture progress. The safest recovery path is exact-identity-bound, deterministic, idempotent, and driven by durable lifecycle evidence.

This reduces four common failure modes:

- duplicate work after a restart;
- false completion from stale ownership;
- retry cascades caused by ambiguous recovery;
- resident-loop instability when recovery itself throws.

## Claim boundary

This case supports a bounded recovery design pattern under deterministic tests and independent QA. It does not establish production activation, universal distributed exactly-once semantics, or a general production-readiness claim.

## Public-safety note

The case is intentionally sanitized. It contains no private source, credentials, hostnames, internal paths, sensitive logs, operational IDs, private fingerprints, or third-party copyrighted material.
