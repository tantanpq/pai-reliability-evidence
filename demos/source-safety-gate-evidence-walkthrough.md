# Source Safety Gate — Synthetic Evidence Walkthrough

This walkthrough uses synthetic examples only. It demonstrates the verification pattern without exposing private source code, credentials, paths, hashes, or logs.

## Scene 1 — Benign identifier

Example:

```text
state.fencingToken = nextGeneration
```

Expected result: **PASS** when the surrounding content is ordinary implementation logic and no sensitive value class is present.

The lesson: a property name containing `token` is not itself evidence of a credential.

## Scene 2 — Credential-shaped literal

Example:

```text
apiToken = "<synthetic-credential-value>"
```

Expected result: **FAIL CLOSED** under the tested credential-literal policy.

The value shown here is deliberately synthetic and is not a usable credential.

## Scene 3 — Private-key fixture

Use a synthetic fixture marked as private-key material.

Expected result: **FAIL CLOSED**.

## Scene 4 — Explicit placeholder fixture

Use a synthetic source fragment containing an explicit secret placeholder in a sensitive context.

Expected result: **FAIL CLOSED**.

## Scene 5 — Regression trap

Now replace the bounded semantic rule with a shortcut such as “allow every identifier containing token-like wording.”

Expected result: the negative fixture suite must fail. If it does not, the classifier has widened beyond the reviewed safety boundary.

## Scene 6 — Frozen evidence and independent QA

Before activation:

- pin the exact source bytes;
- run positive and negative fixtures;
- preserve path, scope, carrier, and byte-fidelity checks;
- freeze the candidate;
- independently re-read candidate and manifest evidence;
- keep release authority outside the classifier.

## Closing rule

**Classify values and context, not scary substrings alone.**

This is a defensive assurance pattern, not a universal secret scanner or production certification.
