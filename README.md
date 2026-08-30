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
- Evidence-first recoverability taxonomy: independent QA matched **174/174** baseline source tuples, passed **159/159** baseline tests, preserved **17/17** candidate source tuples, matched **4/4** pinned dependencies, and passed the full **166/166** isolated candidate suite. The work remained candidate-only and introduced no retry engine or control-plane authority.
- Fail-closed ACL scope validation: candidate checks reported **3/3 syntax** and **4/4 unit/security** passes plus repeated isolated apply/readback; frozen-byte independent security QA subsequently reached **DONE / PASS** under exact-hash, containment, traversal/normalization, forbidden-path, fail-closed, and no-live-mutation acceptance. Physical/live validation is not claimed.
- Evidence-driven reuse freeze: a terminal bootstrap/reuse run reached **DONE**, preserved unavailable proof as `UNKNOWN` rather than inventing missing components, reduced the next frontier to two bounded read/binding investigations, and independently re-verified all **8/8** evidence-bundle SHA-256 entries before publication.
- Pre-activation freeze verification: candidate and independent read-only QA both reached terminal `DONE`; the complete suite passed **166/166**, focused suites passed **24/24**, a **171-entry** candidate tree was independently fingerprint-matched, and six bounded delta hashes were checked. The candidate deliberately remained frozen and not installed, preserving verification and runtime activation as separate decisions.

Evidence snapshots:

- [`evidence/2026-08-29-reliability-tests.md`](evidence/2026-08-29-reliability-tests.md)
- [`evidence/2026-08-30-reversible-cutover-verification.md`](evidence/2026-08-30-reversible-cutover-verification.md)
- [`evidence/2026-08-30-safe-failover-simulation.md`](evidence/2026-08-30-safe-failover-simulation.md)
- [`evidence/2026-08-30-executor-timeout-supersession.md`](evidence/2026-08-30-executor-timeout-supersession.md)
- [`evidence/2026-08-30-recoverability-taxonomy.md`](evidence/2026-08-30-recoverability-taxonomy.md)
- [`evidence/2026-08-30-fail-closed-acl-scope-validation.md`](evidence/2026-08-30-fail-closed-acl-scope-validation.md)
- [`evidence/2026-08-30-evidence-driven-reuse-freeze.md`](evidence/2026-08-30-evidence-driven-reuse-freeze.md)
- [`evidence/2026-08-30-pre-activation-freeze-verification.md`](evidence/2026-08-30-pre-activation-freeze-verification.md)

Reusable derivatives:

- [`patterns/reversible-cutover-verification-checklist.md`](patterns/reversible-cutover-verification-checklist.md)
- [`patterns/fail-closed-failover-checklist.md`](patterns/fail-closed-failover-checklist.md)
- [`patterns/terminal-result-supersession-checklist.md`](patterns/terminal-result-supersession-checklist.md)
- [`patterns/assurance-proof-pattern-pack.md`](patterns/assurance-proof-pattern-pack.md)
- [`patterns/evidence-first-recovery-classification-checklist.md`](patterns/evidence-first-recovery-classification-checklist.md)
- [`patterns/fail-closed-acl-scope-validation-checklist.md`](patterns/fail-closed-acl-scope-validation-checklist.md)
- [`patterns/verified-reuse-freeze-checklist.md`](patterns/verified-reuse-freeze-checklist.md)
- [`patterns/pre-activation-freeze-gate-checklist.md`](patterns/pre-activation-freeze-gate-checklist.md)
- [`case-studies/reversible-cutover-terminal-readback.md`](case-studies/reversible-cutover-terminal-readback.md)
- [`case-studies/deterministic-two-node-failover-simulation.md`](case-studies/deterministic-two-node-failover-simulation.md)
- [`case-studies/fail-closed-recovery-classification.md`](case-studies/fail-closed-recovery-classification.md)
- [`case-studies/acl-boundary-tightening-with-frozen-byte-qa.md`](case-studies/acl-boundary-tightening-with-frozen-byte-qa.md)
- [`case-studies/reuse-freeze-before-successor-generation.md`](case-studies/reuse-freeze-before-successor-generation.md)
- [`case-studies/verified-but-not-activated.md`](case-studies/verified-but-not-activated.md)
- [`demos/reversible-cutover-evidence-walkthrough.md`](demos/reversible-cutover-evidence-walkthrough.md)
- [`demos/failover-fencing-evidence-walkthrough.md`](demos/failover-fencing-evidence-walkthrough.md)
- [`demos/recoverability-taxonomy-walkthrough.md`](demos/recoverability-taxonomy-walkthrough.md)
- [`demos/acl-scope-validation-evidence-walkthrough.md`](demos/acl-scope-validation-evidence-walkthrough.md)
- [`demos/unknown-is-not-missing-walkthrough.md`](demos/unknown-is-not-missing-walkthrough.md)
- [`demos/green-build-frozen-release-walkthrough.md`](demos/green-build-frozen-release-walkthrough.md)

See [`PROVENANCE.md`](PROVENANCE.md) for publication boundaries.

## Claim boundary

These results show only that the listed checks passed in the captured runs. They are not a claim of production certification, universal correctness, security certification, availability guarantee, or zero defects.

## Publication policy

Only evidence that can be shared without leaking private PAI internals is published here. Private source code, credentials, host details, internal paths, raw sensitive logs, and unlicensed third-party material are intentionally excluded.

## License

No license is specified for this repository at this time.
