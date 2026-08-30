# Demo walkthrough: evidence-first recoverability

A short, implementation-neutral walkthrough for explaining safe recovery classification.

## Scene 1 — Successful terminal evidence

Show a completed attempt with verified identity and successful terminal evidence. Classify it as **Success**. No further recovery action is implied.

## Scene 2 — Verified terminal failure

Change only the terminal outcome to an unsuccessful one while keeping evidence valid. Classify it as **Terminal task failure**. Emphasize that classification alone does not create a retry.

## Scene 3 — Technical failure with rollback proof

Show a bounded technical failure followed by readback proving restoration of the known-good state. Classify it as **Recoverable technical failure**. Any continuation still follows existing policy.

## Scene 4 — Ambiguous submit effect

Remove trustworthy completion evidence after the submit boundary. Classify it as **Ambiguous effect**. Demonstrate the key rule: reconcile the original effect identity before replay.

## Scene 5 — Invalid evidence

Corrupt or remove a required verification fact. Classify it as **Invalid evidence** and fail closed.

## Closing proof

The source pattern behind this walkthrough passed independent QA with source-integrity checks and a full **166/166** isolated test suite. The result was candidate-only; no live activation or new scheduler, queue, claim path, retry engine, or authority mechanism was introduced.
