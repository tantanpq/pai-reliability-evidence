# PAI Reliability Evidence

Public, sanitized reliability and assurance evidence from PAI, organized as a **community-first Open Foundation**.

This repository shares practical verification patterns, bounded evidence, synthetic demos, reusable workflows, and case studies for people building AI agents, automation, developer platforms, distributed systems, recovery paths, and safety-sensitive software.

It does **not** publish the complete PAI system.

## Why this repository exists

Software teams already have plenty of green dashboards, passing jobs, and release labels. The harder question is:

> **What does the available evidence actually prove, and what is still unknown?**

PAI Reliability Evidence focuses on that gap.

The public material here is designed to help teams reason about questions such as:

- Did the declared output really materialize?
- Can the system recover the exact state or bytes it claims to protect?
- Did a cutover leave one stable owner or a hidden race?
- Is a PASS terminal and independently supported, or merely an intermediate state?
- Did a later success genuinely supersede an earlier failure?
- Can source-safety checks reject tested sensitive classes without blocking benign code?
- Are release, security, or reliability claims broader than the evidence behind them?

## Start here

If you are new to the repository:

1. Read [`PROVENANCE.md`](PROVENANCE.md) for evidence and publication discipline.
2. Read [`OPEN_FOUNDATION.md`](OPEN_FOUNDATION.md) for the public versus Protected Core boundary.
3. Use [`workflows/community-assurance-baseline.md`](workflows/community-assurance-baseline.md) on a disposable or authorized system.
4. Pick a reusable recipe from [`skills/README.md`](skills/README.md).
5. Browse [`CATALOG.md`](CATALOG.md) for evidence, patterns, case studies, and demos by problem class.
6. Read [`COMMUNITY.md`](COMMUNITY.md) if you want to reuse or contribute material.

## What is open

The Open Foundation may include verified and public-safe:

- evidence summaries;
- acceptance checklists and verification patterns;
- synthetic fixtures and demos;
- reusable skill recipes;
- workflow templates;
- public-safe schemas and evidence contracts;
- standards/interoperability examples;
- bounded case studies and negative lessons.

The goal is to make these useful **without requiring payment or access to private PAI internals**.

## What remains protected

The repository intentionally does not disclose the whole PAI capability surface.

Protected material includes, unless separately and explicitly published:

- PAI Mind and private continuity/authority internals;
- private source code and operational configuration;
- credentials, trust roots, private runtime details, and sensitive logs;
- deep proprietary optimizations;
- protected evaluation corpora and hidden adversarial suites;
- private/shared failure-intelligence datasets and repair lineage;
- customer/tenant source, traces, incidents, evidence, and data;
- private/sovereign execution internals.

Open knowledge and a protected core are not contradictory. The public layer should improve the wider engineering community while the protected layer preserves privacy, safety, customer ownership, and legitimate product differentiation.

## Community assurance workflow

A generic evidence-first workflow is published at:

[`workflows/community-assurance-baseline.md`](workflows/community-assurance-baseline.md)

It covers:

```text
LOCK THE CLAIM
→ PIN THE THING BEING TESTED
→ SEPARATE PLANNED / RUNNING / PASS / LIVE / DONE
→ CHOOSE THE SMALLEST DECISIVE CHECKS
→ RUN POSITIVE + NEGATIVE EVIDENCE
→ PRESERVE TERMINAL FAILURE/SUPERSESSION TRUTH
→ ADD INDEPENDENT REVIEW WHERE IT MATERIALLY CHANGES CONFIDENCE
→ SANITIZE ONLY THE REUSABLE LESSON FOR PUBLICATION
```

The workflow is tool-agnostic and intended for systems you own or are authorized to evaluate.

## Reusable skill recipes

[`skills/README.md`](skills/README.md) currently includes compact recipes for:

- Evidence Boundary Review;
- Verify Bytes Before Trusting Labels;
- Canary-to-Soak Continuity Check;
- Source Safety Gate Review;
- Failure Supersession Review;
- Public Evidence Sanitization.

These are public reasoning/verification recipes, not exports of the PAI internal executor or authority system.

## Selected verified evidence

The repository contains bounded public evidence across several reliability classes, including:

