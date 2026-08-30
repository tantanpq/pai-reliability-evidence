# Single-Owner Cutover Soak Gate

Use this checklist when a canary or promotion claims that one owner has replaced a prior competing owner. A successful first effect is not enough; the owner must remain stable across a bounded observation window.

## Gate order

1. Pin the exact candidate and promotion target before cutover.
2. Record the selected owner and the previously competing owner.
3. Verify the previous owner is disabled or otherwise unable to compete.
4. Verify the promoted owner through the authoritative read path.
5. Run a bounded post-promotion soak with repeated health/readback observations.
6. Confirm active work does not conceal an ownership race during the tested window.
7. Re-read the exact runtime stamp or equivalent immutable promotion evidence during independent QA.
8. Compare the checked candidate, promoted winner, and consumer/Task Box access paths for expected byte consistency where applicable.
9. Run the targeted regression set after promotion.
10. Keep rollback authority and long-term SLO claims outside this gate.

## Suggested receipt

Record at least:

- promotion/candidate identity;
- selected-owner identity class;
- prior-owner disabled status;
- soak observation count and pass count;
- active-claim range during the soak;
- campaign/regression pass counts;
- exact runtime-stamp readback status;
- checked-byte consistency across relevant access paths;
- independent-QA status;
- unsupported claims.

## Acceptance

- [ ] Promotion target was pinned before the effect.
- [ ] Exactly one intended owner was observed after promotion.
- [ ] The previous competing owner remained disabled throughout the tested window.
- [ ] Every required bounded soak observation passed.
- [ ] No active-claim evidence hid a competing owner during the soak.
- [ ] Targeted regressions passed after promotion.
- [ ] Independent QA re-read the exact runtime evidence.
- [ ] Required consumer/read paths returned the expected checked bytes.
- [ ] A canary PASS was not treated as long-term HA/SLO proof.

## Boundary

This is a bounded cutover-verification pattern, not a universal availability, scheduler, or production-certification standard.
