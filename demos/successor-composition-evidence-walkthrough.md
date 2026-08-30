# Demo: Successor Composition Evidence Walkthrough

A short, synthetic walkthrough for explaining how to verify a mostly inherited release candidate without inflating the claim.

## Scenario

A candidate reuses a reviewed base, preserves several previously reviewed delta files, and changes one small policy guard.

## Walkthrough

| Step | Evidence to show | What it proves |
|---|---|---|
| 1 | Prior base security/QA receipt | The inherited base has bounded reviewed evidence |
| 2 | Byte-identity check for reused files | Those reused bytes did not silently drift |
| 3 | Small isolated diff for the remaining file | Review effort is concentrated on the actual change |
| 4 | Configured-suite exit `0`, empty stderr | The configured candidate checks completed cleanly |
| 5 | Exact successor test exit `0`, empty stderr | The successor-specific regression completed cleanly |
| 6 | Authority-surface review | No new writer, queue, scheduler, authority, or claim path appeared |
| 7 | Coverage statement | The audience can see what was not independently re-executed |

## Suggested narration

“Most of this candidate is inherited, so we do not confuse reuse with trust. We prove the reused bytes are unchanged, isolate the new delta, run the bounded checks, and separately inspect whether authority changed. The independent verdict supports release-candidate composition. It does not claim activation or full-tree end-to-end validation.”

## Failure examples

Stop or downgrade the verdict when any of these occur:

- inherited bytes differ from the reviewed candidate;
- provenance for the reused base cannot be established;
- the small diff introduces a new authority or control path;
- test receipts are missing, non-terminal, or ambiguous;
- the reviewer did not receive the full tree but the final claim says “fully independently re-tested.”

## Takeaway

A useful successor proof has three visible layers: **verified inheritance, inspected delta, explicit coverage boundary**.
