# PAI Assurance — Community and Full Workflow Boundary

PAI Assurance is an evidence-first approach to verifying real systems, changes, recovery paths, and operational claims.

This repository exposes the **community/open layer**. It does not publish the entire internal PAI verification machinery.

## Community layer — open and self-service

The public repository provides reusable material for teams that want to improve their own assurance practice without a commercial engagement:

- evidence-first verification patterns;
- cutover, ownership, recovery, provenance, and source-safety checklists;
- synthetic demos;
- case studies with bounded claims;
- community skill recipes;
- a generic assurance workflow that can be adapted to disposable or authorized environments.

The public layer should remain useful by itself.

## Full PAI Assurance workflow — commercial/private path

A deeper PAI Assurance engagement may be appropriate when a team needs verification on a real product, private repository, live-like environment, incident, or controlled production-readiness boundary.

A full workflow may include, when authorized and technically appropriate:

1. **Scope and claim lock** — define the exact product/change, declared outcomes, unsupported claims, effect boundary, and evidence owners.
2. **Reality capsule** — freeze the relevant source/revision/release/config/state/trace needed to reproduce the declared system boundary.
3. **Reconstruction and fidelity checks** — prove that the system under evaluation matches the intended inputs closely enough for the requested claim.
4. **Verification plan** — select deterministic, differential, mutation, restart, fault, black-box, recovery, security, or lifecycle checks according to the actual risk.
5. **Failure staircase** — continue through verified failures to find the next hidden seam instead of stopping at the first defect.
6. **Root-seam repair loop** — where repair is in scope, fix the owning defect class, preserve unrelated known-good behavior, and rerun the relevant evidence path.
7. **Independent assurance** — separate builder/repair evidence from terminal review where the risk or claim warrants it.
8. **Outcome evidence bundle** — deliver reproducible evidence, provenance, claim boundaries, remaining unknowns, and a reopen path.
9. **Reverification** — rerun the bounded evidence after meaningful changes rather than relying on stale green status.

## When the commercial/private path is justified

Paid or scoped engagement conditions may include:

- private source or customer-controlled evidence must stay inside a declared environment;
- customer-specific adapters or reconstruction are required;
- a private/sovereign runner is needed;
- deep failure analysis or repeated regression retention is required;
- the team needs independent evidence for a release, incident, migration, cutover, or recovery claim;
- ongoing assurance is required across meaningful changes;
- delivery effort, compute, specialist review, or controlled security evaluation materially exceeds the open self-service layer.

Commercial terms, pricing, support commitments, and any service-level obligations require separate explicit agreement. This repository does not create them automatically.

## What a full engagement does not mean

PAI Assurance is not, by itself:

- a regulated certification body;
- a guarantee of zero defects;
- an availability or security warranty;
- permission to test systems without authorization;
- a substitute for customer legal/compliance responsibility;
- a claim that every PAI internal capability is publicly available.

## Customer ownership and privacy

Customer-private source, traces, incidents, evidence, and product data remain customer/tenant material. Shared learning should contain only scrubbed, rights-cleared, provenance-preserving abstractions that are safe to reuse.

## Maturity truth

The workflow above describes the intended full assurance surface and operating boundary. Public documentation is not evidence that every commercial package or tier is generally available, certified, or repeatably proven at scale.

Commercial maturity must be earned through real problem interviews, quantified pain, identified buyers, paid pilots, measured value, renewal/expansion, and repeatable delivery.
