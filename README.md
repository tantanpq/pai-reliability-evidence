# PAI Reliability Evidence

Public, sanitized evidence derived from verified PAI reliability results.

## What this repository is

This repository publishes bounded reliability evidence and reusable verification patterns without exposing private implementation details, credentials, internal paths, or sensitive operational logs.

## Published evidence

- Core candidate test suite: **35 passed, 0 failed**.
- Focused SQLite lock-budget checks: **3 passed, 0 failed**.
- Reversible cutover: independently QA-passed candidate, exact checked-byte readback, bounded restart, canary verification, terminal completion, and post-terminal readback passed.

Evidence snapshots:

- [`evidence/2026-08-29-reliability-tests.md`](evidence/2026-08-29-reliability-tests.md)
- [`evidence/2026-08-30-reversible-cutover-verification.md`](evidence/2026-08-30-reversible-cutover-verification.md)

Reusable derivatives:

- [`patterns/reversible-cutover-verification-checklist.md`](patterns/reversible-cutover-verification-checklist.md)
- [`case-studies/reversible-cutover-terminal-readback.md`](case-studies/reversible-cutover-terminal-readback.md)
- [`demos/reversible-cutover-evidence-walkthrough.md`](demos/reversible-cutover-evidence-walkthrough.md)

See [`PROVENANCE.md`](PROVENANCE.md) for publication boundaries.

## Claim boundary

These results show only that the listed checks passed in the captured runs. They are not a claim of production certification, universal correctness, security certification, availability guarantee, or zero defects.

## Publication policy

Only evidence that can be shared without leaking private PAI internals is published here. Private source code, credentials, host details, internal paths, raw sensitive logs, and unlicensed third-party material are intentionally excluded.

## License

No license is specified for this repository at this time.
