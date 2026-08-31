# Source-Binding Integrity Checklist

Use this checklist when a durable pointer, source ID, or configuration reference must keep the same intended meaning across updates without silently accepting changed bytes.

This is a verification pattern. It does not grant authority to rewrite canonical sources, activate a candidate, deploy, or publish.

## 1. Bind identity and meaning separately

Record both the physical source identity and its semantic role:

```text
SEMANTIC_ROLE:
SOURCE_ID:
EXPECTED_FINGERPRINT:
EXPECTED_BYTES_OR_SIZE:
SCHEMA_OR_VERSION:
OWNER:
```

A pointer resolving successfully proves only that something exists at the reference. It does not prove the referenced material is the expected material.

## 2. Verify before semantic use

- [ ] Durable source ID is recorded.
- [ ] Expected fingerprint or equivalent immutable identity is recorded where available.
- [ ] Semantic role/reference is recorded separately from the physical pin.
- [ ] Consumer validates the observed source identity before semantic use.
- [ ] Required schema/version checks pass.
- [ ] Mismatch fails closed rather than silently rebinding meaning.

## 3. Surface drift explicitly

- [ ] Physical pin drift is detected.
- [ ] Semantic-reference drift is detected or ruled out independently.
- [ ] A changed pointer does not automatically inherit the old source's semantic trust.
- [ ] Drift status is visible as `MATCH`, `DRIFT`, or `UNKNOWN` rather than inferred from filename or presence.

## 4. Separate staging from activation

Use explicit lifecycle states such as:

```text
STAGED
ACTIVATED
REJECTED
```

- [ ] Staged candidate bytes are not described as live behavior.
- [ ] Activation requires the existing authorized owner/path.
- [ ] Post-activation readback verifies the active source binding.
- [ ] Presence is not treated as activation evidence.

## 5. Keep rollback bounded

- [ ] Prior source/pin identity is retained for rollback.
- [ ] Rollback restores the previous binding rather than mutating unrelated owners.
- [ ] Verification remains read-only unless an existing governed activation step separately authorizes a change.

## Minimal receipt

```text
SEMANTIC_ROLE:
SOURCE_ID:
EXPECTED_FINGERPRINT:
OBSERVED_FINGERPRINT:
EXPECTED_BYTES_OR_SIZE:
OBSERVED_BYTES_OR_SIZE:
BINDING_STATUS: MATCH | DRIFT | UNKNOWN
SEMANTIC_REFERENCE_STATUS: PRESERVED | CHANGED | UNKNOWN
CANDIDATE_STATUS: STAGED | ACTIVATED | REJECTED | NONE
ACTIVATION_EVIDENCE:
OWNER:
ROLLBACK_REF:
UNSUPPORTED_CLAIMS:
```

## Core rule

```text
POINTER EXISTS
≠ SOURCE IDENTITY VERIFIED
≠ SEMANTIC ROLE PRESERVED
≠ CANDIDATE ACTIVATED
```

## Claim boundary

Passing this checklist supports bounded source-binding/provenance evidence only. It does not establish universal supply-chain integrity, live activation, or authority to alter canonical sources.
