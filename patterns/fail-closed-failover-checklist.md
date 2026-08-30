# Fail-Closed Failover Verification Checklist

A reusable review pattern derived from verified deterministic failover simulation evidence.

## Before takeover

- [ ] Confirm the current mutable owner is unambiguous.
- [ ] Confirm the lease uses an explicit, ordered time basis.
- [ ] Require strict lease expiry; do not treat heartbeat loss alone as authority to take over.
- [ ] Revalidate graph/work identity, version, dependencies, and mutable-scope provenance.
- [ ] Check for an existing terminal result before allowing new mutation.
- [ ] Require candidate ordering to be deterministic when multiple takeover candidates exist.
- [ ] Fail closed when shared authority state or safe clock ordering cannot be established.

## During takeover

- [ ] Advance the fencing token atomically.
- [ ] Replace ownership so there is exactly one current mutable writer.
- [ ] Ensure a second contender cannot reuse the prior lease or token.

## After takeover

- [ ] Reject mutation from the prior owner using its stale token.
- [ ] Require a returning node to reread current ownership before doing mutable work.
- [ ] Reconcile duplicate result events idempotently.
- [ ] Repeat an equivalent scenario and compare serialized evidence for determinism.

## Claim boundary

Passing this checklist supports a bounded failover-safety review. It does not by itself prove production availability, disaster recovery, or universal split-brain prevention.
