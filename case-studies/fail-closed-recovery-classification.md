# Case study: classifying recovery without inventing retries

## Problem

Distributed execution failures are easy to flatten into one vague state such as “failed, try again.” That shortcut is dangerous when a request may already have crossed a submit boundary or when rollback is incomplete.

The engineering goal was narrower: classify verified evidence without introducing a new retry engine, scheduler, queue, claim path, or authority layer.

## Approach

The candidate used five bounded classes: successful terminal result, terminal task failure, rollback-proven technical failure, ambiguous submit effect, and invalid evidence.

Two rules carried most of the safety value:

1. **Ambiguity does not authorize replay.** When submit may have happened but trusted completion evidence is unavailable, the original effect identity must be reconciled first.
2. **Recovery requires rollback proof.** A technical failure is recoverable only when readback proves restoration to a known-good state.

Unknown or malformed evidence fails closed instead of being promoted into a success, failure, or retry decision.

## Verification

Independent QA reported no blocker. The baseline matched **174/174** source-manifest tuples and passed **159/159** tests. The isolated candidate preserved **17/17** source tuples, matched **4/4** pinned dependencies, and passed the full **166/166** test suite plus focused classification and routing checks.

The verification did not activate the candidate in a live runtime or mutate control, database, pointer, claim, scheduler, or authority state.

## Reusable lesson

Recovery logic becomes easier to audit when three concerns remain separate:

- evidence verification;
- outcome classification;
- policy-controlled action.

That separation prevents an apparently convenient classifier from quietly becoming another control plane.
