# Community Guide

This repository is intended to be useful **before** anyone buys anything.

Its public purpose is to help engineers, researchers, operators, security teams, and builders reason more carefully about reliability, evidence, recovery, cutover safety, provenance, and AI/automation assurance.

## Start with a real problem

Use the repository when you need to answer questions such as:

- Did the change really produce the declared output?
- Is a green canary enough, or did ownership remain stable afterward?
- Can a system recover the exact bytes it claims to protect?
- Is a passing result supported by independent evidence or only by the component that produced it?
- Did a failure disappear, or was it explicitly superseded by stronger evidence?
- Can source-safety checks reject real sensitive material without blocking benign code?
- Are the tested claims narrower than the marketing language around them?

## Suggested learning path

1. Read `PROVENANCE.md` to understand evidence and publication boundaries.
2. Read `OPEN_FOUNDATION.md` to understand what is intentionally public and what stays protected.
3. Pick one problem from `patterns/`.
4. Read the matching `case-studies/` example.
5. Use a synthetic walkthrough from `demos/`.
6. Try the community workflow in `workflows/community-assurance-baseline.md` on a disposable or authorized system.
7. Record what passed, failed, remained unknown, and what claims are still unsupported.

## Community principles

- Evidence beats confidence.
- `UNKNOWN` is better than invented proof.
- Candidate, running, passing, live, and done are different states.
- A blocker should block its dependency cone, not unrelated work.
- Verify the owning seam rather than multiplying retries around it.
- Keep release/deployment authority separate from verification.
- Preserve privacy, ownership, provenance, and reversible boundaries.
- Share reusable lessons without dumping private internals.

## Contributions

Useful contributions include:

- a clearer reusable checklist;
- a synthetic fixture that demonstrates a failure class safely;
- a bounded case study with evidence and claim limits;
- an interoperability or standards mapping;
- a workflow improvement that removes ambiguity or false PASS;
- a correction to an unsupported or overly broad claim.

Please do **not** submit real credentials, private customer data, sensitive logs, proprietary source you do not have permission to publish, exploit material intended for misuse, or internal PAI Protected Core content.

## Evidence standard for contributed case studies

A case study should distinguish at least:

- observed fact;
- test or reproduction method;
- terminal outcome;
- independent verification, if any;
- unsupported claims;
- sanitization and provenance notes.

A planned test is not a passing test. A passing unit test is not automatically production proof. A public story should never be stronger than the evidence behind it.

## Commercial work is optional

The Open Foundation is not a teaser that becomes useless unless someone pays. The public patterns should stand on their own.

For teams that need deeper private execution, customer-specific evidence, repeated assurance, or a private/sovereign environment, `ASSURANCE.md` describes the separate PAI Assurance path and its boundaries.
