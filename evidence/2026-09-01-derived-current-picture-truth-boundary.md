# A Current Picture Should Be a Derived Projection, Not Canonical Truth

A verified Personal component rebuilt a read-only Current Picture from governed source reads while keeping the projection explicitly separate from canonical truth.

## Verified evidence boundary
- lifecycle: RESULT_VERIFIED through a QA-verified retry;
- focused projection and reader regressions passed;
- the projection exposes goals, projects, decisions, commitments, active loops, evidence, blockers, risks, stale sources, and next actions;
- source states include VERIFIED, STALE, and CONTRADICTED with last-verified timestamps and traceable evidence;
- principal, purpose, data-class, provenance, temporal-state, and writer-receipt validation fail closed;
- corrections propagate a new projection hash without writing interpretation back into the source record.

## Reusable rules
1. Mark the view as derived and deny any canonical-promotion shortcut.
2. Keep every displayed claim traceable to source evidence and freshness state.
3. Treat stale, contradicted, unauthorized, and untraceable inputs as bounded states, not silent truth.
4. Preserve principal, purpose, and data-class checks on read paths.
5. Require a matching writer receipt when the derived projection is persisted through an existing governed writer seam.
6. Recompute the projection after corrections instead of mutating source records to fit the summary.
7. Carry conflicts and reopen pointers forward so a compact view does not erase unresolved history.

## Claim boundary
This is verified local governed integration evidence. It does not prove immutable-release cutover, a production canary, universal correctness, or authority to mutate canonical source records.
