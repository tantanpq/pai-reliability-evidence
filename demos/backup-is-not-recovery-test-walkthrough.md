# A Backup Is Not a Recovery Test

A short synthetic walkthrough for demonstrating software-side recovery evidence without implying offline or physical-media guarantees.

## Scene 1 — Define the recoverable set

Start with a synthetic allowlist of ordinary files plus a separate synthetic secret fixture. Show the secret excluded from the distributable set.

## Scene 2 — Build manifests

Create synthetic full and incremental manifests for the allowed inputs.

## Scene 3 — Fail unsafe publication

Use synthetic traversal and missing-required-input cases and show publication fail closed.

## Scene 4 — Restore in isolation

Restore the clean synthetic backup into a temporary isolated target and compare restored bytes exactly with the accepted source bytes.

## Scene 5 — Missing object

Remove one synthetic backup object and show restore fail.

## Scene 6 — Corrupt object

Alter one synthetic backup object and show restore fail.

## Scene 7 — Seal by content identity

Create a synthetic content-addressed secondary copy. Show identical reuse accepted and attempted mutation rejected at the software layer.

## Scene 8 — Keep the boundary visible

End with two separate verdicts:

- `SOFTWARE_DR_ACCEPTED=true`
- `OFFLINE_OR_PHYSICAL_IMMUTABILITY=NOT_PROVEN`

## Demo safety

Use only synthetic names, files, paths, hashes, storage targets, and payloads. This walkthrough is defensive/educational and includes no credentials, real secrets, private infrastructure, or live mutation steps.
