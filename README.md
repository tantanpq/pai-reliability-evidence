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
- Portable byte-fidelity verification: independent QA verified **11/11 immutable manifest entries** totaling **22,356 bytes**, reconstructed the pinned baseline byte-for-byte, passed ordinary UTF-8 and UTF-8-with-BOM round trips, rejected malformed/unsupported text and embedded-NUL cases, and independently confirmed exact staged bytes without live-runtime mutation.
- Software DR contract verification: **13/13 ordinary allowlisted files** were covered by full/incremental manifests and restored byte-for-byte in isolation; secret input was excluded, unsafe/missing/corrupt cases failed closed, and sealed-copy reuse/mutation behavior was verified at the software layer. Offline or physical immutability remains explicitly unproven.
- Physical startup validation: the live startup path reached terminal **DONE / PASS** and independent post-effect QA also passed; a low-density canary completed **1/1**, a bounded burst completed **10/10**, independent re-query confirmed **11/11** physical completions, burst overlap peaked at **10**, execution/result identities were unique, and the narrow permission boundary remained fail-closed outside the intended scope. Continued polling and remote pull/placement remain outside the claim.
- Successor composition verification: independent compositional QA returned **PASS_RELEASE_CANDIDATE** with no critical blockers; inherited security evidence included **42 independent QA checks**, four reused delta files were byte-identical to the prior reviewed candidate, the remaining integration change was bounded to **4 nonblank diff records**, and configured plus exact successor checks completed with exit `0` and empty stderr. The full successor tree was not independently re-executed, and activation is not claimed.
- Immutable provenance-chain reconstruction: **125/125** source-manifest checks matched, a regenerated **55-entry** candidate tree matched its recorded fingerprint, the focused continuity suite passed **58/58**, executor/QA identities matched the recorded evidence chain, the reported change claim was byte-derived, and read-only pre/post bundle diff was **0**.

Evidence snapshots:

- [`evidence/2026-08-29-reliability-tests.md`](evidence/2026-08-29-reliability-tests.md)
- [`evidence/2026-08-30-reversible-cutover-verification.md`](evidence/2026-08-30-reversible-cutover-verification.md)
- [`evidence/2026-08-30-safe-failover-simulation.md`](evidence/2026-08-30-safe-failover-simulation.md)
- [`evidence/2026-08-30-executor-timeout-supersession.md`](evidence/2026-08-30-executor-timeout-supersession.md)
- [`evidence/2026-08-30-recoverability-taxonomy.md`](evidence/2026-08-30-recoverability-taxonomy.md)
- [`evidence/2026-08-30-fail-closed-acl-scope-validation.md`](evidence/2026-08-30-fail-closed-acl-scope-validation.md)
- [`evidence/2026-08-30-evidence-driven-reuse-freeze.md`](evidence/2026-08-30-evidence-driven-reuse-freeze.md)
- [`evidence/2026-08-30-pre-activation-freeze-verification.md`](evidence/2026-08-30-pre-activation-freeze-verification.md)
- [`evidence/2026-08-30-portable-byte-fidelity.md`](evidence/2026-08-30-portable-byte-fidelity.md)
- [`evidence/2026-08-30-software-dr-contract.md`](evidence/2026-08-30-software-dr-contract.md)
- [`evidence/2026-08-30-physical-startup-validation.md`](evidence/2026-08-30-physical-startup-validation.md)
- [`evidence/2026-08-30-successor-composition-verification.md`](evidence/2026-08-30-successor-composition-verification.md)
- [`evidence/2026-08-30-immutable-provenance-chain.md`](evidence/2026-08-30-immutable-provenance-chain.md)

Reusable derivatives:

