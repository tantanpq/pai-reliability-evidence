# Composition Reachability — Verified Negative Evidence

## Scope

This public snapshot summarizes a bounded independent-QA failure where helper and injected-dependency tests passed, but the stronger integration claim did not. The description is sanitized and contains no private topology, source, credentials, logs, internal identifiers, or fingerprints.

## Verified outcome

A candidate harness correctly demonstrated fail-closed `UNKNOWN` behavior and propagated bounded observations when a reader dependency was injected. Focused and inherited tests passed.

Independent QA then traced the actual selected composition and found that the normal runtime path had no accepted, configured, reachable provider for the required observation. The helper semantics were valid; the integration-readiness claim was not.

The accepted result was therefore **FAIL / not integration-ready**, with no live mutation.

## Assurance pattern

Integration evidence has at least two separate obligations:

```text
semantic correctness
  + accepted provider
  + real composition wiring
  + entrypoint reachability
  = bounded integration evidence
```

An injected test double can prove the first term while proving nothing about the remaining three.

## What to verify

- pin the actual selected runtime/release identity;
- name the required provider/observation contract explicitly;
- verify that the provider itself is accepted/current;
- prove configuration and wiring in the selected composition;
- execute the real normal entrypoint, not only helper functions;
- exercise missing-provider fail-closed behavior;
- exercise representative accepted observations through the composed path;
- reject hidden dependencies on unaccepted candidate material.

## Why it matters

Without a reachability check, a clean test suite can create synthetic integration confidence. The system may know how to consume a dependency that production can never obtain.

## Claim boundary

This evidence supports a bounded composition/reachability assurance pattern and preserves the negative QA verdict. It does **not** prove a production outage, general platform failure, or production readiness after correction.

## Publication safety

No credentials, private paths, host identifiers, runtime endpoints, proprietary source, sensitive logs, internal hashes, or third-party copyrighted material are included.
