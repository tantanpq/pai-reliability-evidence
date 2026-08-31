# The Path That Passed Around the Policy

## Situation

A candidate implemented the intended freshness/admission gate on its ordinary execution route and passed broad copied tests. A less-common but reachable route to the same protected effect retained weaker eligibility logic.

If review had stopped at the main route and aggregate pass count, the candidate would have looked healthy.

## Approach

Independent QA separated **policy invariant** from **route implementation**:

1. verify candidate integrity;
2. rerun the broad and targeted suites;
3. enumerate reachable entrypoints to the protected effect;
4. trace each route to its actual admission predicate;
5. build a route-specific negative falsifier;
6. inspect whether signer/freshness construction remained under one accountable owner or had been duplicated.

## Result

The ordinary route enforced the expected freshness sequence. The copied suites passed. The route-specific falsifier nevertheless demonstrated that an alternate route could admit a degraded state that the invariant required it to reject.

Because that route could reach the protected effect without equivalent proof, QA rejected the candidate. No live mutation was performed.

## Why this matters

Policy text is not policy closure.

A system can contain:

```text
COMMON PATH: strong gate
SPECIAL PATH: weaker predicate
```

and still report a reassuring aggregate test result if the special path is not directly challenged.

The useful unit of assurance is therefore not “the policy exists.” It is:

> every reachable route to the protected effect proves the same invariant through an accountable owner.

## Reusable lesson

```text
NAME THE INVARIANT ONCE
→ ENUMERATE REACHABLE ROUTES
→ BIND THEM TO ONE GOVERNED POLICY OWNER
→ TEST VALID STATES
→ FALSIFY STALE / DEGRADED STATES
→ FAIL CLOSED ON ANY WEAKER ROUTE
```

## Claim boundary

This case study demonstrates bounded reachable-path policy-integrity failure from one verified QA result. It does not prove a production exploit, universal authorization security, formal verification, or production readiness.

The public version intentionally excludes private route names, source, keys, receipts, paths, hashes, hosts, logs, and internal identifiers.
