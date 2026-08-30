# Fail-Closed ACL Scope Validation — Evidence Snapshot

## Scope

This public snapshot records a verified candidate-level repair that tightened filesystem ACL scope validation before any permission grant.

## Verified result

The candidate changed the authorization boundary so that only the intended state-directory shapes are accepted. Reserved or ambiguous state, key, and release path variants are rejected before any ACL grant is attempted.

Candidate-side verification reported:

- syntax checks: **3/3 passed**;
- unit/security checks: **4/4 passed**;
- negative-path coverage for reserved names, nested forbidden variants, lookalike state names, and ancestor-only scopes;
- isolated mocked apply/readback: **passed twice**, supporting bounded idempotent behavior.

The frozen candidate archive was re-hashed before publication and matched its pinned SHA-256.

An independent security-QA task subsequently reached **DONE / PASS** under an acceptance contract that required exact-hash source identity, frozen-byte identity, changed-file containment, path normalization/traversal checks, exact allowlisted state paths, forbidden key/release/state variants, fail-closed ordering, active-principal-only permission semantics, and no live mutation.

## Why it matters

ACL repair is easy to get superficially right while leaving broad path shapes or traversal-adjacent variants accidentally admissible. The useful pattern here is narrower:

1. define the exact allowed path shapes;
2. reject reserved and ambiguous variants first;
3. fail closed before granting anything;
4. freeze the candidate bytes;
5. run independent QA against the frozen artifact;
6. keep live activation outside the verification step.

## Claim boundary

This is **candidate verification evidence**, not proof of physical startup validation, live deployment, security certification, or production-wide correctness.

## Publication safety

This summary excludes private source code, internal filesystem paths, host identifiers, credentials, raw logs, private release identifiers, and proprietary implementation details. No third-party copyrighted material is included. No repository-wide license is granted by this file.
