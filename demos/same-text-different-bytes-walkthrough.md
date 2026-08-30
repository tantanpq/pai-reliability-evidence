# Same Text, Different Bytes

A short synthetic walkthrough for showing why rendered text is not enough evidence of byte fidelity.

## Scene 1 — Similar appearance

Show two synthetic files that appear similar when rendered but differ at the byte level.

## Scene 2 — Permissive decoding

Demonstrate conceptually how permissive decoding can hide malformed input or replacement behavior. Do not execute untrusted content.

## Scene 3 — Strict contract

Apply a strict decoding rule and show malformed input being rejected instead of silently normalized.

## Scene 4 — Explicit BOM policy

Use a synthetic UTF-8-with-BOM fixture and show the declared byte-order-mark rule passing a round-trip check.

## Scene 5 — Unsupported cases fail closed

Use synthetic UTF-16 and embedded-NUL fixtures and show them rejected under the text-only contract.

## Scene 6 — Fingerprint verified bytes

Build a synthetic bundle fingerprint from the accepted bytes.

## Scene 7 — Stage and compare

Stage the synthetic bundle and compare staged bytes exactly with the verified snapshot.

## Scene 8 — Detect drift

Change one synthetic staged byte and show the verification result fail closed.

## Closing rule

Verify source identity first, then independently verify byte fidelity through decoding, packaging, staging, and readback.

Use only synthetic identifiers, filenames, paths, hashes, payloads, and runtime values in the demo.
