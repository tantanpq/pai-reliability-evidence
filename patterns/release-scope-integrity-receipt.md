# Release-Scope Integrity Receipt

Use this pattern to verify that a release candidate changes **exactly the authorized scope**, not merely that its focused tests are green.

The verifier should remain read-only and must not gain activation, deployment, writer, or publication authority.

## Minimal receipt fields

```text
BASELINE_TREE_FINGERPRINT:
BASELINE_ENTRY_COUNT:
CANDIDATE_TREE_FINGERPRINT:
CANDIDATE_ENTRY_COUNT:
ADDED_SET_FINGERPRINT:
CHANGED_SET_FINGERPRINT:
REMOVED_SET_FINGERPRINT:
AUTHORIZED_DELTA_FINGERPRINT:
UNAUTHORIZED_ADDED_COUNT:
UNAUTHORIZED_CHANGED_COUNT:
UNAUTHORIZED_REMOVED_COUNT:
SOURCE_PIN_STATUS: MATCH | DRIFT | UNKNOWN
FOCUSED_TESTS_PASSED:
FOCUSED_TESTS_TOTAL:
MUTATION_DIFF_COUNT:
ACTIVATION_ALLOWED: true | false
OBSERVED_AT:
VERIFIER_IDENTITY:
UNSUPPORTED_CLAIMS:
```

## Acceptance checklist

### 1. Pin the baseline

- [ ] Baseline selection is exact and fingerprint-bound.
- [ ] The reason this baseline is authoritative for the comparison is recorded.
- [ ] Current source/pointer pins are checked so stale baseline drift is not confused with candidate scope failure.

### 2. Recompute the candidate

- [ ] Candidate tree identity is recomputed from actual entries/bytes rather than trusted from a release label or packaging narrative.
- [ ] Added, changed, and removed sets are computed completely.
- [ ] Read-only verification does not mutate the candidate or baseline.

### 3. Represent authority separately

- [ ] The authorized delta is independently represented.
- [ ] Every added candidate entry is covered by the authorized delta.
- [ ] Every changed candidate entry is covered by the authorized delta.
- [ ] Every removed candidate entry is covered by the authorized delta.
- [ ] Any uncovered delta fails closed.

### 4. Keep behavior tests separate

- [ ] Focused tests are rerun or otherwise independently verified where appropriate.
- [ ] Passing tests are recorded as behavior evidence, not release-scope authorization.
- [ ] A green test suite cannot override an uncovered tree delta.

### 5. Gate the effect

A minimal effect rule is:

```text
SOURCE_PIN_STATUS == MATCH
AND UNAUTHORIZED_ADDED_COUNT == 0
AND UNAUTHORIZED_CHANGED_COUNT == 0
AND UNAUTHORIZED_REMOVED_COUNT == 0
AND REQUIRED_TESTS_PASS
→ candidate may proceed to the next existing governed gate
```

Anything else remains blocked or explicitly unresolved. The receipt itself does not activate anything.

## Claim boundary

This receipt checks composition against an authorized change boundary. It does not prove the candidate is bug-free, secure, production-ready, or approved by every downstream release gate.
