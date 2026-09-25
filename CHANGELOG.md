# Changelog — skill

Versions follow SemVer. Tags are `vX.Y.Z` on this repository.

## v0.1.6 — 2026-09-25

- Document payout-only `REFUNDED` query and webhook results, including `refundNo`,
  `refundAmount`, and `refundTime`, with refund idempotency and late-success handling.

## v0.1.5 — 2026-09-22

- `references/methods.md`: `IDR` payouts require `accountNo` for every method, wallets
  included (`ID_DANA`, `ID_OVO`, `ID_GOPAY`, `ID_LINKAJA`, `ID_SHOPEEPAY`), matching the
  gateway. The `BDT`, `IDR`, `PHP` and `PKR` notes now say the recipient account is taken
  from `accountNo` — the phone number registered to the wallet for a wallet method — and
  that `mobile` is the recipient contact number, which never stands in for `accountNo`.

## v0.1.4 — 2026-09-21

- The reference tables no longer advertise what the gateway refuses: the currencies
  `RUB` and `THB`, the countries `RU` and `TH`, and the method codes no currency
  accepts (`APPLE_PAY`, `CREDIT_CARD`, `GOOGLE_PAY`, `NETELLER`, `P2P`, `PAGO_FACIL`,
  `RAPIPAGO`, `SBP`, `SERVIFACIL`, `SKRILL`, `TH_BANK_CARD`, `TH_BANK_TRANSFER`,
  `TH_PROMPTPAY`, `TH_TRUEMONEY` and the three `USDT-*` codes).
- `endpoints.md` says the currency list bounds order creation and that the country is
  derived from it, not checked on the way in; `GetBalance` and `GetUSDRate` take any
  currency.

- `references/methods.md` lists the method-code allowlist for every currency and
  direction the gateway validates (`ARS`, `BRL`, `CLP`, `COP`, `MXN`, `TRY`, and
  `IDR` payouts were previously open). `OXXO` is marked as a pay-in method and
  `TRANSFIYA` as payout only, matching the gateway.

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
