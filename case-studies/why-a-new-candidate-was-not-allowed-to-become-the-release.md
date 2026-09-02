# Why a New Candidate Was Not Allowed to Become the Release

## The situation

A new software candidate looked healthy at first glance. It built successfully, had inventory data, and did not present an obvious catastrophic defect.

That was not enough to make it the release.

The admission boundary required independent evidence for candidate identity, trusted source provenance, signer policy, repository pinning, and vulnerability reachability.

## What the gate found

The candidate was evaluated against fail-closed supply-chain checks.

A promotion would be blocked if any admission-critical fact failed, including:

- the candidate was unsigned when a signature was required;
- its signer was outside the trusted signer policy;
- signed provenance did not match the candidate;
- repository, branch, or commit identity differed from the trusted source record;
- no trusted repository source could be established;
- a HIGH or CRITICAL vulnerability had a reachable runtime path.

A high-severity finding that was demonstrably unreachable remained visible as a watch condition. It was not erased, but it also was not inflated into a blocking claim without the reachability evidence required by the bounded policy.

## Why the decision mattered

A successful build answers a build question. It does not answer an origin question.

A scanner finding answers a vulnerability question. It does not automatically answer whether that vulnerability is reachable in this candidate.

A signature answers a cryptographic question. It does not automatically prove that the signer is trusted for the expected source.

The admission gate kept those questions separate. That prevented a candidate from becoming a release merely because several individually reassuring facts were present.

## What happened next

The gate itself did not repair the candidate.

It did not:

- update a dependency;
- rewrite provenance;
- switch signers;
- modify source;
- deploy software;
- grant release authority.

A blocked candidate instead required a separately governed correction, producing a new or properly re-qualified candidate with fresh evidence.

## Reusable lesson

Treat release admission as an evidence conjunction, not a confidence score.

A useful mental model is:

`immutable identity AND trusted provenance AND signer policy AND trusted source pin AND bound inventory AND vulnerability policy`

If a required term is false or materially unknown, stop at the admission boundary.

## Evidence basis and claim boundary

This case study is a synthetic public abstraction derived from a verified bounded supply-chain admission component whose focused verification passed **7/7 tests**.

It demonstrates the decision pattern. It is not a report of a customer incident, not a production-security certification, and not proof that every software supply-chain risk has been covered.
