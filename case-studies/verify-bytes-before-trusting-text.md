# Verify the Bytes Before You Trust the Text

## Situation

A portable build path needed to move text-like source material across packaging and staging boundaries without allowing encoding quirks or silent transformations to change what had already been verified.

## Approach

The candidate pinned source bytes, used a strict decoding contract, made byte-order-mark handling explicit, retained fail-closed checks for unsupported content, and verified staged bytes against the bundle snapshot. Independent read-only QA reconstructed the baseline and added adversarial encoding cases rather than relying only on supplied tests.

## Evidence

- **11/11** immutable input-manifest entries independently verified, totaling **22,356 bytes**.
- Pinned baseline reconstructed byte-for-byte and fingerprint-matched.
- Ordinary UTF-8 and UTF-8-with-BOM round trips passed independent checks.
- Malformed UTF-8, UTF-16, embedded NUL, and sensitive-content fixtures were rejected.
- Exact staged file bytes and bundle verification were independently checked.
- Parent and QA both reached terminal successful states with no blocker.
- No live-runtime mutation was performed by QA.

## Value

The result closes a subtle assurance gap between “the intended source was selected” and “the staged artifact still contains the intended bytes.” That distinction matters whenever inputs cross operating systems, storage layers, decoders, or packaging boundaries.

## Boundary

This case study does not claim universal encoding safety, universal sensitive-content detection, formal verification, production readiness, or deployment eligibility.
