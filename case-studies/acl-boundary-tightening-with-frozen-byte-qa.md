# Case Study: Tightening an ACL Boundary Without Broadening Authority

## Problem

A filesystem permission helper needed to support a legitimate state directory while preventing broader or ambiguous paths from becoming grant targets. The main risk was not whether one happy-path grant worked. It was whether nearby path variants could slip through the same boundary.

## Approach

The repair was kept candidate-only and bounded:

1. narrow the accepted path shapes to the intended state locations;
2. reject reserved state, key, and release variants before effect;
3. preserve unrelated candidate files byte-for-byte;
4. exercise negative path cases as first-class tests;
5. freeze the candidate artifact by hash;
6. send the frozen bytes to independent security QA;
7. prohibit live ACL, service, release, key, database, fencing, or authority changes during QA.

## Evidence

Candidate verification reported **3/3 syntax checks** and **4/4 unit/security checks**, plus negative cases for reserved, nested, lookalike, and ancestor-only path shapes. An isolated mocked apply/readback passed twice.

The frozen archive hash was rechecked before publication and matched its pinned value.

Independent QA later reached **DONE / PASS** under a contract requiring exact artifact identity, byte preservation, containment, normalization/traversal coverage, exact allowed paths, forbidden variants, fail-closed ordering, bounded principal permissions, and zero live mutation.

## Result

The useful outcome is a reusable assurance pattern: permission-boundary repairs should be proven against the *negative space* around the allowlist, not merely the intended path.

## What this does not prove

The evidence does not claim physical startup validation, live deployment, production certification, or universal security correctness. Those require separate terminal evidence.
