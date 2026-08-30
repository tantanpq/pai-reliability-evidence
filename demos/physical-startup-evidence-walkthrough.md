# Physical Startup Evidence Walkthrough

This synthetic walkthrough demonstrates how to turn a narrow startup repair into bounded physical evidence without exposing a real environment.

## Scenario

Assume a worker needs one narrowly scoped state permission before its startup path can execute correctly. Static checks have already passed, but physical behavior is still unproven.

## Walkthrough

1. Record the pre-change permission boundary and freeze the candidate evidence.
2. Apply only the intended narrow permission change.
3. Re-run negative checks against adjacent and traversal-style paths. They must remain denied.
4. Launch one physical canary and require a terminal completion plus executor identity.
5. If it passes, launch a bounded 10-lane burst.
6. For every accepted lane, collect only the evidence needed to prove terminal state and execution uniqueness.
7. Independently recompute overlap from execution intervals. Ten launches do not prove ten-way concurrency; interval overlap does.
8. Re-query terminal receipts independently rather than trusting the original launcher summary.
9. Re-read the permission boundary after execution and confirm that the change did not broaden.
10. State the unresolved next behavior explicitly instead of extending the claim.

## Example result shape

A valid bounded result might read: single canary **1/1 completed**; burst **10/10 completed**; independent re-query **11/11 completed**; burst overlap peak **10**; executor identities and result fingerprints unique; negative boundary checks still fail closed.

## Lesson

A green configuration check is not the same thing as physical startup proof. The stronger demonstration connects the narrow change to terminal execution and then checks that the safety boundary survived the effect.
