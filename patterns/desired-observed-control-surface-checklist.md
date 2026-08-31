# Desired / Observed Control Surface Checklist

Use this checklist when building an operator-facing settings or control surface over systems whose actual runtime state is owned elsewhere.

The control surface should expose truth and route writes. It should not become another scheduler, queue, database, claim authority, or control plane.

## 1. Separate intent from reality

- [ ] Desired operator intent is represented separately from observed/effective runtime state.
- [ ] Observed values carry readback/freshness context where relevant.
- [ ] An observed value is not silently copied into desired policy.
- [ ] A desired value is not displayed as effective until readback proves the effect.

## 2. Give every control a binding state

Use explicit states such as:

```text
LIVE_BOUND
ARMED
OBSERVED_ONLY
UNBOUND
```

- [ ] `UNBOUND` controls cannot be presented as active switches.
- [ ] `OBSERVED_ONLY` values are visibly non-writable.
- [ ] `ARMED` does not imply live/effective.
- [ ] `LIVE_BOUND` has a known owner and write/readback path.

## 3. Surface drift

- [ ] Desired and observed mismatch is visible.
- [ ] Drift is timestamped or readback-scoped where useful.
- [ ] No automatic two-way sync silently rewrites desired intent.
- [ ] Missing or invalid policy fails toward a known-safe/known-good behavior rather than guessing.

## 4. Make reconciliation explicit

A useful model is:

```text
APPLY_DESIRED
or
ADOPT_OBSERVED
```

- [ ] Reconciliation direction is explicit.
- [ ] The selected action is scoped to the relevant field/component.
- [ ] Every write routes through the existing owner of that mutable scope.
- [ ] One writer is preserved per mutable scope.
- [ ] Authority/capacity/safety clamps remain external truth rather than editable UI fiction.

## 5. Keep rollback narrow

- [ ] Rollback targets the smallest changed policy, binding, or component.
- [ ] Unrelated owners are not rewritten during reconciliation.
- [ ] A read-only UI may ship before unsafe write controls are bound.

## Minimal record

```text
CONTROL_NAME:
DESIRED_VALUE:
OBSERVED_VALUE:
EFFECTIVE_VALUE:
BINDING_STATE:
DRIFT_STATE:
OWNER:
LAST_READBACK:
WRITE_PATH:
ROLLBACK:
CLAIM_BOUNDARY:
```

## Claim boundary

Passing this checklist supports bounded control-surface truthfulness. It does not prove every control is live, current runtime health, configuration correctness, or authority to apply settings.
