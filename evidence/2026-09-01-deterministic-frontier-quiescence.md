# Deterministic Frontier Compilation and Exact Quiescence

A verified candidate showed that work supply, execution attempts, and program completion can be represented as separate deterministic claims instead of one overloaded queue state.

## Bounded verified result

- Candidate tests: 6 pass, 0 fail.
- Reference self-tests: 9 pass.
- Frozen input hashes and byte counts matched before and after verification.
- No live, task-store, claim, network, process, database, or production mutation was performed by the candidate module.

## Reusable rules

1. **Supply horizon is not capacity.** Compile every known eligible work item; worker or lane count is a separate runtime concern.
2. **Frontier compilation must be deterministic.** Replaying the same frozen frontier should produce the same materialization plan.
3. **Task identity survives retries.** A transport or attempt failure may create a new fenced attempt without inventing a successor task.
4. **Terminal states have bounded effects.** `DONE` may release compatible dependencies; `NOT_DONE` and `BLOCKED` remain local to their dependent cone.
5. **Duplicate results are inert.** Replay must not rematerialize work or produce a second wake/effect.
6. **Task done is not program done.** Program completion requires exact quiescence: no remaining known eligible or materializable work under the declared completion envelope.

## Claim boundary

This is candidate-only verification evidence. It does not prove a live scheduler, multi-host execution, production activation, product readiness, or an autonomous control plane.
