# Source Safety Gate — Verification Checklist

Use this checklist when a source-packaging or build-preparation pipeline needs to reject real sensitive material without blocking benign identifiers merely because their names contain words such as `token`.

## Gate order

1. Pin exact source identity and immutable bytes before classification.
2. Evaluate filename/path policy separately from content semantics.
3. Fail closed on the tested private-key, explicit-placeholder, credential-shaped literal, and sensitive path classes.
4. Do not reject a benign property or identifier solely because its name contains token-like wording.
5. Preserve byte-fidelity, path, scope, and carrier checks around the classifier.
6. Run adversarial positive and negative fixtures.
7. Independently re-read the frozen candidate and manifest before activation.
8. Keep deployment and release authority outside the classifier.

## Suggested receipt

Record at least:

- source identity and source digest;
- classifier and policy versions;
- benign token-identifier cases passed;
- tested secret/private-key/placeholder cases rejected;
- credential-named path cases rejected;
- byte-fidelity status;
- scope and carrier status;
- independent-QA status;
- frozen-manifest reference;
- runtime-mutation count;
- unsupported claims.

## Acceptance

- [ ] Exact source bytes were pinned before classification.
- [ ] Benign token-like identifiers/properties passed.
- [ ] Tested credential-shaped literal assignments failed closed.
- [ ] Tested private-key fixtures failed closed.
- [ ] Tested explicit-placeholder fixtures failed closed.
- [ ] Sensitive path/name rules remained enforced.
- [ ] UTF-8/BOM behavior remained deterministic.
- [ ] Path, scope, and carrier checks remained enforced.
- [ ] Frozen candidate/manifest evidence was independently re-read.
- [ ] Candidate or QA PASS was not treated as deployment authority.

## Boundary

This checklist is a verification pattern, not a universal secret-scanning specification or security certification.
