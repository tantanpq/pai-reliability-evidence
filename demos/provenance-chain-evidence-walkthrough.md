# Provenance Chain Evidence Walkthrough

A short synthetic demo for showing why a passing result should be traceable to immutable evidence rather than trusted as a label.

## Walkthrough

1. Start with a synthetic build marked `PASS` and a plausible change summary.
2. Ask which exact source bytes and generated tree were actually tested.
3. Verify a synthetic source manifest by fingerprint and entry count.
4. Regenerate a synthetic candidate tree and compare its fingerprint.
5. Bind synthetic executor and QA receipts by immutable identity.
6. Derive a synthetic change set from byte comparison rather than filenames.
7. Re-run a focused verification suite and record pass/total counts.
8. Compare pre/post snapshots and require `mutation_diff_count = 0` for read-only verification.
9. Corrupt one synthetic receipt fingerprint and return `MISMATCH` instead of guessing.
10. End with the rule: verify the evidence chain, then keep promotion as a separate authority gate.

## Reference evidence

The bounded result behind this walkthrough reported **125/125** exact source-manifest checks, a matching **55-entry** regenerated candidate tree, **58/58** focused checks passing, matching executor/QA identities, byte-derived change evidence, and **0** inspected-bundle mutations.

## Public-demo safety

Use only synthetic IDs, hashes, paths, filenames, hostnames, and runtime values. Do not expose credentials, private implementation source, raw sensitive logs, or private operational identifiers.

## Boundary

The demo illustrates a verification pattern. It does not demonstrate universal supply-chain security, production readiness, or automatic release authority.
