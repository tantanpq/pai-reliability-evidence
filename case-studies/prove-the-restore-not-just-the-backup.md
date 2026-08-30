# Prove the Restore, Not Just the Backup

## Situation

A recovery design had working backup mechanics, but the useful assurance question was stricter: could the software define exactly what was recoverable, exclude sensitive inputs, reject damaged artifacts, and restore the accepted set byte-for-byte without pretending ordinary software storage was an offline recovery medium?

## Approach

The candidate was constrained to a software DR contract. Verification used an allowlisted fixture, excluded secret input, exercised full and incremental manifests, rejected traversal and missing inputs, restored into an isolated temporary target, compared restored files byte-for-byte, rejected corrupt or missing backup objects, and checked a sealed content-addressed secondary copy. Independent QA preserved the unresolved physical-media boundary.

## Evidence

- **13/13** ordinary allowlisted files verified for full and incremental manifests.
- Secret input excluded from the distributable set.
- Traversal and missing required inputs failed closed.
- All **13 files** restored byte-for-byte in an isolated target.
- Missing and corrupt backup objects were rejected.
- Identical sealed-copy reuse was accepted while mutation was rejected at the software layer.
- Independent QA accepted the software DR component.
- No live activation occurred.

## Value

The result replaces vague “backup succeeded” confidence with a testable recovery contract. It also keeps software recovery semantics separate from stronger claims about offline media or physical immutability.

## Boundary

Dedicated offline or physically immutable recovery-medium proof remains outside this result. Production activation and complete disaster-recovery closure are not claimed.
