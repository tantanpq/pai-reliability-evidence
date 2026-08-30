# Case Study: Deterministic Two-Node Failover Simulation

## Problem

Failover logic can appear healthy while still allowing unsafe takeover, stale-writer mutation, ambiguous lease boundaries, or non-deterministic contention. A bounded simulator was used to test these failure modes without enabling production failover.

## Verification approach

The verified run exercised 21 scenarios, including both takeover directions, delayed and missing heartbeats, exact lease-expiry boundaries, stale-owner return, simultaneous takeover attempts, unavailable shared state, unsafe clock conditions, duplicate terminal events, provenance mismatch, fencing monotonicity, and deterministic replay.

## Result

**21/21 scenarios passed.** The verified behavior maintained one mutable owner, advanced fencing tokens monotonically, rejected stale mutation, blocked takeover when a terminal result already existed, and failed closed when ordering or authority state was unsafe.

## Design lesson

A useful failover test should separate *liveness signals* from *authority*. Heartbeat loss is evidence that a node may be unavailable; it is not sufficient authority to mutate. Safe takeover needs explicit lease expiry, provenance revalidation, deterministic contender ordering, atomic fencing, and stale-owner rejection.

## Product value

The result is reusable as an assurance pattern for systems that need to demonstrate bounded single-writer failover behavior before any live activation. It is especially useful as a pre-production review artifact because the simulator can test dangerous edge cases without creating a second live authority path.

## Limits

The verified result was an isolated simulation with production activation disabled. It does not establish live availability, disaster-recovery performance, or universal split-brain resistance.

## Public-safety boundary

Private source code, host identities, credentials, internal paths, raw logs, and sensitive topology details are intentionally omitted.
