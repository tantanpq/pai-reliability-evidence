# Evidence-first recoverability taxonomy

## Verified result

A bounded candidate introduced a pure recoverability classifier for already-verified execution evidence.

The classifier distinguishes five outcomes:

- **Success**: a verified completed result with successful terminal evidence.
- **Terminal task failure**: a verified completed attempt that ended unsuccessfully; this is terminal for that attempt and does not itself create a retry.
- **Recoverable technical failure**: a technical failure with a verified rollback to a known-good state.
- **Ambiguous effect**: the submit boundary may have been crossed but trustworthy completion evidence is missing; the same effect identity must be reconciled before any replay.
- **Invalid evidence**: malformed, unknown, missing, or failed verification facts; fail closed and infer nothing.

## Verification

Independent QA completed with no blocker.

- Baseline source manifest: **174/174 tuples matched**.
- Baseline test suite: **159/159 passed**.
- Candidate bundle: **31 files**.
- Preserved source tuples: **17/17 matched**.
- Pinned dependency donors: **4/4 matched**.
- Full isolated candidate suite: **166/166 passed**.
- Focused taxonomy, binding, and portable-routing suites passed.

No live runtime, control surface, database, pointer, claim, scheduler, or authority mutation was performed by this verification.

## Claim boundary

This evidence supports a classification and verification pattern. It does not claim production activation, automatic recovery, universal correctness, or zero defects.