- core candidate tests: **35 passed, 0 failed**;
- focused SQLite lock-budget checks: **3 passed, 0 failed**;
- deterministic two-node failover simulation: **21/21** scenarios passed;
- executor-timeout supersession: **39 focused tests across 4 suites** after preserving the earlier failure;
- recoverability classification: **159/159** baseline tests and **166/166** isolated candidate tests with exact source/dependency checks;
- portable byte-fidelity: **11/11** immutable entries totaling **22,356 bytes** plus encoding edge cases;
- software DR: **13/13** allowlisted files restored byte-for-byte in the tested scope;
- immutable provenance-chain reconstruction: **125/125** source checks and **58/58** focused continuity tests;
- large-tree evidence freeze QA: **5,558 files / 194,318,686 bytes** with zero manifest mismatch in the verified scope;
- post-promotion ownership continuity: **30/30** health observations, **48/48** campaign checks, and **12/12** targeted regressions.

These numbers are **evidence summaries, not marketing multipliers**. Every item remains bounded by its own test scope and claim limitations.

See [`CATALOG.md`](CATALOG.md) for the full public index.

## Useful patterns and case studies

Examples include:

- reversible cutover verification;
- fail-closed failover and fencing;
- terminal result supersession;
- evidence-first recovery classification;
- pre-activation freeze gates;
- software disaster-recovery acceptance;
- provenance-chain receipts;
- Source Safety Gate;
- Single-Owner Cutover Soak Gate;
- “Verify Bytes Before Trusting Text”;
- “Prove the Restore, Not Just the Backup”;
- “When Token Is Just a Variable Name”;
- “A Canary Pass Is Not a Stable Owner.”

The matching evidence, checklists, and synthetic demos are indexed in [`CATALOG.md`](CATALOG.md).

## PAI Assurance

The public repository is not a paywall preview. The Open Foundation should remain useful on its own.

Some teams, however, need deeper verification on private products or customer-controlled environments. [`ASSURANCE.md`](ASSURANCE.md) describes the boundary for a fuller PAI Assurance workflow that may include, when authorized and appropriate:

- exact product/change and claim lock;
- private reality/source/release reconstruction;
- fidelity verification;
- restart, fault, differential, mutation, black-box, recovery, lifecycle, or security checks selected for the real risk;
- failure-staircase continuation;
- root-seam repair and reverification;
- independent assurance;
- reproducible private evidence bundles;
- repeated assurance on meaningful changes;
- private/sovereign execution where required.

That deeper path may become a paid/commercial engagement when private execution, specialist review, customer-specific reconstruction, controlled environments, repeated verification, or material delivery cost is involved.

This repository does **not** claim that every commercial package is generally available, certified, or proven at scale. Commercial maturity must be demonstrated through real users, paid evidence, measured value, renewal/expansion, and repeatable delivery.

## Evidence and publication rules

Public material follows several non-negotiable rules:

- planned/materialized/running is not terminal `DONE`;
- a PASS is not automatically LIVE or production-ready;
- failures are preserved rather than edited out of history;
- `UNKNOWN` is better than invented evidence;
- independent QA is used when it materially changes confidence;
- public claims stay narrower than or equal to the verified evidence;
- credentials, private source, sensitive logs, internal paths/hosts, customer data, and unnecessary private fingerprints are excluded;
- third-party material must have clear rights and provenance;
- cyber/security content is defensive and authorization-bound.

See [`PROVENANCE.md`](PROVENANCE.md).

## License

Unless a file says otherwise, public **non-code content** in this repository is licensed under **Creative Commons Attribution 4.0 International (CC BY 4.0)**.

See [`LICENSE.md`](LICENSE.md) for scope and exclusions.

The license applies to public content the repository owner or contributors have the rights to license. It does **not** grant rights to unpublished/private PAI material, Protected Core content, customer evidence, third-party material, trademarks, or future software without an explicit software license.

## Claim boundary

This repository is not a certification authority, security warranty, high-availability guarantee, or claim of zero defects.

Its purpose is narrower and, ideally, more useful:

> **Publish verifiable lessons about how to know what a system actually did, what the evidence supports, what failed, what was repaired, and what remains unknown.**
