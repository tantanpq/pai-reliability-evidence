# Verified Reuse-Freeze Checklist

Use this checklist before turning an incomplete capability picture into new build work.

## 1. Freeze current evidence

- Read the controlling semantic sources.
- Read volatile runtime state only from the current authority surface.
- Separate terminal evidence from planned, queued, materialized, or running work.
- Record freshness and provenance.

## 2. Classify reuse before build

For every relevant existing asset, choose the strongest evidence-supported state:

- `LIVE_OWNER`
- `LIVE_TOOL`
- `QUALIFIED`
- `READY_WITH_LIMITS`
- `OPTIONAL`
- `UNKNOWN`

Do not promote a candidate merely because it exists in a catalog.

## 3. Keep unknowns honest

`UNKNOWN` means current evidence is insufficient.

It does **not** mean:

- missing;
- broken;
- obsolete; or
- permission to create a replacement.

Resolve the evidence gap before opening a build gap.

## 4. Prove the gap

A new implementation is eligible only when:

1. existing candidates were checked;
2. their insufficiency is evidenced;
3. the missing behavior is named precisely; and
4. the new work does not duplicate an existing owner or authority.

## 5. Compile the smallest successor frontier

Prefer bounded reads, binding checks, or isolated tests when they can resolve uncertainty.

Do not pre-materialize a large downstream chain from assumptions.

## 6. Preserve ownership and write safety

- one writer per mutable scope;
- retain the existing integration owner;
- keep optional assurance tooling bypassable unless the exact risk requires it;
- never turn a checklist into a second planner or gatekeeper.

## 7. Bound capability and cost claims

- distinguish `CAN_DO`, `SHOULD_DO`, and `COST_TO_DO`;
- preserve unknown quotas or provider limits as unknown;
- do not install dependencies solely to satisfy discovery.

## 8. Verify negative space

Explicitly confirm what the run did **not** mutate or create.

Useful checks include:

- no new control plane;
- no unauthorized runtime mutation;
- no destructive cleanup;
- no broad import;
- no silent authority expansion.

## 9. Content-address the evidence

Hash the evidence bundle and verify the hashes independently before promotion or publication.

## 10. Independent challenge

A second method or reviewer should challenge:

- duplicate ownership;
- hidden context/token amplification;
- ambient tool or authority leakage;
- one-writer conflicts; and
- rollback or bypass gaps.

The challenge is evidence, not a permanent global gate.
