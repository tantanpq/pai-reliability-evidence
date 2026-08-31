# Why 99.9% Uptime Can Still Produce a False PASS

This synthetic walkthrough shows why an automation system may need a correctness error budget in addition to ordinary availability metrics.

No real infrastructure, credentials, customer data, private source, or production incident is used.

## Toy system

Assume a small automation pipeline:

```text
REQUEST
  -> CLAIM
  -> EXECUTE
  -> RESULT EVENT
  -> VERIFY
  -> RESOLVE
```

The service endpoint remains reachable throughout the example.

## Scenario A — availability-only view

Synthetic observations:

```text
requests served: 999 / 1000
endpoint availability: 99.9%
median latency: healthy
worker process: running
```

A conventional dashboard can reasonably look green.

Now add one fact:

```text
one execution completed
but its terminal Result Event was never recorded
```

The process is available, but the system can no longer reconstruct whether the work completed correctly.

## Scenario B — correctness budget

Define a separate hard-zero class:

```text
LOST_TERMINAL_RESULT_EVIDENCE allowed = 0
```

The same observation now produces:

```text
availability budget: healthy
correctness budget: EXHAUSTED
incident state: OPEN
```

This does not mean the whole platform must stop. It means the affected correctness cone cannot be represented as healthy or resolved.

## Evidence lifecycle

A bounded recovery path might require:

```text
DETECTED
  -> OWNED
  -> REPAIR_RELEASED
  -> EVIDENCE_VERIFIED
  -> CURRENT_STATE_REREAD
  -> RESOLVED
  -> REGRESSION_WINDOW_CLOSED
```

Two important rules follow:

1. elapsed time alone cannot close the incident;
2. a green availability metric cannot substitute for missing terminal evidence.

## Falsification checks

Try these synthetic mutations:

- duplicate an external effect while keeping the endpoint responsive;
- replay stale work after a newer owner exists;
- mark a result PASS before its evidence is readable;
- restore a previous version but skip the restoration reread.

A useful correctness budget should reject each case even if uptime remains excellent.

## Takeaway

> Reliability is not only “did the service stay up?” It is also “can the system prove that important work was not duplicated, lost, replayed, fabricated, or left unverified?”

This walkthrough is an educational pattern, not a production SLO prescription or certification claim.
