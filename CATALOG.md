# Public Evidence and Learning Catalog

This catalog organizes the public PAI Reliability Evidence material by the problem it helps a reader reason about.

The repository intentionally publishes **bounded lessons and reusable evidence patterns**, not the complete internal PAI implementation.

## 1. Foundations

- [`PROVENANCE.md`](PROVENANCE.md) — what counts as verified public evidence and what is excluded.
- [`OPEN_FOUNDATION.md`](OPEN_FOUNDATION.md) — public versus Protected Core boundary.
- [`COMMUNITY.md`](COMMUNITY.md) — how to learn from and contribute to the repository.
- [`ASSURANCE.md`](ASSURANCE.md) — community layer versus full private/commercial assurance workflow.
- [`workflows/community-assurance-baseline.md`](workflows/community-assurance-baseline.md) — generic evidence-first workflow.
- [`runbooks/source-only-resume.md`](runbooks/source-only-resume.md) — reconstruct durable context from verified sources after a fresh session, while fetching volatile runtime truth JIT.
- [`skills/README.md`](skills/README.md) — compact reusable assurance skill recipes, including audit finding clustering.
- [`skills/release-scope-integrity.md`](skills/release-scope-integrity.md) — verify complete release composition against an authorized delta even when focused tests pass.
- [`skills/reachable-path-policy-integrity.md`](skills/reachable-path-policy-integrity.md) — verify one invariant across every reachable route to a protected effect.
- [`skills/deterministic-source-resolution.md`](skills/deterministic-source-resolution.md) — resolve durable context from pinned evidence while keeping volatile runtime truth JIT.

## 2. Core reliability evidence

- [`evidence/2026-08-29-reliability-tests.md`](evidence/2026-08-29-reliability-tests.md) — bounded core and SQLite lock-budget test evidence.
- [`evidence/2026-08-30-reversible-cutover-verification.md`](evidence/2026-08-30-reversible-cutover-verification.md) — reversible cutover and terminal readback.
- [`evidence/2026-08-30-safe-failover-simulation.md`](evidence/2026-08-30-safe-failover-simulation.md) — deterministic failover/fencing simulation.
- [`evidence/2026-08-30-executor-timeout-supersession.md`](evidence/2026-08-30-executor-timeout-supersession.md) — preserving failure truth and explicit supersession.
- [`evidence/2026-08-30-recoverability-taxonomy.md`](evidence/2026-08-30-recoverability-taxonomy.md) — evidence-first recovery classification.
- [`evidence/2026-08-30-fail-closed-acl-scope-validation.md`](evidence/2026-08-30-fail-closed-acl-scope-validation.md) — fail-closed access/scope validation.
- [`evidence/2026-08-30-evidence-driven-reuse-freeze.md`](evidence/2026-08-30-evidence-driven-reuse-freeze.md) — reuse freeze and explicit `UNKNOWN` handling.
- [`evidence/2026-08-30-pre-activation-freeze-verification.md`](evidence/2026-08-30-pre-activation-freeze-verification.md) — verified candidate freeze without activation inference.
- [`evidence/2026-08-30-portable-byte-fidelity.md`](evidence/2026-08-30-portable-byte-fidelity.md) — byte-accurate transport and encoding boundaries.
- [`evidence/2026-08-30-software-dr-contract.md`](evidence/2026-08-30-software-dr-contract.md) — prove restore behavior rather than backup existence.
- [`evidence/2026-08-30-physical-startup-validation.md`](evidence/2026-08-30-physical-startup-validation.md) — bounded physical startup/canary evidence.
- [`evidence/2026-08-30-successor-composition-verification.md`](evidence/2026-08-30-successor-composition-verification.md) — review reused bytes plus the actual successor delta.
- [`evidence/2026-08-30-immutable-provenance-chain.md`](evidence/2026-08-30-immutable-provenance-chain.md) — reconstructing evidence from immutable provenance.
- [`evidence/2026-08-30-immutable-evidence-freeze-qa.md`](evidence/2026-08-30-immutable-evidence-freeze-qa.md) — large-tree freeze/readback verification.
- [`evidence/2026-08-30-portable-secret-classification.md`](evidence/2026-08-30-portable-secret-classification.md) — reduce tested false positives without weakening tested fail-closed secret classes.
- [`evidence/2026-08-30-post-promotion-ownership-continuity.md`](evidence/2026-08-30-post-promotion-ownership-continuity.md) — bounded ownership continuity after promotion.
- [`evidence/2026-08-31-global-assurance-audit-clustering.md`](evidence/2026-08-31-global-assurance-audit-clustering.md) — 86 raw audit occurrences integrated into 27 bounded causal clusters while preserving incomplete coverage and repair separation.
- [`evidence/2026-08-31-release-scope-integrity.md`](evidence/2026-08-31-release-scope-integrity.md) — a focused-test-passing candidate was correctly rejected when complete composition exceeded the qualified change scope.
- [`evidence/2026-08-31-reachable-path-policy-integrity.md`](evidence/2026-08-31-reachable-path-policy-integrity.md) — common-path tests passed, but route-level falsification found a weaker reachable path to the same protected effect.
- [`evidence/2026-08-31-deterministic-source-frontier-resolution.md`](evidence/2026-08-31-deterministic-source-frontier-resolution.md) — bounded candidate resolved durable context deterministically from validated sources and failed closed on invalid source conditions.
- [`evidence/2026-08-31-desired-observed-control-surface.md`](evidence/2026-08-31-desired-observed-control-surface.md) — desired intent, observed state, binding truth, and explicit reconciliation remained separate across a terminal candidate wave.

