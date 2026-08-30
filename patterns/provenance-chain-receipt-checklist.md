# Provenance Chain Receipt Checklist

Use this checklist when a passing build or test result needs stronger evidence that the inspected bytes, generated artifact, executor evidence, QA receipts, and reported change set belong to one reproducible chain.

## Minimal receipt fields

- result identity
- source-manifest fingerprint and entry count
- candidate-tree fingerprint and entry count
- executor-evidence fingerprint
- QA artifact fingerprints
- change-set derivation method
- change-set fingerprint
- focused-suite pass/total counts
- pre-verification snapshot fingerprint
- post-verification snapshot fingerprint
- mutation-diff count
- verifier identity and observation time
- status: `VERIFIED`, `SOURCE_CHECK_REQUIRED`, or `MISMATCH`
- unsupported claims

## Acceptance checklist

- [ ] Required evidence inputs are frozen or fingerprint-bound.
- [ ] Source-manifest entries match expected bytes or fingerprints.
- [ ] The candidate tree is reconstructed instead of trusted from narrative.
- [ ] Executor evidence identity is checked.
- [ ] Earlier QA/HANDOFF identities are checked when they are part of the chain.
- [ ] A reported change is derived from bytes or equivalent primary evidence.
- [ ] Focused verification is re-run independently.
- [ ] Read-only verification produces zero mutation of the inspected bundle.
- [ ] Missing or contradictory evidence fails closed.
- [ ] The receipt states unsupported claims explicitly.
- [ ] Verification does not grant promotion, deployment, writer, claim, or publication authority.

## Reference proof

One bounded verification run satisfied **125/125** source-manifest checks, regenerated a matching **55-entry** candidate tree, passed a focused **58/58** suite, matched recorded executor/QA identities, derived its change claim from byte comparison, and produced a pre/post mutation diff of **0**.

## Boundary

This pattern strengthens provenance for a bounded result. It is not a scheduler, release manager, deployment controller, trust root, or proof of universal supply-chain security.
