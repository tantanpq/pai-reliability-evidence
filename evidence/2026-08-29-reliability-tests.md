# Reliability Evidence Snapshot — 2026-08-29

## Scope

This snapshot records verified test outcomes selected for public sharing. It intentionally omits private implementation details and raw internal logs.

## Result A — Core candidate test suite

Observed test summary:

- tests: 35
- pass: 35
- fail: 0
- cancelled: 0
- skipped: 0
- todo: 0

The run included checks covering authority selection, lifecycle truth precedence, claim identity, HANDOFF handling, durable learning journal behavior, sanitized read-only lifecycle projection, reconciliation behavior, admission fixtures, bounded SQLite lock handling, duplicate-key coalescing, and worker-proxy error mapping.

## Result B — Focused SQLite lock-budget checks

Observed test summary:

- tests: 3
- pass: 3
- fail: 0
- cancelled: 0
- skipped: 0
- todo: 0

The three focused checks covered:

1. A bounded local SQLite lock hold completing without a retryable busy failure.
2. A near-budget local projection hold being admitted with connection-local busy timeout behavior.
3. A lock beyond the local budget failing closed after the bounded wait.

## Interpretation boundary

These are test-run results, not a production certification. They support only the claim that the captured checks passed in the recorded runs.

## Public-safety filtering

Excluded from this publication:

- credentials or secrets;
- private hostnames, paths, or operational topology;
- proprietary source code;
- raw sensitive logs;
- unsupported production claims;
- third-party copyrighted material not required to state the result.
