# Pre-Activation Freeze Gate Checklist

Use this pattern when a candidate may be technically verified before a separate decision allows it to become active.

## Package verification

- [ ] Freeze the candidate before installation.
- [ ] Verify the exact bounded source manifest.
- [ ] Recompute and record the candidate tree fingerprint.
- [ ] Run the complete verification suite.
- [ ] Run focused checks for the bounded change set.
- [ ] Independently repeat verification from a read-only context.
- [ ] Confirm bounded deltas match the qualified change set.

## Runtime activation gate

- [ ] Keep `VERIFIED` distinct from `ACTIVATED`.
- [ ] Run a fresh runtime health check immediately before activation.
- [ ] Require zero protected active claims or running work before cutover.
- [ ] Drain the existing owner before changing the active pointer.
- [ ] Make the pointer update the final activation step.
- [ ] If any gate fails, keep the candidate frozen.

## Minimal receipt semantics

A useful receipt should separately record package identity, source/tree fingerprints, test totals, independent-QA status, frozen state, fresh-health result, active-work counts, drain completion, pointer-update ordering, whether activation was allowed, and whether activation was actually performed.

## Claim discipline

A green build is not proof that a package is installed. A verified package is not proof that runtime conditions permit activation. Activation permission is not proof that activation occurred. Keep those states separately auditable instead of letting one green checkbox impersonate four different facts.

This checklist adds no scheduler, queue, deployment owner, claim path, or control-plane authority. It is intended to bind to an existing governed release and activation path.
