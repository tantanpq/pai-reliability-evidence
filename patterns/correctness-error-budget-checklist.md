# Correctness Error Budget Checklist

Use this checklist when an automation or agent system can look available while correctness evidence is degraded.

## Definition

- [ ] Objectives are measurable in bounded lifecycle transitions or explicit observations.
- [ ] Required lifecycle transitions are named and cannot be skipped silently.
- [ ] Hard-zero correctness events are explicitly enumerated.
- [ ] Unknown event classes fail closed instead of being normalized away.
- [ ] Availability and latency misses are not mixed with correctness violations by default.

## Hard-zero candidates

Review whether the system should immediately exhaust the correctness budget on:

- [ ] duplicate external effects;
- [ ] lost terminal result evidence;
- [ ] unauthorized effects;
- [ ] stale replay or stale-owner mutation;
- [ ] false PASS;
- [ ] trace/provenance gaps that prevent reconstruction;
- [ ] rollback without restoration readback.

The exact list is system-specific. Do not copy these classes blindly into a production policy without mapping them to real invariants and effect boundaries.

## Change control

- [ ] Each mutable scope has a bounded change-rate policy.
- [ ] Concurrent changes to the same mutable scope are constrained.
- [ ] Repeated failed repairs trigger architecture or owner escalation rather than retry spirals.
- [ ] Rollback requires restoration plus fresh readback evidence.
- [ ] A repair in one dependency cone does not globally stall unrelated eligible work.

## Resolution

- [ ] Evidence verification happens before a current-state reread.
- [ ] Current-state reread happens before `RESOLVED`.
- [ ] Stability requires consecutive healthy evidence cycles, not elapsed wall time alone.
- [ ] Recurrence keeps the incident open until the regression window closes.
- [ ] A green availability dashboard cannot override missing correctness evidence.

## Authority

- [ ] The evaluator is advisory unless an existing governed owner explicitly admits enforcement.
- [ ] The evaluator does not create claims, schedules, queues, databases, writers, or authority.
- [ ] Candidate verification is never reported as live activation.
- [ ] Publication, production cutover, credentials, money, and legal effects retain their separate gates.

## Acceptance sentence

A useful acceptance statement is:

> The correctness budget is explicit, measurable, fail-closed for named hard-zero events, bounded by change control, and evaluated without creating a second authority path.
