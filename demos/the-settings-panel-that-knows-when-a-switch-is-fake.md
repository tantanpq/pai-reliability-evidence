# The Settings Panel That Knows When a Switch Is Fake — Synthetic Walkthrough

This walkthrough uses invented controls, owners, and values.

## Scenario

A synthetic operator panel shows two controls:

| Control | Desired | Observed | Reality |
|---|---:|---:|---|
| `auto_resume` | ON | OFF | write path exists |
| `fast_mode` | ON | UNKNOWN | no write binding exists |

The bad UI renders both as ordinary active switches. One of them is not actually connected to anything.

## Step 1 — Separate desired and observed

Represent intent and runtime readback independently:

```text
auto_resume.desired  = ON
auto_resume.observed = OFF

fast_mode.desired     = ON
fast_mode.observed    = UNKNOWN
```

Do not let runtime readback silently rewrite operator intent.

## Step 2 — Add binding state

```text
auto_resume.binding = LIVE_BOUND
fast_mode.binding    = UNBOUND
```

Now the UI can tell the truth:

- `auto_resume` is a real bound control with drift.
- `fast_mode` is an intent field without an active write path.

The unbound control should be visibly disabled rather than theatrically clickable.

## Step 3 — Surface drift

```text
auto_resume:
  desired: ON
  observed: OFF
  drift: YES
```

Nothing is automatically overwritten.

## Step 4 — Reconcile explicitly

For `auto_resume`, the operator chooses one direction:

```text
APPLY_DESIRED  # ask existing owner to make runtime ON
```

or:

```text
ADOPT_OBSERVED # change desired intent to OFF
```

The control surface itself does not bypass the owning component.

## Step 5 — Read back before claiming effect

After `APPLY_DESIRED`, read runtime state again:

```text
desired: ON
observed: ON
binding: LIVE_BOUND
drift: NO
```

Only now is the effective-state claim supported.

## Useful rule

```text
VISIBLE CONTROL ≠ BOUND CONTROL ≠ EFFECTIVE STATE
```

A settings panel earns trust by displaying unsupported or drifting states accurately, not by making every rectangle look powerful.

## Claim boundary

This synthetic demo teaches desired/observed separation and binding-state truth. It grants no authority to modify real systems and does not establish production health or configuration correctness.
