# Physical Startup Verification Checklist

Use this when a narrow startup or permission repair has passed static checks but still needs physical proof.

1. Freeze the exact candidate/result evidence before live validation.
2. Capture the relevant pre-change boundary so rollback and post-effect comparison are possible.
3. Apply only the smallest permitted change.
4. Re-run negative path and boundary cases before treating the change as safe.
5. Run one low-density physical canary first.
6. Require a terminal completion receipt and an executor identity for that canary.
7. Run a bounded concurrent burst only after the single canary passes.
8. Verify every accepted execution terminalizes exactly once.
9. Recompute executor uniqueness and result uniqueness independently.
10. Recompute observed concurrency from intervals rather than relying on launch count.
11. Re-read the changed boundary after the live run and verify adjacent/forbidden paths remain fail-closed.
12. Perform independent post-effect QA from frozen evidence and fresh readbacks.
13. Keep unresolved follow-on behavior explicitly open instead of expanding the claim.

## Fail-closed rule

Any mismatch in terminal receipts, uniqueness, boundary containment, or post-effect readback should stop the claim at NOT_DONE until a bounded changed-method correction is verified.

## Claim discipline

Passing this checklist supports a bounded startup-path claim. It does not establish fleet-wide availability, continued polling, remote placement behavior, or general production certification.