## 3. Reusable verification patterns

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
- [`patterns/immutable-evidence-freeze-qa-checklist.md`](patterns/immutable-evidence-freeze-qa-checklist.md)
- [`patterns/source-safety-gate-checklist.md`](patterns/source-safety-gate-checklist.md)
- [`patterns/single-owner-cutover-soak-gate.md`](patterns/single-owner-cutover-soak-gate.md)
- [`patterns/audit-to-repair-clustering-checklist.md`](patterns/audit-to-repair-clustering-checklist.md) — dedupe occurrence noise, preserve coverage truth, cluster by causal boundary, and admit repair only when bounded.
- [`patterns/release-scope-integrity-receipt.md`](patterns/release-scope-integrity-receipt.md) — complete baseline/candidate set comparison against an independently represented authorized delta.
- [`patterns/reachable-path-policy-integrity-checklist.md`](patterns/reachable-path-policy-integrity-checklist.md) — enumerate all routes, bind one invariant to one governed owner, and falsify weaker special paths.
- [`patterns/deterministic-source-resolution-contract.md`](patterns/deterministic-source-resolution-contract.md) — validate source identity and precedence before durable interpretation; keep volatile runtime truth separate.
- [`patterns/source-binding-integrity-checklist.md`](patterns/source-binding-integrity-checklist.md) — bind physical source identity separately from semantic role, surface drift, and keep staged versus activated states explicit.
- [`patterns/desired-observed-control-surface-checklist.md`](patterns/desired-observed-control-surface-checklist.md) — keep operator intent, runtime readback, binding state, drift, and reconciliation direction explicit.

