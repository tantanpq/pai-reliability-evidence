# Demo Walkthrough: Evidence-First ACL Scope Validation

This walkthrough demonstrates the assurance pattern without exposing private implementation details.

## 1. Start with the boundary

Show two conceptual classes:

- intended state-directory shapes;
- everything else, including reserved, nested, lookalike, ancestor-only, and traversal-adjacent variants.

The rule is simple: only the exact intended shapes are eligible.

## 2. Show fail-closed ordering

Explain that scope validation happens before any permission effect. An invalid target fails immediately rather than receiving a partial grant followed by cleanup.

## 3. Show negative-case testing

Present the verification categories:

- reserved state/key/release names;
- nested forbidden variants;
- lookalike state names;
- ancestor-only targets;
- normalization and traversal cases.

The point is to test what must *not* happen.

## 4. Show bounded effect semantics

Use an isolated or mocked grant/readback. Verify only the intended active principal receives the required permission and repeat the operation to check idempotence.

## 5. Freeze, then QA

Pin the candidate artifact by hash. Independent QA runs against those frozen bytes and checks hash identity, byte containment, negative cases, fail-closed ordering, and absence of live mutation.

## 6. Stop at the evidence boundary

End the demo at candidate QA. Do not imply physical startup, live deployment, or production certification unless separate terminal evidence exists.

## Demo takeaway

A reliable ACL change is not “the happy path worked.” It is “the allowed surface was exact, the forbidden surface stayed forbidden, the effect was bounded, and independent QA verified the frozen artifact.”
