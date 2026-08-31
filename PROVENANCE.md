# Provenance and Publication Boundaries

## Source class

Published material in this repository is derived from verified PAI result evidence or from public-safe reusable abstractions created from that evidence.

The repository is an **Open Foundation evidence and learning surface**, not a mirror of the complete PAI system.

## Verification standard

Only terminal outcomes that were already observed as completed and passing may be represented as completed evidence.

Planned, queued, materialized, running, candidate, or partially verified work must not be rewritten as terminal `DONE` merely because it appears in a public document.

Public workflow and skill documents may describe a general method without claiming that every future implementation of that method has already passed PAI verification.

## Sanitization

Before publication, material is reduced to the reusable lesson and bounded claim. Public versions exclude, unless an explicit rights/safety decision says otherwise:

- credentials, secrets, and trust-root material;
- private PAI source and internal implementation details;
- private host identities and filesystem paths;
- sensitive or unnecessary raw logs;
- private task IDs, internal fingerprints, or topology that add no public value;
- customer/tenant source, traces, incidents, product evidence, or data;
- protected evaluation corpora and deep proprietary failure intelligence;
- third-party material without clear rights to publish.

Synthetic examples are preferred when they teach the same lesson without exposing private reality.

## Claim discipline

A passing test is reported as a passing test. It is not promoted into a claim of production readiness, security certification, universal correctness, high availability, complete safety, or zero defects unless separate evidence explicitly supports that claim.

`UNKNOWN` is preserved when evidence does not establish a fact.

Failure history is preserved. A later PASS supersedes an earlier failure only when the later evidence actually closes the same acceptance boundary.

## Open Foundation versus Protected Core

Public candidates include scrubbed and rights-cleared evidence summaries, checklists, skill recipes, workflow templates, synthetic demos, schemas, examples, standards mappings, and bounded case studies.

Protected Core material includes private continuity/authority internals, proprietary implementation, deep optimizations, protected evaluation corpora, private/shared failure-intelligence datasets, customer-private evidence, and private/sovereign execution internals unless an explicit later decision publishes a bounded part of them.

See `OPEN_FOUNDATION.md` for the full boundary.

## Licensing

Unless a file says otherwise, public **non-code** content in this repository is licensed under **CC BY 4.0** as described in `LICENSE.md`.

That license grant applies only to material the repository owner or contributors have the rights to license. It does not extend to unpublished/private PAI material, Protected Core content, customer data/evidence, third-party material, trademarks/branding rights, or future software that lacks an explicit software license.

Publication of a public pattern never implies a license grant to the unpublished machinery that may have produced the original private evidence.

## Commercial/private assurance

The open repository should remain useful without payment.

A full PAI Assurance engagement may use private execution, customer-specific reconstruction, protected evaluation/failure intelligence, repeated verification, or private/sovereign environments under separate authorization and commercial terms. Public documentation does not itself create a service contract, certification, warranty, pricing commitment, or availability claim.