- [`patterns/reversible-cutover-verification-checklist.md`](patterns/reversible-cutover-verification-checklist.md)
- [`patterns/fail-closed-failover-checklist.md`](patterns/fail-closed-failover-checklist.md)
- [`patterns/terminal-result-supersession-checklist.md`](patterns/terminal-result-supersession-checklist.md)
- [`patterns/assurance-proof-pattern-pack.md`](patterns/assurance-proof-pattern-pack.md)
- [`patterns/evidence-first-recovery-classification-checklist.md`](patterns/evidence-first-recovery-classification-checklist.md)
- [`patterns/fail-closed-acl-scope-validation-checklist.md`](patterns/fail-closed-acl-scope-validation-checklist.md)
- [`patterns/verified-reuse-freeze-checklist.md`](patterns/verified-reuse-freeze-checklist.md)
- [`patterns/pre-activation-freeze-gate-checklist.md`](patterns/pre-activation-freeze-gate-checklist.md)
- [`patterns/portable-byte-fidelity-checklist.md`](patterns/portable-byte-fidelity-checklist.md)
- [`patterns/software-dr-acceptance-checklist.md`](patterns/software-dr-acceptance-checklist.md)
- [`patterns/physical-startup-verification-checklist.md`](patterns/physical-startup-verification-checklist.md)
- [`patterns/compositional-successor-verification-checklist.md`](patterns/compositional-successor-verification-checklist.md)
- [`patterns/provenance-chain-receipt-checklist.md`](patterns/provenance-chain-receipt-checklist.md)
- [`case-studies/reversible-cutover-terminal-readback.md`](case-studies/reversible-cutover-terminal-readback.md)
- [`case-studies/deterministic-two-node-failover-simulation.md`](case-studies/deterministic-two-node-failover-simulation.md)
- [`case-studies/fail-closed-recovery-classification.md`](case-studies/fail-closed-recovery-classification.md)
- [`case-studies/acl-boundary-tightening-with-frozen-byte-qa.md`](case-studies/acl-boundary-tightening-with-frozen-byte-qa.md)
- [`case-studies/reuse-freeze-before-successor-generation.md`](case-studies/reuse-freeze-before-successor-generation.md)
- [`case-studies/verified-but-not-activated.md`](case-studies/verified-but-not-activated.md)
- [`case-studies/verify-bytes-before-trusting-text.md`](case-studies/verify-bytes-before-trusting-text.md)
- [`case-studies/prove-the-restore-not-just-the-backup.md`](case-studies/prove-the-restore-not-just-the-backup.md)
- [`case-studies/from-permission-repair-to-physical-startup-proof.md`](case-studies/from-permission-repair-to-physical-startup-proof.md)
- [`case-studies/review-the-delta-not-the-release-label.md`](case-studies/review-the-delta-not-the-release-label.md)
- [`case-studies/reconstructing-evidence-behind-green-result.md`](case-studies/reconstructing-evidence-behind-green-result.md)
- [`demos/reversible-cutover-evidence-walkthrough.md`](demos/reversible-cutover-evidence-walkthrough.md)
- [`demos/failover-fencing-evidence-walkthrough.md`](demos/failover-fencing-evidence-walkthrough.md)
- [`demos/recoverability-taxonomy-walkthrough.md`](demos/recoverability-taxonomy-walkthrough.md)
- [`demos/acl-scope-validation-evidence-walkthrough.md`](demos/acl-scope-validation-evidence-walkthrough.md)
- [`demos/unknown-is-not-missing-walkthrough.md`](demos/unknown-is-not-missing-walkthrough.md)
- [`demos/green-build-frozen-release-walkthrough.md`](demos/green-build-frozen-release-walkthrough.md)
- [`demos/same-text-different-bytes-walkthrough.md`](demos/same-text-different-bytes-walkthrough.md)
- [`demos/backup-is-not-recovery-test-walkthrough.md`](demos/backup-is-not-recovery-test-walkthrough.md)
- [`demos/physical-startup-evidence-walkthrough.md`](demos/physical-startup-evidence-walkthrough.md)
- [`demos/successor-composition-evidence-walkthrough.md`](demos/successor-composition-evidence-walkthrough.md)
- [`demos/provenance-chain-evidence-walkthrough.md`](demos/provenance-chain-evidence-walkthrough.md)

See [`PROVENANCE.md`](PROVENANCE.md) for publication boundaries.

## Claim boundary

These results show only that the listed checks passed in the captured runs. They are not a claim of production certification, universal correctness, security certification, availability guarantee, or zero defects.

## Publication policy

Only evidence that can be shared without leaking private PAI internals is published here. Private source code, credentials, host details, internal paths, raw sensitive logs, and unlicensed third-party material are intentionally excluded.

## License

No license is specified for this repository at this time.
