# Software DR Acceptance Checklist

Use this pattern to test software-side recoverability without overstating storage or physical-media guarantees.

## Backup contract

- [ ] Explicitly allowlist ordinary recoverable inputs.
- [ ] Exclude secrets from distributable backup artifacts.
- [ ] Build deterministic full and incremental manifests for the tested scope.
- [ ] Reject path traversal before publication.
- [ ] Fail closed when required ordinary inputs are missing.

## Restore proof

- [ ] Restore into an isolated temporary target rather than live state.
- [ ] Compare restored files byte-for-byte with accepted source bytes.
- [ ] Fail restore if a required backup object is missing.
- [ ] Fail restore if a backup object is corrupt.
- [ ] Rehash supplied input/readback artifacts against the verification manifest.

## Sealed secondary copy

- [ ] Bind sealed content to content identity at the software layer.
- [ ] Permit identical reuse without changing sealed-content semantics.
- [ ] Reject mutation of sealed content.

## Claim boundary

- [ ] Report software DR acceptance separately from offline-media assurance.
- [ ] Do not claim WORM or physical immutability without dedicated evidence.
- [ ] State activation status explicitly.
- [ ] Retain detailed provenance privately.

A successful backup job is not a recovery proof. A byte-exact restore contract is useful evidence, but it still does not turn ordinary software storage into offline or physically immutable recovery media.

This checklist creates no backup authority, scheduler, database, queue, or control plane.
