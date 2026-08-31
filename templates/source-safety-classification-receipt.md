# Source Safety Classification Receipt Template

Use this template to record a bounded source-safety classification result without turning a scanner PASS into a release, deployment, or security-certification claim.

Use only on source and environments you own or are authorized to evaluate.

## Claim

State one narrow claim.

Example:

> The pinned source bundle passed the declared source-safety policy: tested sensitive classes failed closed, tested benign token-like identifiers were not rejected solely by name, and surrounding byte/path/scope/carrier checks remained intact.

## Receipt

```text
CLAIM:
SOURCE_IDENTITY:
SOURCE_SHA256:
CLASSIFIER_VERSION:
PATH_POLICY_VERSION:
CONTENT_POLICY_VERSION:
FIXTURE_SET_VERSION:

BENIGN_TOKEN_IDENTIFIER_CASES_PASSED:
CREDENTIAL_LITERAL_CASES_REJECTED:
PRIVATE_KEY_CASES_REJECTED:
EXPLICIT_PLACEHOLDER_CASES_REJECTED:
SENSITIVE_PATH_CASES_REJECTED:

BYTE_FIDELITY_STATUS:
SCOPE_STATUS:
CARRIER_STATUS:
UTF8_BOM_STATUS:

INDEPENDENT_QA_STATUS:
FROZEN_MANIFEST_REFERENCE:
RUNTIME_MUTATION_COUNT:

TERMINAL_STATUS:
PROVENANCE:
UNSUPPORTED_CLAIMS:
```

## Minimum acceptance

- [ ] Exact source identity and bytes were pinned before classification.
- [ ] Tested benign token-like identifiers/properties were accepted when their values/context were benign.
- [ ] Tested credential-shaped literal assignments failed closed.
- [ ] Tested private-key material failed closed.
- [ ] Tested explicit placeholders failed closed.
- [ ] Tested sensitive path/name rules remained enforced.
- [ ] Byte-fidelity, scope, carrier, and encoding checks remained deterministic.
- [ ] Independent QA re-read frozen evidence when the claim warranted it.
- [ ] Candidate or QA PASS was not treated as deployment or release authority.
- [ ] Remaining unknowns and unsupported claims are explicit.

## Interpretation

A useful receipt distinguishes at least three things:

1. **Identity** — what exact source bytes were evaluated.
2. **Classification** — which tested benign and sensitive classes were accepted or rejected.
3. **Authority boundary** — what the result does not authorize.

Do not broaden this receipt into claims of universal secret detection, malware detection, repository-wide safety, production readiness, or certification unless separate evidence supports those claims.

## Public-sharing boundary

Before publishing a completed receipt:

- remove credentials, private source, internal paths/hostnames, sensitive logs, customer data, and unnecessary private fingerprints;
- use synthetic examples where they teach the same lesson;
- confirm rights and provenance for any third-party material;
- keep claims within the verified test boundary.

Related material:

- [`../patterns/source-safety-gate-checklist.md`](../patterns/source-safety-gate-checklist.md)
- [`../case-studies/when-token-is-just-a-variable-name.md`](../case-studies/when-token-is-just-a-variable-name.md)
- [`../demos/source-safety-gate-evidence-walkthrough.md`](../demos/source-safety-gate-evidence-walkthrough.md)
