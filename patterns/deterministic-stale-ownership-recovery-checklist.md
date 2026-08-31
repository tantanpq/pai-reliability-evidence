# Deterministic Stale-Ownership Recovery Checklist

Use this checklist when a long-running worker, agent, or process disappears while still recorded as the owner of work.

## Before recovery

- [ ] Resolve the exact task/claim identity.
- [ ] Read durable lifecycle evidence before mutating ownership.
- [ ] Verify that the recorded owner is actually stale/dead according to the accepted source of truth.
- [ ] Keep recovery local; do not globally block unrelated work.
- [ ] Preserve prior failure and non-pass evidence.

## Recovery invariant

- [ ] Reconcile terminal evidence before creating any new mutation or successor.
- [ ] Complete only the exact matching nonterminal claim.
- [ ] Treat owner disappearance as insufficient evidence of completion.
- [ ] Make repeated recovery idempotent.
- [ ] Do not mint a new execution identity merely to make recovery convenient.
- [ ] Contain recovery exceptions so one failed reconciliation does not destabilize the resident loop.

## Verification

- [ ] Focused recovery tests exercise stale owner, exact match, mismatch, repeat recovery, and failure containment.
- [ ] A broader regression suite still passes.
- [ ] The production delta is bounded to the intended owner seam.
- [ ] Unrelated dependencies are unchanged or independently pinned.
- [ ] Historical non-pass evidence remains visible after recovery.
- [ ] Candidate QA PASS is not upgraded to LIVE without a separate activation/readback gate.

## Fail closed when

- terminal evidence is missing or ambiguous;
- the claim identity does not match exactly;
- ownership liveness cannot be established from an accepted source;
- a repeat recovery would create a second effect;
- recovery requires silently rewriting historical evidence.

Recovery is a reconciliation operation, not a license to invent progress.
