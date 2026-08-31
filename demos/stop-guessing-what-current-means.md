# Stop Guessing What “Current” Means — Synthetic Walkthrough

This demo uses invented source IDs, hashes, Program names, and runtime values.

## Scenario

Three hints claim to describe the current phase:

```text
notes-latest.md        → PHASE_B
handoff-copy.md        → PHASE_C
canonical-pointer.json → PHASE_D
```

The bad approach is to choose the newest filename or whichever text appeared most recently in a chat.

## Step 1 — Declare authoritative sources

Use a small explicit manifest:

```text
SOURCE A
id: SOURCE_PROGRAM
expected_hash: abc123...
required: true

SOURCE B
id: SOURCE_CHECKPOINT
expected_hash: def456...
required: true
```

The filenames are irrelevant to precedence.

## Step 2 — Validate identity before interpretation

Read the sources and verify their expected identity/schema.

If both match, resolve the durable projection:

```json
{
  "program": "PROGRAM_X",
  "phase": "PHASE_D",
  "checkpoint": "CP_17",
  "status": "RESOLVED",
  "runtime_truth_required": true
}
```

## Step 3 — Corrupt one required source

Now make SOURCE B fail its expected hash check.

Do **not** fall back to the nearest filename or an older chat message.

```json
{
  "status": "SOURCE_CHECK_REQUIRED",
  "runtime_truth_required": true
}
```

A missing answer is safer than a fabricated authoritative answer.

## Step 4 — Keep volatile truth separate

Suppose the durable projection correctly resolves `PHASE_D`. It still cannot tell you whether a worker is healthy at this instant.

That requires a separate JIT runtime read:

```text
durable phase: PHASE_D
worker health: FETCH FROM CURRENT RUNTIME OWNER NOW
```

## Step 5 — Replay

Run the resolver again with identical validated inputs. The durable output should be identical.

## Useful rule

```text
PIN → VERIFY → RESOLVE → PROVENANCE
AND
VOLATILE TRUTH → READ JIT
```

Do not turn interpretation into a shadow control plane. Humans already have a remarkable talent for creating three sources of truth and naming all three “final.” Software does not need to join the hobby.

## Claim boundary

This synthetic walkthrough demonstrates a generic read-only source-resolution pattern. It does not expose private PAI internals or grant authority to change the resolved Program, phase, checkpoint, or runtime state.
