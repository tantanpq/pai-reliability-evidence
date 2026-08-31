# Green Tests, Wrong Release — Synthetic Walkthrough

This walkthrough uses invented paths, names, hashes, and counts. It demonstrates why passing tests are not enough to prove release-scope integrity.

## Scenario

Assume an approved patch is allowed to change exactly two files:

```text
AUTHORIZED DELTA
- config/claim-policy.json
- src/claim-validator.py
```

A candidate is built and its focused tests all pass.

So far, we have behavior evidence. We do **not** yet have proof that the package changed only those two files.

## Step 1 — Pin a synthetic baseline

```text
baseline/
  config/claim-policy.json
  src/claim-validator.py
  src/worker.py
  src/recovery.py
  docs/operator-notes.md
```

Compute and record a tree fingerprint from the actual entries.

## Step 2 — Recompute the candidate tree

```text
candidate/
  config/claim-policy.json    # authorized change
  src/claim-validator.py      # authorized change
  src/worker.py
```

The candidate is missing two unrelated baseline files.

## Step 3 — Compute the complete delta

```text
ADDED:   none
CHANGED:
  config/claim-policy.json
  src/claim-validator.py
REMOVED:
  src/recovery.py
  docs/operator-notes.md
```

The behavior tests may still pass if they never exercise the missing material.

## Step 4 — Compare with authorization

```text
AUTHORIZED CHANGED:
  config/claim-policy.json
  src/claim-validator.py

UNAUTHORIZED REMOVED:
  src/recovery.py
  docs/operator-notes.md
```

The candidate exceeds its authorized release scope.

## Step 5 — Fail closed

```text
focused_tests: PASS
source_pin_status: MATCH
unauthorized_removed_count: 2
activation_allowed: false
```

Do not let `focused_tests: PASS` overwrite the composition failure.

## Step 6 — Rebuild from the exact baseline

Start from the pinned baseline again, apply only the two authorized edits, recompute the full tree, and rerun the required tests.

A clean scope receipt now has zero unauthorized added/changed/removed entries. That means the candidate may proceed to the **next existing governed gate**. It still does not mean “production ready.” Humanity has invented enough ways to turn one green light into twelve imaginary approvals already.

## Useful rule

```text
GREEN TESTS DO NOT EXPAND CHANGE AUTHORITY.
VERIFY THE COMPLETE RELEASE DELTA AGAINST THE AUTHORIZED DELTA.
```

## Claim boundary

This synthetic demo is educational. It does not provide deployment authority, certify a supply chain, or replace downstream security, reliability, or production-readiness checks.
