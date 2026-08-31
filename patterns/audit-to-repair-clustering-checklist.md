# Audit-to-Repair Clustering Checklist

Use this checklist when an audit produces many observations and you need to decide which evidence represents repeated occurrences, distinct defects, unresolved ambiguity, or bounded repair candidates.

This pattern is evidence-first. It does not grant repair, deployment, scheduling, claim, or publication authority.

## 1. Freeze the audit boundary

- [ ] The audited source/revision, configuration, environment class, and evidence scope are pinned where relevant.
- [ ] Scan work is read-only or otherwise explicitly bounded.
- [ ] Scan completion and target-system correctness are tracked as different claims.

## 2. Preserve occurrence-level evidence

For every observation, retain enough structure to distinguish it from inference:

- [ ] source or evidence reference;
- [ ] failed or questioned invariant;
- [ ] observed symptom;
- [ ] bounded scope;
- [ ] candidate owner, if known;
- [ ] confidence or uncertainty state.

Do not turn `NOT_DONE`, `UNKNOWN`, or `INCONCLUSIVE` coverage into a proven target defect without additional evidence.

## 3. Deduplicate exact repeats

- [ ] Exact repeated observations are occurrence-deduped.
- [ ] Repeated worker, host, file, or log count is not treated as independent defect count by itself.
- [ ] The original occurrence count remains available for coverage and prevalence analysis.

## 4. Cluster by causal boundary

Group observations only when evidence supports a shared causal lineage. Useful dimensions include:

- root or owning seam;
- failed invariant;
- mutable scope;
- owner boundary;
- state transition;
- causal family.

- [ ] Similar text alone is not sufficient to merge clusters.
- [ ] The same filename or path appearing in separate causal families does not force a collision.
- [ ] Different symptoms may share one cluster only when the evidence supports one owning cause.

## 5. Keep severity and confidence bounded

- [ ] Cluster severity is derived from supported evidence, not multiplied by occurrence count.
- [ ] Low-confidence clusters remain informational or require discrimination.
- [ ] Caps or prioritization rules are applied **after** clustering so duplicates do not consume the queue unfairly.

A useful maturity vocabulary is:

```text
QUALIFIED_FINDING
→ NEEDS_DISCRIMINATION
→ REPAIR_READY
```

The labels are descriptive, not execution authority.

## 6. Admit repair only at a bounded acceptance boundary

Before calling a cluster repair-ready, verify that the following are sufficiently clear:

- [ ] owning defect/seam;
- [ ] mutable scope;
- [ ] evidence supporting the causal hypothesis;
- [ ] acceptance checks;
- [ ] rollback or safe-failure boundary where applicable;
- [ ] one writer for the mutable scope.

Many findings from one root cause should not become many competing repair tasks.

## 7. Preserve audit/repair separation

- [ ] The audit does not silently mutate the target system.
- [ ] Repair authority remains with the existing governed owner/path.
- [ ] A post-repair claim requires a new Result/readback and, where material, independent verification.
- [ ] Earlier failed or incomplete coverage remains visible after a later repair.

## Minimal receipt

```text
AUDIT_BOUNDARY:
RAW_OCCURRENCES:
DEDUPED_OCCURRENCES:
CAUSAL_CLUSTERS:
QUALIFIED_FINDINGS:
NEEDS_DISCRIMINATION:
REPAIR_READY:
NOT_DONE_OR_UNKNOWN_COVERAGE:
CLUSTERING_EVIDENCE:
REPAIR_AUTHORITY: NONE | <existing owner>
UNSUPPORTED_CLAIMS:
```

## Claim boundary

This checklist helps structure evidence and repair admission. It does not guarantee correct root-cause inference, eliminate the need for engineering judgment, or certify production readiness.
