# Supply-Chain Admission Gate Checklist

Use this checklist before allowing a software candidate to proceed to a governed promotion or release gate.

## 1. Freeze candidate identity

- [ ] Bind the candidate to an immutable digest.
- [ ] Record the expected source repository.
- [ ] Record the expected branch or equivalent source reference.
- [ ] Record the exact source commit or immutable revision.
- [ ] Reject identity ambiguity instead of guessing which build is intended.

## 2. Verify provenance and signer policy

- [ ] Require a valid signature when policy requires signing.
- [ ] Verify that at least one accepted signer is trusted for this admission policy.
- [ ] Verify that signed provenance refers to the same immutable candidate.
- [ ] Verify repository, branch, and commit against trusted source metadata.
- [ ] Fail closed on unsigned, invalid, untrusted, or mismatched provenance.

## 3. Bind inventory evidence

- [ ] Generate or obtain the software inventory for the exact candidate.
- [ ] Content-hash the inventory evidence.
- [ ] Preserve the relationship between candidate digest and inventory digest.
- [ ] Treat missing inventory evidence as UNKNOWN or blocking according to policy, never as implicit PASS.

## 4. Evaluate vulnerability reachability

- [ ] Classify HIGH and CRITICAL findings separately from lower-severity findings.
- [ ] Determine whether the affected component is reachable on a relevant runtime path.
- [ ] Block admission when policy identifies a reachable HIGH or CRITICAL vulnerability as blocking.
- [ ] Keep an unreachable HIGH finding visible as WATCH rather than silently deleting it.
- [ ] Preserve uncertainty when reachability cannot be established.

## 5. Keep verification non-mutating

- [ ] Do not update dependencies as part of the admission decision.
- [ ] Do not edit the candidate working tree to make the gate pass.
- [ ] Do not deploy, promote, or roll out software from the verification step.
- [ ] Do not touch credentials merely to manufacture a PASS.
- [ ] Route remediation into a separate governed change with its own identity and evidence.

## 6. Fail closed on admission-critical evidence

Block the candidate when any required condition is false, including:

- [ ] missing or invalid signature;
- [ ] untrusted signer;
- [ ] provenance mismatch;
- [ ] trusted-source mismatch;
- [ ] repository, branch, or commit mismatch;
- [ ] blocking reachable vulnerability;
- [ ] missing mandatory evidence that policy requires before admission.

## 7. Preserve a bounded decision

Return one of a small set of explicit outcomes, for example:

| Outcome | Meaning |
|---|---|
| `BLOCK` | A required admission condition failed. |
| `WATCH` | Evidence warrants attention but is not independently blocking under the current bounded policy. |
| `ELIGIBLE_FOR_NEXT_GATE` | Required checks passed; this is not automatic release authority. |
| `UNKNOWN` | Evidence is insufficient to decide safely. |

## Claim boundary

A PASS at this checklist is evidence for the **admission gate only**. It does not certify the entire product, prove production safety, authorize automatic remediation, or authorize deployment.

The release or promotion owner remains responsible for every later governed gate.
