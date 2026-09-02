# Checklist: Derived Current-Picture Truth Boundary

## Source and freshness
- [ ] Every displayed claim has source identity and last-verified time.
- [ ] VERIFIED, STALE, CONTRADICTED, inferred, and missing states are distinguishable.
- [ ] Conflicts remain source-traceable instead of being flattened into one answer.

## Access and provenance
- [ ] Principal, purpose, and data class are checked before read exposure.
- [ ] Provenance and temporal-state validation fail closed.
- [ ] The reader has no path that promotes the derived view into canonical truth.

## Projection integrity
- [ ] The view is explicitly labeled derived/non-canonical.
- [ ] A correction recomputes the projection rather than rewriting the source to match the summary.
- [ ] Persisted projections use only an existing governed writer seam.
- [ ] A matching projection-hash receipt is required before accepting persisted output.
- [ ] Close/compaction keeps conflict and reopen pointers available.

## Evidence ceiling
Passing this checklist supports a bounded projection-integrity claim only. It does not establish production readiness, immutable-release admission, or source-mutation authority.
