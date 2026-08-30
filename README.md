# PAI Reliability Evidence

Public, sanitized evidence derived from verified PAI reliability test results.

## What this repository is

This repository publishes bounded reliability evidence that can be inspected without exposing private implementation details, credentials, internal paths, or sensitive operational logs.

Current published evidence:

- Core candidate test suite: **35 passed, 0 failed**.
- Focused SQLite lock-budget checks: **3 passed, 0 failed**.

See [`evidence/2026-08-29-reliability-tests.md`](evidence/2026-08-29-reliability-tests.md) for the sanitized evidence snapshot and [`PROVENANCE.md`](PROVENANCE.md) for publication boundaries.

## Claim boundary

These results show that the listed checks passed in the captured test runs. They are not a claim of production certification, universal correctness, security certification, or zero defects.

## Publication policy

Only evidence that can be shared without leaking private PAI internals is published here. Private source code, credentials, host details, internal paths, raw sensitive logs, and unlicensed third-party material are intentionally excluded.

## License

No license is specified for this repository at this time.
