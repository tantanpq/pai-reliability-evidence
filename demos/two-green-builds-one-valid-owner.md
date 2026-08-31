# Two Green Builds, One Valid Owner

This synthetic walkthrough shows why functional PASS does not automatically grant architecture ownership.

No private implementation, real infrastructure, credentials, customer data, or production identifiers are used.

## Setup

Assume one governed verification policy already exists:

```text
policy-owner-A
  -> evaluate candidate
  -> emit advisory verification result
  -> promotion authority: NONE
```

A second implementation is introduced:

```text
policy-owner-B
  -> evaluate candidate
  -> emit advisory verification result
  -> promotion authority: NONE
```

Both implementations are given the same synthetic functional fixtures.

## Functional result

```text
owner-A tests: PASS
owner-B tests: PASS
```

If the review stops here, both appear acceptable.

## Ownership/provenance check

Now ask a different question:

```text
Does owner-B add a missing capability?
```

Synthetic answer:

```text
existing capable owner: owner-A
missing capability: false
duplicate policy owner: true
```

Expected disposition:

```text
owner-A: KEEP
owner-B: REJECT / DISCARD
```

## Known-bad mutant check

Change one synthetic policy rule so an unsupported state is accepted.

Expected evaluator behavior:

```text
known-bad mutant: REJECT
```

This validates that the verification layer can catch deliberately broken variants instead of only confirming known-good fixtures.

## Rollback/readback

After rejecting owner-B:

```text
canonical owner: owner-A
active duplicate owner count: 0
promotion authority from verification: NONE
```

## Takeaway

> “The code works” and “this is the correct component to own the behavior” are separate claims.

A useful verification membrane checks both, while keeping deployment and promotion behind their existing authority gates.
