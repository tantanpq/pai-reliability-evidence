# When Passing Tests Are Still the Wrong Answer

## Situation

A verification capability already had a canonical owner. During reconciliation, a second implementation was produced because earlier source visibility was incomplete.

The duplicate implementation behaved correctly in its focused tests. That was not enough.

## Evidence

The duplicate passed focused functional checks and independent QA. The broader verification work also showed that deliberately broken policy variants were rejected and that the canonical verification path behaved consistently across the tested environments.

## Decision

The duplicate was rejected because it created a second policy owner. The system restored the canonical implementation and treated the duplicate as negative evidence rather than a new component.

The decisive failure was architectural duplication, not local functional correctness.

## Why this matters

A green test suite answers whether the tested behavior works. It does not answer whether the candidate is the correct component to own that behavior.

For governed automation, verification should therefore include:

- functional behavior;
- provenance;
- scope;
- ownership;
- authority isolation;
- rollback/readback.

This reduces forked policy, conflicting authority, and integration ambiguity that can otherwise emerge from two individually “correct” implementations.

## Limits

This case study supports a bounded assurance pattern only. It does not establish universal correctness, formal verification, arbitrary-system production readiness, or automatic promotion authority.
