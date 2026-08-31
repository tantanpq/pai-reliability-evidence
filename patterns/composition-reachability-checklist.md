# Composition Reachability Checklist

Use this checklist before upgrading helper-level or injected-dependency success into an integration-readiness claim.

## Bind the selected composition

- [ ] Freshly pin the selected runtime/release identity.
- [ ] Name the required provider or observation contract.
- [ ] Verify the provider's own acceptance/current status.
- [ ] Verify the selected composition contains the required configuration and wiring.
- [ ] Reject any dependency that exists only in an unaccepted candidate.

## Exercise the real path

- [ ] Run the actual normal entrypoint.
- [ ] Confirm missing provider produces truthful `UNKNOWN` or another defined fail-closed state.
- [ ] Send representative accepted observations through the real composition.
- [ ] Confirm values are not fabricated as zero, healthy, progress, or capacity when the provider is absent.
- [ ] Do not use helper-only injection as a substitute for entrypoint reachability.

## Separate evidence classes

- [ ] Record semantic/helper PASS separately from composition PASS.
- [ ] Record provider acceptance separately from provider reachability.
- [ ] Preserve negative QA when the real path is missing even if subtests pass.
- [ ] Require correction + re-verification before changing the integration verdict.

## Fail closed when

- the selected runtime identity is unknown;
- provider acceptance is unknown;
- provider wiring cannot be demonstrated;
- only injected tests can obtain the dependency;
- an unaccepted candidate is the sole source of the required provider.

A component can be perfectly injectable and still be unreachable in the system that matters.
