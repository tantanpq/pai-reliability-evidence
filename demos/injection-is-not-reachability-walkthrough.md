# Synthetic Walkthrough: Injection Is Not Reachability

This walkthrough uses synthetic components only. It demonstrates why passing dependency-injection tests does not establish that a real application can reach the dependency.

## Setup

Create:

- an adapter `A` that accepts a reader function;
- a unit/integration-style test that injects a perfect reader;
- an application entrypoint `E` whose provider wiring is intentionally absent;
- a second composition where an accepted provider is wired explicitly.

## Walkthrough

### 1. Pass the injected test

Inject a reader that returns a bounded observation. The adapter behaves correctly and the test passes.

Record only the claim this proves: **adapter semantics with a supplied dependency**.

### 2. Run the real entrypoint

Invoke `E` without provider wiring. The expected result is truthful `UNKNOWN` or another defined fail-closed state.

If the entrypoint reports a healthy value anyway, the system is fabricating evidence.

### 3. Compare the two claims

| Evidence | What it proves |
|---|---|
| Injected reader test passes | Adapter can consume the contract |
| Provider is accepted | Provider itself passed its gate |
| Provider is wired | Selected composition references it |
| Real entrypoint reaches it | Runtime path can obtain the dependency |

No single row substitutes for the others.

### 4. Wire the accepted provider

Add the provider explicitly to the synthetic composition and rerun the real entrypoint.

### 5. Exercise both boundaries

Test:

- provider absent -> fail closed;
- provider present with representative value -> value traverses the real path;
- unaccepted provider -> reject;
- helper injection only -> no integration-readiness claim.

## Core lesson

A harness can prove logic around a dependency while hiding that the dependency is absent from the selected system. Integration evidence must include real-path reachability.

## Boundary

This is an educational fixture. It does not represent private runtime topology or prove production readiness.
