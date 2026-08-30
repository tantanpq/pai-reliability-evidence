# Immutable Evidence Freeze QA Checklist

Use this when a candidate has already passed semantic review and must be frozen before promotion or physical validation.

## 1. Freeze the evidence set

- Define the exact candidate tree under review.
- Generate a manifest containing path, byte count, and cryptographic digest for every file.
- Record the aggregate file count and byte count.
- Do not rebuild or normalize the candidate after the freeze.

## 2. Verify from an independent copy

- Transfer or obtain a separately read reference copy.
- Recompute every file digest independently.
- Require exact agreement on path, size, and digest.
- Fail closed on missing, extra, unreadable, or changed files.

## 3. Prove the verifier did not change the target

- Capture a pre-QA digest of the frozen evidence.
- Run QA read-only.
- Capture a post-QA digest.
- Require exact equality.
- Record zero candidate and live mutations as an explicit assertion.

## 4. Preserve claim boundaries

A successful freeze QA means the evidence bytes are stable and independently reproducible. It does not mean the candidate is activated, promoted, or production-ready.

## 5. Promotion handoff

Only after the freeze passes should the same frozen candidate advance to the next physical or promotion gate. If the bytes change, invalidate the freeze and verify the new candidate rather than inheriting the old result.
