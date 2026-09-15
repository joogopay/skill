# Changelog — skill

Versions follow SemVer. Tags are `vX.Y.Z` on this repository.

## v0.1.0 — 2026-09-15

Initial release.

- Routing entry point plus the per-currency method codes, conditional required
  fields, endpoint list, checkout field semantics and order statuses, all
  generated from the protocol data that the SDKs validate against.
- Recovery rules for a create that failed: which outcomes mean nothing was sent,
  which require a query before resending, and which forbid reusing the merchant
  order number.
