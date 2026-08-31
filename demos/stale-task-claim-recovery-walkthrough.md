# Synthetic Walkthrough: Recover a Stale Task Claim Without Inventing Progress

This walkthrough uses synthetic data only. Its purpose is to show the recovery invariant, not to reproduce any private runtime.

## Setup

Create four synthetic objects:

- task `T-17` recorded as owned by worker `W-old`;
- a durable terminal receipt for the exact claim `C-17`;
- an unrelated task `T-99` in a separate cone;
- a small recovery function that can reconcile ownership only when exact durable evidence matches.

## Walkthrough

### 1. Show stale ownership

`T-17` still says `W-old` owns the claim, but the worker is gone.

Unsafe conclusions would be:

- mark the task complete because the worker disappeared;
- retry immediately;
- create a successor attempt before checking durable evidence.

### 2. Read durable evidence first

The terminal receipt proves an outcome for claim `C-17`. The recovery function must match that exact identity before changing ownership.

### 3. Reconcile the exact claim

When the task and terminal receipt match, recovery clears stale ownership and reconciles the terminal state.

When the identity differs, recovery fails closed.

### 4. Prove idempotency

Run the same recovery a second time. The second run must produce no new effect.

### 5. Inject a recovery failure

Make the synthetic recovery function throw after evidence lookup. The failure should be recorded/contained rather than becoming an unhandled resident-loop crash.

### 6. Check cone isolation

`T-99` remains unchanged throughout the recovery of `T-17`.

## Expected observations

| Scenario | Expected result |
|---|---|
| Exact terminal evidence + stale matching claim | Reconcile locally |
| Mismatched claim identity | Reject |
| Missing terminal evidence | Reject / remain unknown |
| Same recovery repeated | No second effect |
| Recovery exception | Contained failure |
| Unrelated task | Unchanged |

## Core lesson

A vanished owner is not evidence of completion. Recover from durable lifecycle evidence, bind to exact identity, make the operation idempotent, and keep failure local.

## Boundary

This is a teaching fixture. Passing the walkthrough would not prove production activation, live failover, or universal exactly-once semantics.
