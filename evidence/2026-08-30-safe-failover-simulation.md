# Safe Failover Simulation Evidence — 2026-08-30

## Scope

Sanitized summary of a verified deterministic two-node failover simulation result captured on 2026-08-29.

## Verified result

- Test summary: **21/21 passed**.
- The simulator was isolated from production activation, credentials, scheduler integration, and continuous auto-claim behavior.
- Takeover preserved a single mutable owner and advanced a strictly monotonic fencing token.
- A delayed or missing heartbeat alone was insufficient to take over an active lease.
- Takeover required strict lease expiry plus established ordering and provenance checks.
- Existing terminal results blocked takeover, and duplicate result events reconciled idempotently.
- Provenance mismatch, unavailable shared state, and unsafe clock conditions failed closed.
- A returning stale owner could not resume mutation with its old fencing token.
- Equivalent repeated simulations produced deterministic evidence.

## What this proves

The captured simulation exercised failover safety properties including single-writer ownership, fencing, strict expiry, stale-owner rejection, terminal-result reconciliation, provenance checks, and fail-closed behavior.

## What this does not prove

This is **simulation evidence**, not proof of live production failover, availability, disaster recovery, or zero split-brain risk in every environment. Production activation remained disabled in the verified result.

## Publication filtering

This public summary excludes private source code, internal host identities, credentials, filesystem paths, operational topology, raw logs, and implementation-specific secrets. No third-party copyrighted material is included.
