# Self-Supply and Quiescence Verification Checklist

Use this before claiming that a task graph, workflow engine, or autonomous loop can supply its own known work and stop truthfully.

- [ ] Freeze the declared program/completion envelope and its source identity.
- [ ] Enumerate every currently known eligible work item before considering worker capacity.
- [ ] Confirm the compiled supply set does not shrink merely because fewer workers or lanes are available.
- [ ] Replay the same frozen frontier and verify deterministic materialization.
- [ ] Keep durable Task identity separate from per-execution Attempt identity.
- [ ] Require a fresh monotonic fence or equivalent ownership token for each new attempt.
- [ ] Reject stale ownership and stale attempt results.
- [ ] Define exactly which terminal states may release dependencies.
- [ ] Verify `NOT_DONE` or `BLOCKED` isolates only the dependent cone it actually blocks.
- [ ] Replay a duplicate terminal result and verify zero rematerialization and zero duplicate wake/effect.
- [ ] Verify one task reaching `DONE` cannot promote the whole program to complete.
- [ ] Recompute newly eligible work after every accepted terminal result.
- [ ] Declare program completion only when no known eligible/materializable work remains under the frozen envelope.
- [ ] Keep compile/planning logic free of hidden filesystem, network, process, database, claim, or scheduler effects when it is meant to be pure.
- [ ] Record exact tests, hashes, mutation status, and bounded final claim.

Minimum receipt: envelope identity, compiled frontier, deterministic replay evidence, Task/Attempt identities, stale-fence test, duplicate-result test, dependency-release evidence, and exact quiescence verdict.
