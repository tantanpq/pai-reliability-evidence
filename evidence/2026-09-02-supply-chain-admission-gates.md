# Bounded Supply-Chain Admission Gates — Evidence Snapshot

## Scope

This public snapshot records a verified, bounded supply-chain assurance component used to decide whether a software candidate may proceed to the next admission or promotion gate.

The component verifies candidate identity and provenance, signer trust, source pinning, repository trust, a content-hashed software inventory, and vulnerability reachability before returning an admission decision.

## Verified result

Focused verification completed with **7/7 tests passing**.

The verified behavior included:

- unsigned candidates fail closed;
- candidates signed by an untrusted signer fail closed;
- provenance mismatch fails closed;
- source repository, branch, or commit mismatch fails closed;
- absence of a trusted repository source fails closed;
- a reachable HIGH or CRITICAL vulnerability is blocking;
- a HIGH vulnerability with no reachable runtime path remains a watch condition rather than becoming a blocking finding by itself;
- automatic dependency updates are not authorized by the gate;
- verification does not mutate the candidate working tree, install dependencies, roll out software, or touch credentials.

The verification also confirmed that candidate inventory evidence is content-hashed and that signer/source policy is evaluated before admission.

## Admission principle

A candidate is not admitted merely because it built successfully or because a security scanner produced a mostly clean report.

Admission requires evidence that answers separate questions:

1. **What exact candidate is this?**
2. **Where did it come from?**
3. **Is its signer trusted for this source and policy?**
4. **Does the immutable source identity match the expected repository, branch, and commit?**
5. **Is the inspected software inventory bound to the candidate?**
6. **Do blocking vulnerabilities have a reachable runtime path?**
7. **Did every required gate pass without silently changing the candidate?**

A failure in an admission-critical prerequisite stops promotion instead of being converted into an optimistic warning.

## Claim boundary

This evidence supports a **bounded admission-gate component**.

It does **not** establish:

- complete production security;
- a complete or universal software bill of materials;
- commercial code-signing, HSM, or PKI readiness;
- automatic vulnerability remediation;
- authorization to update dependencies;
- authorization to deploy or promote a release;
- security certification or zero-defect status.

Passing this gate means only that the candidate may be eligible for the **next governed gate**.

## Publication safety

This public abstraction contains no credentials, private source code, private filesystem paths, host identities, raw operational logs, customer or tenant data, protected evaluation corpora, proprietary failure-intelligence datasets, or third-party copyrighted source material.

The examples and terminology are intentionally generic so the verification lesson is reusable without exposing private implementation details.
