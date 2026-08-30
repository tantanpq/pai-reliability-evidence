# From Permission Repair to Physical Startup Proof

## Problem

A narrowly scoped permission repair can pass static and isolated checks while the real startup path still fails. Treating the repair itself as proof would collapse two different questions: “is the boundary correct?” and “does the physical execution path now work?”

## Method

The validation kept those questions separate.

- First, the changed permission boundary was constrained and negative path cases were required to remain fail-closed.
- A single live canary then had to reach terminal completion with an executor identity.
- Only after that passed was a bounded 10-lane burst executed.
- The burst was evaluated by terminal receipts, distinct executor identities, distinct result fingerprints, and independently recomputed interval overlap.
- A separate QA pass re-queried the full physical result set and re-read the permission boundary after the effect.

## Verified outcome

The low-density canary completed **1/1**. The concurrent burst completed **10/10**. Independent QA confirmed **11/11** physical completions, an overlap peak of **10**, and **10 distinct executor identities** plus **10 distinct result fingerprints** in the burst. The intended permission boundary remained narrow and the negative containment cases remained fail-closed.

## What made the proof stronger

The useful part was not merely that the burst was green. The evidence connected a narrow change to physical execution, terminal state, uniqueness, real overlap, post-effect readback, and independent verification. Each stage ruled out a different class of false confidence.

## Boundary

The result closes only the tested startup path. Continued polling, remote pull/placement behavior, broad availability, and production certification were left open rather than being inferred from the successful canaries.
