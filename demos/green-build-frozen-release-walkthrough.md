# Green Build, Frozen Release

A short synthetic walkthrough for demonstrating why verification and activation should be separate states.

## Scene 1 — Green candidate

Start with a synthetic candidate whose complete and focused test suites are green. Label it `CANDIDATE` rather than `LIVE`.

## Scene 2 — Bind the artifact

Recompute a synthetic tree fingerprint and show that an independent verifier obtains the same value. Mark the package `VERIFIED`.

## Scene 3 — Keep it frozen

Show that verification does not change the installed runtime. The candidate remains `FROZEN`.

## Scene 4 — Activation gate fails

Introduce a synthetic protected workload. Because active work is non-zero, set `activation_allowed=false`. Nothing is cut over.

## Scene 5 — Clear runtime prerequisites

Drain the synthetic workload, perform a fresh health check, and confirm protected active/running work is zero.

## Scene 6 — Pointer last

Only after every earlier gate passes, demonstrate the active-pointer update as the final activation action.

## Scene 7 — Separate receipts

End with four independently meaningful labels:

- `VERIFIED`: package evidence passed.
- `FROZEN`: package is intentionally not installed.
- `ACTIVATED`: the governed cutover was actually performed.
- `REJECTED`: a required gate failed.

## Demo safety

Use only synthetic identifiers, hashes, paths, hostnames, runtime values, and workloads. The walkthrough is educational and does not include private infrastructure details or deployment credentials.
