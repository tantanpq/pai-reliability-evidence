# The Test Passed Because the Dependency Was Handed to It

## Situation

A candidate looked close to integration-ready. Its helper-level logic behaved correctly when supplied a reader dependency, and the surrounding focused and inherited tests passed.

## Finding

Independent QA traced the selected runtime composition instead of stopping at the harness. The real normal path had no accepted, configured provider reachable for the required observation.

The test had proved the adapter. It had not proved the system composition.

## Decision

Preserve the negative integration verdict.

Require evidence that:

1. the provider is accepted/current;
2. the selected runtime actually wires it;
3. the normal entrypoint can reach it;
4. missing-provider behavior fails closed;
5. representative accepted observations traverse the composed path.

## Why it matters

Dependency injection is useful for testing semantics, but it can also hide a missing production dependency. Treating injected success as deployment evidence can produce fabricated capacity, health, or progress claims from a component that the live path cannot obtain.

The reusable lesson is simple:

> Prove the dependency is reachable, not merely injectable.

## Claim boundary

This case preserves a bounded independent-QA failure. It does not claim a production outage, a general architectural defect, or successful correction after the rejected candidate.

## Public-safety note

The case contains no private topology, source code, credentials, hostnames, internal paths, sensitive logs, operational identifiers, fingerprints, or third-party copyrighted material.
