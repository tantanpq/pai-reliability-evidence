# Compositional Successor Verification Checklist

Use this when a release candidate reuses previously reviewed components and introduces a small bounded delta.

## 1. Freeze the claim

- State exactly what is being verified: composition, candidate bytes, test receipts, activation, or live behavior.
- Do not let a release-candidate PASS silently become an activation or production claim.

## 2. Verify inherited evidence

- Identify the reviewed base and the prior evidence being reused.
- Confirm reused candidate components are byte-identical to the previously reviewed bytes.
- Reject inheritance when provenance or byte identity cannot be established.

## 3. Isolate the real delta

- Diff the remaining changed surface separately.
- Count and inspect nonblank changes.
- Confirm the change is bounded to the stated policy or behavior and does not smuggle in a new writer, queue, scheduler, authority, or claim path.

## 4. Re-run the bounded checks

- Execute the configured suite for the successor scope.
- Execute the exact regression or successor-specific checks.
- Record exit status and stderr rather than translating “process ran” into “tests passed.”

## 5. Reconcile terminal semantics

- Require exact scope and request-contract binding.
- Confirm terminal reconciliation is explicit.
- Preserve FAIL/BLOCKED evidence instead of overwriting it with a later candidate PASS.

## 6. State coverage gaps

- Record whether the independent reviewer actually received and re-executed the full successor tree.
- If not, say so prominently and bound the verdict to composition and captured receipts.

## 7. Keep activation separate

A candidate can be valid for release consideration while remaining deliberately unactivated. Treat activation as a separate governed decision and evidence chain.
