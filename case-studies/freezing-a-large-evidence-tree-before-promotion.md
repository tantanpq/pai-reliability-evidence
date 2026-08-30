# Freezing a Large Evidence Tree Before Promotion

## Situation

A candidate had already passed semantic review, but the next step depended on proving that the reviewed evidence was exactly the evidence being handed forward. Re-running a reviewer against a mutable tree would have made the result ambiguous.

## Approach

The candidate was frozen and described by an exact manifest. An independent reviewer used a separately transferred copy and recomputed path, byte-count, and file-digest evidence instead of trusting labels or prior summaries.

The reviewed tree contained 5,558 files and 194,318,686 bytes. Independent comparison found zero manifest mismatches. The reviewer also checked that the evidence digest was unchanged before and after QA and that no candidate or live mutation occurred during the review.

## Result

The freeze received an independent PASS. The result established two things that are easy to conflate:

1. the reviewed bytes were reproducible from an independent copy; and
2. the act of reviewing them did not change the candidate.

It did not establish physical activation or production readiness. The same frozen candidate still had to cross those later gates.

## Reusable lesson

Promotion should inherit evidence only when the promoted candidate is byte-identical to the independently reviewed freeze. If the bytes change, the old review belongs to the old candidate. Software labels are surprisingly talented at surviving changes that evidence should not.

## Public boundary

This case study is a sanitized derivative. It excludes private paths, identities, source code, raw logs, credentials, internal identifiers, and private source fingerprints.
