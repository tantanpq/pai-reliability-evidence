# Bounded Independent Solution Certification

A verified reliability component demonstrated that a candidate can be certified only when an independent evaluator binds the certification to exact operating bounds rather than treating a generic PASS as permanent truth.

## Verified evidence boundary
- lifecycle: RESULT_VERIFIED / LIVE_PROVEN_COMPONENT;
- focused tests: 5/5 pass;
- 64 bounded candidates were assessed and certified in the verified fixture;
- self-certification is rejected;
- missing rollback or required fixture evidence rejects certification;
- expired certification is inactive;
- release, environment, scope, or counterevidence mismatch makes a certification inactive;
- certification does not mutate runtime, source code, authority, or solution execution.

## Reusable rules
1. Keep evaluator identity independent from the candidate producer.
2. Bind certification to exact version or release, environment, and scope.
3. Require the rollback and test fixtures needed to reproduce the claim.
4. Give certifications an explicit expiry or reevaluation condition.
5. Treat stale release, environment drift, scope drift, and counterevidence as invalidation signals.
6. Separate certification authority from repair or execution authority.
7. Reevaluate after material runtime changes instead of carrying an old PASS forward.

## Claim boundary
This is bounded component evidence. It does not prove universal correctness, production readiness, permanent validity, or authority to execute a repair.
