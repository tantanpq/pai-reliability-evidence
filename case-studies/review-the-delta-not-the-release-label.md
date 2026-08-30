# Case Study: Review the Delta, Not the Release Label

## Problem

A successor candidate reused a previously reviewed base plus a small integration change. The tempting shortcut was to treat “successor” as a fresh object and either re-review everything blindly or, worse, trust the label and skip the changed surface.

## Approach

The review split the problem into inherited evidence and new delta:

1. verify the reviewed base and inherited security evidence;
2. prove reused delta files were byte-identical to the previously reviewed candidate;
3. isolate the remaining integration change and inspect its nonblank diff records;
4. run configured and successor-specific checks;
5. confirm no new authority, writer, queue, scheduler, or claim-path behavior appeared;
6. keep activation outside the verification claim.

## Evidence

The independent review reported a release-candidate PASS with no critical blockers. It preserved a passing cybersecurity receipt and **42 independent QA checks**, verified four reused delta files byte-for-byte, and bounded the remaining integration delta to **4 nonblank records**. Configured and exact successor test receipts both completed with exit code `0` and empty stderr.

## Result

The candidate was justified for release consideration without pretending the review proved more than it did.

## Limitation that mattered

The independent reviewer did not receive and re-execute the full successor tree. The verdict therefore remained a **composition and reviewed-evidence** verdict, not an end-to-end runtime or production certification.

## Reusable lesson

When most of a candidate is inherited, verify inheritance by bytes, inspect the actual delta separately, and publish the coverage gap beside the PASS. Release labels are metadata. Evidence is the part that gets to make claims.
