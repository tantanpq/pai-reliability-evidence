# Community Skill Recipes

These are compact, reusable assurance skills derived from public-safe PAI reliability evidence. They are not executable PAI internals and do not grant deployment, production, or security authority.

Each skill has a narrow purpose, a minimal input contract, and a bounded output.

## Skill 1 — Evidence Boundary Review

**Use when:** a test, release, incident report, or dashboard says something is green and you need to know what that green result actually proves.

**Inputs:**

- claim being made;
- tests/evidence available;
- terminal status;
- relevant readback/provenance.

**Procedure:**

1. Rewrite the claim in one bounded sentence.
2. Separate observed facts from inference.
3. Mark `planned`, `running`, `PASS`, `LIVE`, and `DONE` separately.
4. Identify evidence produced by the same component versus independent evidence.
5. List unsupported claims explicitly.

**Output:** a claim/evidence table plus the smallest missing proof.

---

## Skill 2 — Verify Bytes Before Trusting Labels

**Use when:** a build, package, backup, restore, or promotion is identified by a mutable name or human-readable label.

**Inputs:**

- exact source/artifact identity;
- expected manifest/digest;
- reconstructed or consumed bytes.

**Procedure:**

1. Pin exact input identity.
2. Re-read the bytes from the consumer side.
3. Compare manifest/digest or exact byte content.
4. Test encoding/BOM or other transport edge cases when relevant.
5. Fail closed on mismatch rather than accepting a matching label.

**Output:** byte-fidelity receipt and unsupported boundaries.

---

## Skill 3 — Canary-to-Soak Continuity Check

**Use when:** a cutover or new owner passes an initial canary.

**Inputs:**

- intended owner;
- previous competing owner;
- bounded observation window;
- authoritative read path;
- targeted regression checks.

**Procedure:**

1. Confirm the canary effect.
2. Confirm the previous owner cannot compete.
3. Repeat authoritative ownership/health observations for the bounded window.
4. Check that active work does not hide a race.
5. Re-run targeted regressions.
6. Independently re-read the runtime evidence when the claim warrants it.

**Output:** bounded continuity result, not an HA/SLO claim.

---

## Skill 4 — Source Safety Gate Review

**Use when:** source packaging or build preparation needs to reject sensitive material without blocking benign token-like identifiers.

**Inputs:**

- pinned source bytes;
- path/name policy;
- content policy;
- positive and negative fixtures.

**Procedure:**

1. Separate path/name rules from semantic content rules.
2. Test benign identifiers that contain security-looking words.
3. Test credential-shaped literals, private-key fixtures, and explicit placeholders.
4. Preserve path, scope, carrier, encoding, and byte-fidelity checks.
5. Reject a broad bypass such as “allow every token-like name.”

**Output:** classification receipt plus false-positive/false-negative boundary.

---

## Skill 5 — Failure Supersession Review

**Use when:** an earlier attempt failed and a later attempt passes.

**Inputs:**

- earlier terminal failure;
- later terminal result;
- acceptance boundary;
- evidence that changed between attempts.

**Procedure:**

1. Keep the original failure visible.
2. Identify whether the later run addresses the same acceptance boundary.
3. State what evidence changed.
4. Mark the earlier failure superseded only when the later evidence actually closes it.
5. Preserve unrelated unresolved failures.

**Output:** explicit failure-to-successor lineage rather than a rewritten history.

---

## Skill 6 — Public Evidence Sanitization

**Use when:** a verified private result may have reusable public value.

**Inputs:**

- verified result;
- provenance;
- private/public boundary;
- third-party rights information.

**Procedure:**

1. Extract the reusable lesson.
2. Remove private source, credentials, internal paths/hosts, sensitive logs, customer data, and unnecessary fingerprints.
3. Replace demonstrations with synthetic fixtures where possible.
4. Check license and third-party provenance.
5. Bound claims to the verified evidence.
6. Confirm that Protected Core material is not required for the public artifact to be useful.

**Output:** public-safe evidence, checklist, case study, demo, or workflow candidate.

---

## Skill 7 — Audit Finding Clustering

**Use when:** an audit produces many repeated observations and you need to distinguish coverage volume from actual defect count before repair work exists.

**Inputs:**

- occurrence-level findings;
- failed/questioned invariant;
- evidence references;
- coverage state;
- candidate owner and mutable scope where known.

**Procedure:**

1. Preserve every raw occurrence and its coverage state.
2. Deduplicate exact repeats without deleting prevalence evidence.
3. Separate `NOT_DONE`, `UNKNOWN`, and `INCONCLUSIVE` coverage from proven target defects.
4. Cluster distinct symptoms only when causal/root seam, owner, invariant, or mutable-scope evidence supports the merge.
5. Keep similar text in separate clusters when causal lineage differs.
6. Grade clusters as `QUALIFIED_FINDING`, `NEEDS_DISCRIMINATION`, or `REPAIR_READY` rather than turning every observation into a task.
7. Apply prioritization/caps after clustering so duplicate observations do not crowd out distinct defects.
8. Admit repair only through the existing governed owner with bounded scope, acceptance, and rollback.

**Output:** an occurrence-to-cluster map, maturity classification, remaining uncertainty, and the smallest justified repair boundary.

See [`../patterns/audit-to-repair-clustering-checklist.md`](../patterns/audit-to-repair-clustering-checklist.md) for the longer checklist.

## Using these skills together

A common sequence is:

```text
Evidence Boundary Review
→ Verify exact input/output identity
→ Run decisive positive/negative checks
→ Cluster repeated audit evidence where needed
→ Add independent review where it materially changes confidence
→ Preserve failure/supersession truth
→ Sanitize the reusable lesson for public sharing
```

For a longer end-to-end public workflow, see `workflows/community-assurance-baseline.md`.
