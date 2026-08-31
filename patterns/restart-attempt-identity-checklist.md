# Restart Attempt Identity Checklist

Use this checklist when work can survive worker or process restart and terminal completion must still be attributable to the exact original execution attempt.

## Before interruption

- [ ] Ownership persists task identity, claim identity, attempt identity, work reference, and expected result identity.
- [ ] The attempt identifier originates from the authoritative execution path, not local reconstruction.
- [ ] Ownership is durable before recovery can resume work.
- [ ] Existing lease/fence semantics remain explicit where applicable.

## Recovery

- [ ] Recovery loads the exact persisted attempt identifier.
- [ ] A missing legacy attempt identifier fails closed.
- [ ] A foreign or mismatched attempt identifier cannot complete the work.
- [ ] Recovery does not invent a replacement claim, attempt, or completion identity.
- [ ] Restart does not weaken owner, lease, or fence validation.

## Completion and replay

- [ ] Completion is bound to the persisted attempt.
- [ ] Same-attempt, same-result replay is idempotent.
- [ ] Same-attempt, conflicting-result replay is rejected as a conflict.
- [ ] One accepted terminal result unlocks downstream work at most once.
- [ ] Result identity or hash checks remain active after restart.

## Verification

- [ ] Pinned source/evidence is re-read before independent QA.
- [ ] Focused restart tests pass.
- [ ] Inherited regression tests pass.
- [ ] Candidate acceptance is not reported as live activation.
- [ ] Rollback preserves the previously accepted generation and ownership history.

## Acceptance sentence

> Restart restores execution without reconstructing execution identity, and replay cannot turn one attempt into two successful completions.
