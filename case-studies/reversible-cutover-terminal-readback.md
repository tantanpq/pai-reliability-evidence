# Case Study: Reversible Cutover with Terminal Readback

## Problem

A candidate can pass build-time tests and still fail during promotion because live state, ownership, restart behavior, or configuration differs from the test environment. Declaring success immediately after a process starts is therefore weak evidence.

## Approach

The verified run used a staged sequence:

1. prepare a frozen candidate;
2. obtain independent QA;
3. capture bounded rollback state;
4. promote only the intended component;
5. compare promoted bytes with the frozen candidate;
6. restart only the affected service;
7. verify health and targeted state;
8. run a bounded canary;
9. record terminal completion;
10. perform a post-terminal system readback.

An earlier verification attempt in the same repair lineage did not pass. The successful path used a changed, re-verified candidate rather than relabeling the failed attempt.

## Verified result

The final cutover completed with exact candidate-to-live byte equality for the checked sets, successful bounded restart, passing health/readback and canary checks, successful terminal completion, and a passing post-terminal check with no active claims.

## Why this matters

The reusable capability is not “we can restart a service.” It is the evidence chain that separates candidate quality from live-effect truth and then verifies the system again after the claim is terminal.

That pattern is useful for release engineering, reliability work, controlled migrations, and other changes where rollback and truthful completion matter.

## Limits

The evidence is scoped to this captured run. It does not establish universal reliability, production certification, or coverage of every failure mode.
