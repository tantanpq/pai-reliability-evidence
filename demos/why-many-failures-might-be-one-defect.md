# Why Many Failures Might Be One Defect — Synthetic Walkthrough

This demo uses invented names and data. It teaches occurrence deduplication and causal clustering without exposing private systems or PAI internals.

## Scenario

A synthetic deployment audit returns eight observations:

| Finding | Observation | Initial interpretation |
|---|---|---|
| F1 | Worker A cannot submit its scan result | transport failure |
| F2 | Worker B cannot submit its scan result | transport failure |
| F3 | Worker C cannot submit its scan result | transport failure |
| F4 | package manifest differs from reconstructed bytes | fidelity defect |
| F5 | the same package mismatch is reported by a second check | fidelity defect |
| F6 | an ownership label is ambiguous | low-confidence ownership finding |
| F7 | service X rejects a stale owner as expected | negative-control PASS |
| F8 | service Y reports a different stale-state symptom | separate lifecycle finding |

The bad approach creates eight tickets because eight lines exist. Computers are very good at counting lines. They remain tragically indifferent to whether the lines mean the same thing.

## Step 1 — Separate observations from defects

Keep all eight observations as evidence, but do not equate `8 observations = 8 defects`.

F7 is a successful negative control, not a defect. F6 is uncertain, not repair-ready.

## Step 2 — Deduplicate repeated occurrences

F1, F2, and F3 share the same failed transport invariant and the same owning seam. Preserve three occurrences for prevalence/coverage, but form one candidate causal cluster:

```text
C1 — RESULT_TRANSPORT_SEAM
occurrences: F1, F2, F3
maturity: REPAIR_READY (only if owner/scope/acceptance are bounded)
```

F4 and F5 are repeated evidence for the same byte-fidelity mismatch:

```text
C2 — ARTIFACT_FIDELITY
occurrences: F4, F5
maturity: REPAIR_READY
```

## Step 3 — Preserve uncertainty

F6 has insufficient evidence to identify the owning defect:

```text
C3 — OWNERSHIP_AMBIGUITY
occurrences: F6
maturity: NEEDS_DISCRIMINATION
```

Do not manufacture a repair task simply to make the dashboard look decisive.

## Step 4 — Keep distinct causal families distinct

F8 may mention stale state just as F7 does, but that does not make them the same defect. Similar words are not causal evidence.

```text
C4 — LIFECYCLE_STATE_SEAM
occurrences: F8
maturity: QUALIFIED_FINDING
```

## Result

The eight raw observations become:

- 4 causal clusters;
- 2 potentially repair-ready clusters;
- 1 cluster needing discrimination;
- 1 qualified finding;
- 1 negative-control PASS preserved at occurrence level.

No repair happens inside this demo.

## The useful rule

```text
COUNT OCCURRENCES FOR COVERAGE.
COUNT DEFECTS AT A JUSTIFIED CAUSAL BOUNDARY.
CREATE REPAIR WORK ONLY WHEN THE OWNER, SCOPE, EVIDENCE, AND ACCEPTANCE ARE BOUNDED.
```

## Safety and claim boundary

Use this method only as an evidence-structuring aid. Causal clustering can be wrong and must be challenged by direct evidence. This walkthrough does not grant authority to test, change, repair, or deploy any system.
