# Assurance Proof Pattern Pack

A compact public-safe distillation of reusable proof patterns from internally verified DONE handoffs. Raw logs, private implementation details, and model output are excluded.

## 1. Source integrity

Use when a result depends on reading the right source rather than merely finding a similarly named artifact.

- bind the expected source explicitly;
- reread the selected source before making the terminal claim;
- test missing and invalid-source behavior;
- separate observation evidence from authority evidence;
- freeze or hash the manifest used for verification.

## 2. Lifecycle recovery

Use when work may be interrupted, released, restarted, or replayed.

- distinguish ownerless work from actively protected work;
- preserve restart provenance;
- make terminal/replay handling idempotent;
- reject malformed recovery evidence safely;
- verify that recovery does not create a duplicate mutable owner.

## 3. Authority freshness

Use before accepting an authority-bearing action after delay, restart, or handoff.

- run freshness preflight before mutation;
- refresh through the accepted signed path;
- verify current holder and fencing state;
- make repeated refresh/replay safe and idempotent;
- fail closed when freshness cannot be established.

## 4. Timeout discipline

Use when execution duration is variable or externally constrained.

- do not invent arbitrary default timeouts when the contract has none;
- preserve an explicitly supplied timeout through the execution path;
- distinguish executor timeout from acceptance failure;
- read back lifecycle/result state after timeout;
- retain failure evidence rather than silently rewriting it.

## How to use this pack

Select only the pattern that matches the failure mode or proof obligation. These are verification patterns, not a replacement planner, queue, scheduler, or control plane.

## Claim boundary

The pack distills patterns from verified internal evidence. It does not claim that applying a checklist alone certifies a production system.
