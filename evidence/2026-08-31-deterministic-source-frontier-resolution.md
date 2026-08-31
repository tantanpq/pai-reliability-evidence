# Deterministic Source/Frontier Resolution — Bounded Evidence

## Why this evidence matters

Automation becomes unreliable when different workers infer “current state” from filenames, stale snapshots, chat history, or implicit defaults.

A safer approach separates **durable source resolution** from **volatile runtime truth** and refuses to guess when required source identity cannot be verified.

## Verified result

A bounded candidate resolver reached terminal `DONE` with:

- all declared resolver acceptance fixtures passing;
- canonical input projection passing;
- source byte/hash validation passing for the pinned inputs;
- machine-readable artifact parsing passing;
- no blocker at the captured candidate checkpoint.

The candidate was a read-only projection over existing authoritative sources. It was **not** evidence that the resolver was active in the live control path.

## What was verified

Within the bounded candidate contract:

1. durable source identifiers can be pinned before interpretation;
2. source identity can be checked by hash/size/schema before semantic use;
3. Program/Phase/checkpoint-style projections can be deterministic for identical valid inputs;
4. missing, malformed, mismatched, or contradictory required inputs can fail closed instead of producing a guessed answer;
5. volatile runtime facts can remain explicitly outside the durable projection and require a just-in-time read;
6. read-only interpretation does not need a second planner, scheduler, queue, database, or authority chain.

## What this does not prove

This result does **not** establish:

- current runtime health;
- current host, claim, or capacity truth;
- live activation of the candidate;
- authority to mutate the selected Program/Phase;
- universal correctness outside the tested contract.

## Public provenance boundary

This public derivative uses only the reusable contract. It excludes private source IDs, hashes, internal paths, host details, runtime outputs, credentials, and PAI continuity internals.

The reusable rule is: **automate interpretation from pinned evidence; never automate authority by guessing what “current” means**.
