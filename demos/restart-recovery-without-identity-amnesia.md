# Restart Recovery Without Identity Amnesia

This synthetic walkthrough illustrates why a restart-safe workflow should restore the exact execution-attempt identity rather than minting a replacement.

No real infrastructure, private source, credentials, customer data, or production identifiers are used.

## Synthetic ownership record

```text
task_id: task-demo-17
claim_id: claim-demo-4
attempt_id: attempt-demo-A
expected_result: result-demo-v1
state: RUNNING
```

Persist this record, then simulate a worker restart.

## Case 1 — exact recovery

Recovery loads `attempt-demo-A` and completes using the same attempt identity.

Expected outcome:

```text
completion: ACCEPT
unlock_count: 1
```

## Case 2 — identical replay

Replay the same terminal result for `attempt-demo-A`.

Expected outcome:

```text
completion: IDEMPOTENT_REPLAY
unlock_count: 1
```

The downstream dependency must not be unlocked twice.

## Case 3 — conflicting replay

Keep `attempt-demo-A` but change the result identity/content.

Expected outcome:

```text
completion: REJECT_CONFLICT
unlock_count: 1
```

A conflicting result is not a second success.

## Case 4 — legacy record without attempt identity

Remove `attempt_id` before recovery.

Expected outcome:

```text
recovery: FAIL_CLOSED
reason: ATTEMPT_IDENTITY_MISSING
```

The recovery path should not invent a replacement attempt merely to keep moving.

## Case 5 — foreign attempt

Try completion using `attempt-demo-B` while ownership still records `attempt-demo-A`.

Expected outcome:

```text
completion: REJECT_FOREIGN_ATTEMPT
unlock_count: 1
```

## Takeaway

> Recovery may restore execution, but it must not invent execution identity.

This walkthrough demonstrates an evidence pattern only. It is not a production exactly-once guarantee or activation claim.
