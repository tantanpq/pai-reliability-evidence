# Verification Signal Integrity

A failed execution signal is not automatically evidence that the candidate failed.
Before assigning a technical verdict, classify which boundary actually failed.

## Four distinct boundaries

1. **Candidate behavior** — the candidate ran and its acceptance assertion failed.
2. **QA invocation** — the test command or harness failed before the candidate was exercised.
3. **Execution transport** — submit/relay/worker transport failed while candidate bytes may remain valid.
4. **Lifecycle projection** — a status surface reports an attempt state that may not describe independently verified candidate bytes.

These states must not be collapsed into one generic `FAIL`.

## Evidence rule

A candidate may be reclassified only when the evidence shows that the original failing boundary did not execute or judge the candidate, and a clean rerun tests the same frozen candidate without mutation.

A later PASS does not erase the earlier failure. It narrows the failure to the boundary actually supported by evidence.
