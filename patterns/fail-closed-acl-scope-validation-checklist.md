# Fail-Closed ACL Scope Validation Checklist

Use this checklist when a component needs narrowly bounded filesystem permission changes.

## 1. Freeze the input

- Pin the candidate artifact by cryptographic hash.
- Separate candidate construction from independent QA.
- Require byte identity during QA.
- Record exactly which files are allowed to change.

## 2. Define the allowlist precisely

- Enumerate the exact path shapes that may receive permissions.
- Reject ancestor-only paths.
- Reject lookalike names.
- Reject reserved state, key, release, credential, or authority locations.
- Normalize paths before comparison.
- Treat traversal or ambiguous normalization as invalid.

## 3. Fail closed before effect

- Validate scope before any permission grant.
- Invalid scope must return a stable failure classification.
- Do not partially grant and then attempt cleanup.
- Do not broaden the allowed scope to make a test pass.

## 4. Prove bounded permission semantics

- Grant only to the intended active principal.
- Avoid inheritance or propagation beyond the required target unless explicitly proven necessary.
- Verify effective permission readback after the mocked or isolated apply.
- Repeat apply/readback to test idempotence.

## 5. Independent QA

QA should independently verify:

- source and artifact hash;
- frozen-byte identity;
- changed-file containment;
- syntax and unit/security tests;
- path normalization and traversal cases;
- every allowed path shape;
- forbidden reserved-path variants;
- fail-closed ordering;
- absence of live mutation.

## 6. Promotion boundary

Candidate QA is not live validation. Keep physical startup, deployment, or production activation as a separate, explicitly evidenced step.

## Claim discipline

Report only the verification stage actually completed. A passing candidate QA does not imply production security certification.
