# Portable Byte-Fidelity Checklist

Use this pattern when text-like build inputs cross packaging, storage, or host boundaries and the verified bytes must survive intact.

## Source and decoding

- [ ] Bind expected source bytes by fingerprint and size before decoding.
- [ ] Use an explicit decoder contract that fails closed on malformed text.
- [ ] Specify byte-order-mark handling and test it directly.
- [ ] Reject unsupported encodings.
- [ ] Reject embedded NUL content where text-only semantics are required.
- [ ] Apply sensitive-content and scope checks before staging.

## Packaging and staging

- [ ] Build the bundle from verified bytes.
- [ ] Record a bundle fingerprint.
- [ ] Stage files without implicit transcoding.
- [ ] Compare staged files byte-for-byte with the verified snapshot.
- [ ] Recompute the staged/bundle fingerprint after staging.

## Independent verification

- [ ] Include ordinary UTF-8 round-trip coverage.
- [ ] Include the declared BOM-policy case.
- [ ] Include malformed and unsupported encoding cases.
- [ ] Include an embedded-NUL rejection case where applicable.
- [ ] Keep verification read-only with respect to the live runtime.

## Claim discipline

Source identity and byte fidelity are different proof boundaries. Correct source selection does not by itself prove that decoding, packaging, or staging preserved the same intended bytes.

This checklist grants no deployment, release, publication, scheduler, registry, queue, database, or control-plane authority.
