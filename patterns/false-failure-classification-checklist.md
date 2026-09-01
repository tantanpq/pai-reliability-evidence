# False-Failure Classification Checklist

Use this before converting an execution signal into a candidate verdict.

- [ ] Identify the exact failing boundary: candidate, QA invocation, transport, or lifecycle projection.
- [ ] Confirm whether candidate code actually executed.
- [ ] Pin the exact candidate bytes or immutable source identity.
- [ ] Preserve the original failure event and timestamp.
- [ ] Capture the exact failing command or transport event.
- [ ] Rule out candidate mutation before rerun.
- [ ] Rerun only the affected verification path with corrected invocation/transport.
- [ ] Keep acceptance assertions unchanged.
- [ ] Record rerun command, exit code, and deterministic test evidence.
- [ ] If candidate bytes changed, treat the rerun as a new candidate rather than a reclassification.
- [ ] If the original failure did not exercise the candidate, classify it at the invocation/transport boundary.
- [ ] If the candidate executed and an assertion failed, keep the candidate failure.
- [ ] Do not use a later PASS to erase failure history.
- [ ] Do not infer live activation, production readiness, or broader authority from an offline PASS.

Minimum receipt: original signal, boundary classification, candidate identity, mutation status, rerun evidence, and bounded final claim.
