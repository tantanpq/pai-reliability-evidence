# Reversible Cutover Verification Checklist

A compact pattern for changing a live component without turning “deployment succeeded” into a faith-based religion.

## Before effect

- Freeze the exact candidate bytes.
- Require independent QA appropriate to the changed seam.
- Capture the smallest rollback state needed to restore the previous known-good component.
- Confirm the change boundary and explicitly list surfaces that must remain unchanged.
- Avoid whole-system rollback when only a bounded component changed.

## During effect

- Change only the intended component or pointer.
- Preserve unrelated owners and services.
- Read back the promoted bytes and compare them with the frozen candidate.
- Restart only what the change actually requires.
- Keep rollback immediately available until health/readback succeeds.

## After effect

- Verify service health and the intended state.
- Run a bounded canary that can expose unintended execution or routing.
- Record terminal completion using immutable evidence.
- Run a post-terminal check for ownership coherence, active-work leakage, and basic execution eligibility.
- Retain evidence hashes and rollback provenance.

## Stop conditions

Treat the cutover as not verified if any of these occur:

- promoted bytes differ from the frozen candidate;
- rollback state is missing or ambiguous;
- unrelated components must be changed to make the candidate appear healthy;
- canary behavior contradicts the intended routing/effect boundary;
- terminal evidence is missing;
- post-terminal ownership or health is incoherent.

## Usage boundary

This checklist is a reliability pattern, not a substitute for system-specific safety, security, compliance, or change-management requirements.
