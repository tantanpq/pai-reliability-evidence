# Demo: `UNKNOWN` Is Not `MISSING`

A short, synthetic walkthrough for demonstrating evidence-driven successor selection without exposing private system details.

## Setup

Suppose a system needs three capabilities for the next change:

| Capability | Current evidence |
|---|---|
| Admission path | live owner and current readback |
| Token estimator | candidate exists, current binding not verified |
| Recovery helper | referenced historically, current proof absent |

The lazy planner sees two blanks and creates two new components.

The evidence-driven route does not.

## Step 1 — classify

| Capability | Classification | Action |
|---|---|---|
| Admission path | `LIVE_OWNER` | reuse as-is |
| Token estimator | `READY_WITH_LIMITS` | verify current binding |
| Recovery helper | `UNKNOWN` | obtain current owner evidence |

## Step 2 — separate evidence gaps from build gaps

Neither unresolved row yet proves that implementation is missing.

So the eligible frontier contains read/binding checks, not replacement services.

## Step 3 — apply negative constraints

Before accepting the frontier, verify:

- no duplicate owner;
- no new scheduler or queue;
- no dependency install just to make discovery convenient;
- no production mutation;
- no broad external import; and
- no global gate added around unrelated work.

## Step 4 — freeze evidence

Record source freshness, classifications, successor reasons, and a content hash for the evidence bundle.

An independent verification should reproduce the recorded hashes before promotion.

## Step 5 — explain the result

The demo's key sentence is:

> Lack of current proof is a reason to investigate, not permission to invent a replacement.

That makes the decision legible to reviewers and keeps the architecture smaller.

## Boundaries

The table is synthetic. It contains no credentials, private paths, internal host data, proprietary source, or third-party copyrighted material.
