# Case Study: The Test Failed Before the Code Ran

## Situation

A staged candidate was initially recorded as failing by an aggregate QA run. Evidence review showed that the failing event occurred at the QA invocation boundary before the candidate itself was exercised.

## Verification

The same frozen candidate bytes were rerun through the corrected verification path. The functional self-test passed its deterministic checks and the compile check exited successfully. No candidate mutation occurred between the original event and the clean rerun.

A separate build wave showed a complementary class: execution attempts remained not-done after a post-submit transport error, while frozen canonical package tests later passed across the complete batch.

## Correct verdict

The first event is evidence of `QA_COMMAND_TRANSPORT_FAILURE`; the second is evidence of `EXECUTION_TRANSPORT_FAILURE`. Neither event, by itself, proves a candidate defect.

## Lesson

Preserve the original failure, identify the boundary it actually proves, freeze candidate identity, rerun only the affected verification path, and record whether candidate bytes changed.

Boundary: this case study does not claim production readiness, live activation, universal correctness, or that every failed test is infrastructure noise.
