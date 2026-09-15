# JooGoPay SDK integration skill

An agent skill for integrating with the merchant open API. It carries the request
signing scheme, the per-currency payment and payout method codes with their
conditional required fields, the endpoint list, and the rules for deciding whether
a failed request means the order exists.

## Install

```
npx skills add joogopay/skill
```

Works with Claude Code, Cursor, Codex and other agents the `skills` CLI supports.
The agent reads `SKILL.md` first and pulls the tables in `references/` on demand.

Without Node, copy the files in by hand:

```
DEST=~/.agents/skills/joogopay-integration
git clone https://github.com/joogopay/skill.git
mkdir -p "$DEST"
cp -r skill/SKILL.md skill/references "$DEST"/
```

`~/.agents/skills/` is the shared location Codex, Cursor, Gemini CLI, Warp and others read.
Claude Code reads `~/.claude/skills/`, so symlink it there as well:

```
mkdir -p ~/.claude/skills
ln -s "$DEST" ~/.claude/skills/joogopay-integration
```

`npx skills add` does both for you, which is why it is the first option.

## Ask your agent

Once installed:

- "Create a BRL PIX payment for 10.00 and give me the checkout URL"
- "Which extra fields does an IDR OVO payout need?"
- "My create call timed out. Did the order go through, and can I resend the same merchantOrderNo?"
- "The gateway returned CHANNEL_ERROR. What do I do before retrying?"
- "Write a webhook handler that verifies the signature and ignores replays"
- "My request comes back 401. Walk through the signature base."

## Contents

| File | What it holds |
|---|---|
| `SKILL.md` | Routing, configuration, signing, and the money-safety rules |
| `references/methods.md` | Method codes per currency and the extra fields each one requires |
| `references/endpoints.md` | Endpoints, which are signed or encrypted, statuses, currencies |
| `protocol/` | The underlying protocol notes the SDKs implement |
| `index.json` | Manifest for serving this skill over HTTP; not needed when installing from this repository |

This repository is generated. Changes belong in the source tree that produces it;
edits made here are overwritten by the next release.
