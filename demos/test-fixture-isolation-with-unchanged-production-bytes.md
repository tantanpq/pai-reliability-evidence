# Demo Outline: Make a Configuration-Dependent Test Deterministic

Status: synthetic demonstration plan derived from verified evidence. It does not require live production access.

## Goal
Show why a test coupled to mutable runtime policy can create a false regression signal, then show the same test using an explicit fixture.

## Five-minute flow
1. Start with a small sample function whose behavior depends on a policy object.
2. Demonstrate a test that reads a mutable external policy value and changes outcome when that value drifts.
3. Replace the ambient dependency with a checked-in fixture owned by the test candidate.
4. Run the focused test and the surrounding suite.
5. Compare protected production hashes before and after to demonstrate that only test evidence changed.
6. Close with the evidence boundary: deterministic test isolation improves attribution, but does not itself certify production behavior.

## Evidence anchors for narration
- Focused verified suite: 31/31 PASS.
- Full verified suite: 167/167 PASS.
- Tree identity replay: 219 entries matched the expected tree hash.
- Protected production and launcher bytes: unchanged.
- Live activation: none.

Use synthetic names and sample configuration in any public recording. Do not display private paths, internal identifiers, credentials, raw logs, or proprietary source.
