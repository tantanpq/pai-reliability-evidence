# Desired / Observed Control Surface — Bounded Evidence

## Why this evidence matters

Operator intent, actual runtime state, and whether a control is truly bound are different facts. Collapsing them into one mutable settings blob can make unsupported switches look live, hide drift, and create accidental two-way synchronization.

## Verified result

A bounded governed candidate wave reached terminal `DONE/PASS` across four control-surface cones while preserving these distinctions:

- desired operator policy remained explicit;
- observed/effective state was read back separately;
- every control carried an explicit binding state;
- drift remained visible instead of being silently auto-reconciled;
- reconciliation required an explicit choice such as `APPLY_DESIRED` or `ADOPT_OBSERVED`;
- each existing owner consumed or wrote only the fields it owned;
- the control surface itself did not become a scheduler, queue, database, claim authority, or second control plane.

Mixed binding states remained valid and were not promoted into false live claims.

## What was verified

Within the bounded candidate contract:

1. desired intent and observed state can be represented separately;
2. explicit binding states can distinguish writable/live controls from armed, observed-only, or unbound fields;
3. drift can be surfaced without silently rewriting operator intent;
4. reconciliation can remain an explicit owner-scoped action;
5. read-only control surfaces can remain useful before every write path is safely bound.

## What this does not prove

This result does **not** establish:

- that every control is live;
- that observed runtime state currently matches desired intent;
- universal configuration correctness;
- current production health;
- autonomous authority to apply settings;
- production readiness.

## Public provenance boundary

The public derivative excludes private controls, owners, source paths, host details, runtime values, credentials, raw logs, and proprietary implementation source.

The reusable rule is: **a truthful control surface shows desired intent, observed reality, binding state, and drift separately; it must not manufacture authority by pretending every visible field is an active switch**.
