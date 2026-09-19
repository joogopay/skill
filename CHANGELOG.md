# Changelog — skill

Versions follow SemVer. Tags are `vX.Y.Z` on this repository.

## v0.1.3 — 2026-09-19

- `references/methods.md` reflects the Philippine payout change: `PH_GCASH` and
  `PH_MAYA` are payout methods as well as pay-in ones and join the `PHP` payout
  allowlist, and `bankCode` is no longer required for every `PHP` payout — only
  `PH_DF_BANK` and `PH_DF_WALLET` still require it, since the channel derives the
  wallet from the named code.

## v0.1.2 — 2026-09-18

- Needs a platform that accepts an omitted or `null` ARS `address` (platform
  release of 2026-09-18); against an earlier platform, send `address` as a string.
- Document the optional, nullable ARS `BANK_TRANSFER` payout `address` contract
  from shared method rules: omission, `null` and empty strings mean no address;
  non-empty strings are preserved and other value types are invalid.
- `references/methods.md` gains the USD rows: `CASH_APP` for pay-in, `CASH_APP` /
  `PAYPAL` / `CHIME` for payouts, each with its required fields.

## v0.1.1 — 2026-09-15

- The manual install now targets `~/.agents/skills/`, the location agents other than
  Claude Code read, and symlinks it into `~/.claude/skills/`. The previous command only
  reached Claude Code.

## v0.1.0 — 2026-09-15

Initial release.

- Routing entry point plus the per-currency method codes, conditional required
  fields, endpoint list, checkout field semantics and order statuses, all
  generated from the protocol data that the SDKs validate against.
- Recovery rules for a create that failed: which outcomes mean nothing was sent,
  which require a query before resending, and which forbid reusing the merchant
  order number.
