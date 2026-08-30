# Terminal Result Supersession Checklist

A reusable evidence discipline for cases where an execution attempt fails for infrastructure reasons and later bounded work produces a verified terminal result.

## Preserve the original event

- [ ] Keep the original FAIL evidence immutable and inspectable.
- [ ] Record whether the failure came from acceptance logic, executor infrastructure, transport, timeout, or another bounded cause.
- [ ] Never silently relabel the original attempt as PASS.

## Qualify the replacement result

- [ ] Require a new bounded execution rather than editing terminal state by hand.
- [ ] Require the later result to satisfy the full acceptance criteria independently of the earlier attempt.
- [ ] Verify tests, integrity/hash evidence, and any required recovery/readback proof.
- [ ] Confirm the later result addresses the same work identity and acceptance scope.

## Reconcile explicitly

- [ ] Bind the authoritative terminal result to the superseded event.
- [ ] State why supersession is valid.
- [ ] Keep both events in the evidence chain.
- [ ] Make consumers resolve to the later verified terminal result without erasing the historical failure.

## Do not supersede when

- acceptance criteria actually failed and remain unresolved;
- the later run changes scope without an explicit new work identity;
- evidence is incomplete, running, materialized, or merely planned;
- provenance or integrity cannot be established.

## Claim boundary

Supersession repairs result semantics; it does not make an infrastructure timeout disappear and does not convert unverified work into completion.
