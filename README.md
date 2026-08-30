# PAI Reliability Evidence

Public, sanitized evidence derived from verified PAI reliability results.

## What this repository is

This repository publishes bounded reliability evidence and reusable verification patterns without exposing private implementation details, credentials, internal paths, or sensitive operational logs.

## Published evidence

- Core candidate test suite: **35 passed, 0 failed**.
- Focused SQLite lock-budget checks: **3 passed, 0 failed**.
- Reversible cutover: independently QA-passed candidate, exact checked-byte readback, bounded restart, canary verification, terminal completion, and post-terminal readback passed.
- Deterministic two-node failover simulation: **21/21 scenarios passed**, including strict lease expiry, single-writer takeover, monotonic fencing, stale-owner rejection, terminal-result reconciliation, provenance guards, and fail-closed unsafe-state handling. Production activation remained disabled.
- Executor-timeout supersession: an infrastructure-timeout FAIL was preserved and explicitly superseded only after a later bounded PASS satisfied the acceptance evidence, including **39 focused tests across 4 suites**.

Evidence snapshots:

- [`evidence/2026-08-29-reliability-tests.md`](evidence/2026-08-29-reliability-tests.md)
- [`evidence/2026-08-30-reversible-cutover-verification.md`](evidence/2026-08-30-reversible-cutover-verification.md)
- [`evidence/2026-08-30-safe-failover-simulation.md`](evidence/2026-08-30-safe-failover-simulation.md)
- [`evidence/2026-08-30-executor-timeout-supersession.md`](evidence/2026-08-30-executor-timeout-supersession.md)

Reusable derivatives:

- [`patterns/reversible-cutover-verification-checklist.md`](patterns/reversible-cutover-verification-checklist.md)
- [`patterns/fail-closed-failover-checklist.md`](patterns/fail-closed-failover-checklist.md)
- [`patterns/terminal-result-supersession-checklist.md`](patterns/terminal-result-supersession-checklist.md)
- [`case-studies/reversible-cutover-terminal-readback.md`](case-studies/reversible-cutover-terminal-readback.md)
- [`case-studies/deterministic-two-node-failover-simulation.md`](case-studies/deterministic-two-node-failover-simulation.md)
- [`demos/reversible-cutover-evidence-walkthrough.md`](demos/reversible-cutover-evidence-walkthrough.md)
- [`demos/failover-fencing-evidence-walkthrough.md`](demos/failover-fencing-evidence-walkthrough.md)

See [`PROVENANCE.md`](PROVENANCE.md) for publication boundaries.

## Claim boundary

These results show only that the listed checks passed in the captured runs. They are not a claim of production certification, universal correctness, security certification, availability guarantee, or zero defects.

## Publication policy

Only evidence that can be shared without leaking private PAI internals is published here. Private source code, credentials, host details, internal paths, raw sensitive logs, and unlicensed third-party material are intentionally excluded.

## License

No license is specified for this repository at this time.
