# Evidence-first recovery classification checklist

Use this checklist after a distributed or automated attempt reaches a failure or uncertain terminal boundary.

## 1. Verify identity before classifying

Confirm that the evidence belongs to the same attempt and expected execution identity. Treat missing or mismatched identity evidence as invalid.

## 2. Separate outcome from recovery policy

Classify what happened first. Do not let the classifier silently create retries, successors, claims, queues, or authority.

## 3. Use five bounded classes

| Class | Required evidence | Safe disposition |
| --- | --- | --- |
| Success | Verified successful terminal evidence | Accept terminal success |
| Terminal task failure | Verified unsuccessful terminal evidence | Keep terminal for this attempt |
| Recoverable technical failure | Technical failure plus verified rollback/readback | Continue only from known-good state under existing policy |
| Ambiguous effect | Submit may have occurred but trusted result is absent | Reconcile the same effect identity before replay |
| Invalid evidence | Unknown, malformed, missing, or failed verification | Fail closed; infer nothing |

## 4. Treat ambiguity as an anti-replay boundary

If a submit may have taken effect, do not create a fresh local replay merely because the response is missing. Reconcile the original effect first.

## 5. Require rollback proof for technical recovery

A failure is not safely recoverable merely because a rollback was attempted. Require readback that the known-good state was actually restored.

## 6. Keep global lifecycle semantics outside the classifier

Do not redefine project-wide meanings of DONE, BLOCKED, NOT_DONE, or equivalent lifecycle states inside a local recovery classifier.

## 7. Verify the verifier

Run both focused classification tests and the broader integration suite. Preserve source identity so the evidence can be traced to the tested bytes.

## Evidence basis

This checklist is derived from a verified candidate whose independent QA passed a 166-test isolated suite after source-manifest and dependency-integrity checks. It is a reusable engineering pattern, not a production certification.
