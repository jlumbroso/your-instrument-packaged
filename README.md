# plugin-starter — the case your parts travel in

*Level: packaging. Your server (s4) and your skill (s6) become ONE
installable thing — a Claude Code plugin. Validated and load-tested
2026-10-22 (claude 2.1.308); doc-verified against code.claude.com/docs
plugins/* the same day.*

## What you fill in (3 edits, then 2 commands)

1. `classroom-market/my-instrument/.mcp.json` — your Render URL
   (keep `"type": "http"` — without it the entry is silently skipped).
2. `classroom-market/my-instrument/skills/my-ways/SKILL.md` — paste your
   s6 skill (frontmatter description + body). Folder name = skill name.
3. Both `plugin.json` and `marketplace.json` — your name.

## The core path (this is the win)

```
claude plugin validate ./classroom-market/my-instrument
claude --plugin-dir ./classroom-market/my-instrument
```

In that session: type `/` and find `/my-instrument:my-ways`; run `/mcp`
and see `plugin:my-instrument:my-server` connected.

## Stretch: install it properly

```
claude plugin marketplace add ./classroom-market
claude plugin install my-instrument@my-classroom --scope user
```

(`@my-classroom` is the marketplace NAME from marketplace.json, not the
folder. Local paths must start with `./`.)

## Gotchas (each one has eaten real minutes)

- `--plugin-dir` takes the PLUGIN root (`…/my-instrument`), not the
  marketplace root — wrong level loads nothing, silently.
- Only `plugin.json` lives inside `.claude-plugin/`; skills and
  `.mcp.json` live at the plugin root.
- Never name a plugin starting with `claude-`/`anthropic-` (reserved).
- Free Render services nap: warm your endpoint before the demo.
- No secrets in `.mcp.json` — a bearer header references an env var
  (`"Authorization": "Bearer ${MY_TOKEN}"`), never a pasted value.
- OAuth-protected servers (your-protected-notes): bundling works, but
  the in-plugin OAuth prompt path is UNVERIFIED — package your no-auth
  or guest-polite server for this exercise; protected stays connected
  the way you already have it.
- Changes apply at next session start or `/reload-plugins`.