## 4. Case studies

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
- [`case-studies/freezing-a-large-evidence-tree-before-promotion.md`](case-studies/freezing-a-large-evidence-tree-before-promotion.md)
- [`case-studies/when-token-is-just-a-variable-name.md`](case-studies/when-token-is-just-a-variable-name.md)
- [`case-studies/a-canary-pass-is-not-a-stable-owner.md`](case-studies/a-canary-pass-is-not-a-stable-owner.md)
- [`case-studies/86-findings-27-defects-zero-ticket-avalanche.md`](case-studies/86-findings-27-defects-zero-ticket-avalanche.md) — why raw audit volume should not become repair-task volume.
- [`case-studies/green-tests-wrong-release.md`](case-studies/green-tests-wrong-release.md) — why passing behavior tests cannot launder unrelated packaging drift into an approved release.
- [`case-studies/the-path-that-passed-around-the-policy.md`](case-studies/the-path-that-passed-around-the-policy.md) — common-path correctness did not close an alternate reachable route with weaker admission logic.
- [`case-studies/making-current-state-a-verifiable-claim.md`](case-studies/making-current-state-a-verifiable-claim.md) — deterministic durable source resolution without confusing it with live runtime truth.
- [`case-studies/designing-an-ai-system-that-can-forget-safely.md`](case-studies/designing-an-ai-system-that-can-forget-safely.md) — source-only resume from verified durable context without treating conversation memory as authority.
- [`case-studies/when-a-pointer-exists-but-isnt-trustworthy.md`](case-studies/when-a-pointer-exists-but-isnt-trustworthy.md) — source identity, semantic role, drift, staging, and activation are kept as separate claims.
- [`case-studies/building-a-control-panel-that-refuses-to-lie.md`](case-studies/building-a-control-panel-that-refuses-to-lie.md) — mixed binding states and drift remain truthful instead of being flattened into fake live controls.

## 5. Synthetic demos

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
- [`demos/large-tree-freeze-evidence-storyboard.md`](demos/large-tree-freeze-evidence-storyboard.md)
- [`demos/source-safety-gate-evidence-walkthrough.md`](demos/source-safety-gate-evidence-walkthrough.md)
- [`demos/why-many-failures-might-be-one-defect.md`](demos/why-many-failures-might-be-one-defect.md) — synthetic occurrence-to-causal-cluster walkthrough.
- [`demos/green-tests-wrong-release-walkthrough.md`](demos/green-tests-wrong-release-walkthrough.md) — synthetic full-tree release-scope gate after a passing focused suite.
- [`demos/one-policy-two-paths-walkthrough.md`](demos/one-policy-two-paths-walkthrough.md) — synthetic route-level falsifier exposing a weaker alternate path.
- [`demos/stop-guessing-what-current-means.md`](demos/stop-guessing-what-current-means.md) — synthetic fail-closed durable-source projection with JIT runtime separation.
- [`demos/the-settings-panel-that-knows-when-a-switch-is-fake.md`](demos/the-settings-panel-that-knows-when-a-switch-is-fake.md) — synthetic desired/observed and binding-state walkthrough.

## 6. How to choose what to read

If your problem is **release/cutover confidence**, start with reversible cutover, pre-activation freeze, successor composition, single-owner soak, and release-scope integrity.

If your problem is **recovery**, start with recoverability taxonomy, software DR, immutable evidence freeze, and provenance reconstruction.

If your problem is **security/safety boundaries**, start with ACL scope validation, Source Safety Gate, reachable-path policy integrity, and the public evidence-sanitization skill.

If your problem is **trusting test results**, start with terminal-result supersession, Evidence Boundary Review, “verified but not activated,” release-scope integrity, and route-parity falsification.

If your problem is **audit noise or duplicate repair work**, start with global assurance audit clustering, the audit-to-repair checklist, Skill 7, and the synthetic clustering walkthrough.

If your problem is **stale handoffs or conflicting durable sources**, start with deterministic source/frontier resolution, source-binding integrity, and the synthetic “Stop Guessing What Current Means” walkthrough.

If your problem is **session/model replacement or safe resume**, use the source-only resume runbook after the deterministic source-resolution material.

If your problem is **operator controls, drift, or fake settings switches**, start with desired/observed control-surface evidence and checklist.

## Claim boundary

This catalog is an index of public evidence and learning material. Inclusion here does not make an item a certification, production guarantee, product availability claim, or disclosure of the PAI Protected Core.
