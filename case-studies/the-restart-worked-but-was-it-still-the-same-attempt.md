# The Restart Worked, but Was It Still the Same Attempt?

## Situation

A distributed workflow could recover after interruption, but recovery safety depended on more than seeing the worker run again. Completion still had to belong to the exact execution attempt that owned the work before restart.

If recovery invents or loosely reconstructs identity, duplicate completion, false attribution, replay ambiguity, or downstream double-unlock can look like normal success.

## Approach

The bounded candidate treated attempt identity as durable evidence:

1. persist the authoritative attempt identifier with ownership;
2. restore that exact identifier after restart;
3. bind completion to the persisted attempt;
4. fail closed on missing, legacy, foreign, or mismatched identities;
5. make identical replay idempotent;
6. reject conflicting result content for the same attempt;
7. verify that one accepted terminal result can unlock downstream work at most once;
8. preserve existing lease, fence, and result-identity checks.

## Verification

Independent QA re-read the pinned evidence and passed the focused owner suite plus inherited regression coverage. The candidate preserved attempt identity across restart, accepted exact replay idempotently, and rejected the tested conflicting or invalid identity paths.

## Decision

Treat execution-attempt identity as persistent recovery evidence, not reconstructable metadata.

## Limits

This is candidate engineering proof only. It does not claim production activation, universal exactly-once semantics, or full distributed-system completion guarantees.
