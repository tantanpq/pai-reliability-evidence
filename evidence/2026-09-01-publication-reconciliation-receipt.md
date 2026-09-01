# Publication Reconciliation Receipt — 2026-09-01

Status: `ACCEPTED_AS_PUBLISHED / CATALOG_RECONCILED`

## Scope

This receipt reconciles publication state for exactly eight non-code files that were already public on `main` before this reconciliation commit. A scope-specific repository-owner disposition accepted this existing eight-file set and authorized one reconciliation commit updating `CATALOG.md` plus this receipt.

This receipt does **not** authorize additional publication, releases, products, services, credentials, pricing, or broader disclosure. It does not change any technical PASS/FAIL/candidate/UNKNOWN verdict inside the accepted files.

Pre-reconciliation `main` head: `3fae17fc888de35ae235024b1eeee20276531802`

Pre-reconciliation `CATALOG.md` blob: `822be08d44adaa3bc9eb890e9f31097c69a93e8a`

## Accepted existing files

| Proof class | Public file | Blob SHA | Origin commit |
|---|---|---|---|
| Deterministic resident recovery | `evidence/2026-08-31-deterministic-resident-recovery.md` | `acc948a15775516d33ebc3669e28f587a039a7ef` | `ffb71cf8ae63fe9cda0539c4d1f68e1c53cf4eed` |
| Deterministic resident recovery | `patterns/deterministic-stale-ownership-recovery-checklist.md` | `0f5ca4b03edb0820eb63a6e776ed0c00743242eb` | `1d7d60a32e9327dceba41a912beb46732687d3bc` |
| Deterministic resident recovery | `case-studies/recover-the-claim-not-the-fiction.md` | `57c57e5d4822d531e4320f8afd36d518f93789e9` | `85d4a5e678e2ab93b335c368f38682694e54fee9` |
| Deterministic resident recovery | `demos/stale-task-claim-recovery-walkthrough.md` | `fb6ba94635566a196d6e6606a333a80c8f59582a` | `acdb5082a3161e8f0a5ea47b70a63c8666e44201` |
| Composition reachability | `evidence/2026-08-31-composition-reachability.md` | `cecd892655fe634874187641e15f483a30ec97a6` | `e24b9c735ea4f43ca76e9745204e58de99c49212` |
| Composition reachability | `patterns/composition-reachability-checklist.md` | `69ee165aa1b82db39dc5dcde92123d70cb4c4a78` | `6728739a0337439572d0f28719d0384d0a8c35cf` |
| Composition reachability | `case-studies/the-test-passed-because-the-dependency-was-handed-to-it.md` | `2b3191caac07752aac794c5f6e901467941c0c66` | `bd29ad4d91a3bbc94f707a2afa0307c0302a8db5` |
| Composition reachability | `demos/injection-is-not-reachability-walkthrough.md` | `97a5c46f24cef9dc7af2f0ba779da1693f05487d` | `3fae17fc888de35ae235024b1eeee20276531802` |

## Readback semantics

The blob SHAs above identify the exact public bytes observed at the pre-reconciliation head. The origin commit SHAs identify the commits that introduced those files. This receipt records publication provenance; it does not promote bounded evidence into production readiness, certification, universal correctness, or a broader authority claim.

GitHub reports the pre-reconciliation head commit as `unsigned`. This receipt therefore relies on Git object identity and repository readback, not signed-commit provenance.

## Public-safety boundary

This reconciliation metadata contains public repository paths, Git object identifiers, and bounded publication-state statements only. It intentionally excludes credentials, private PAI implementation or authority internals, host/filesystem details, sensitive logs, customer data, proprietary source, and third-party copyrighted material not cleared for publication.

Licensing and publication boundaries remain governed by [`LICENSE.md`](../LICENSE.md), [`PROVENANCE.md`](../PROVENANCE.md), and [`OPEN_FOUNDATION.md`](../OPEN_FOUNDATION.md).

## Non-self-reference rule

The reconciliation commit SHA and the post-commit blob SHAs for `CATALOG.md` and this receipt are not embedded here because doing so would make the receipt self-referential. They are established by repository readback after the commit.
