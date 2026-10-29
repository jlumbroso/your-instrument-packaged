# Stretch: install it properly (no --plugin-dir)

`--plugin-dir` loads your plugin for one session. To make it load in
EVERY session, Claude Code installs plugins from a *marketplace* — and
the simplest marketplace is **this repository itself**:

1. From the repository folder (AFTER you've finished the main steps):

```
cp extras/marketplace/marketplace.json.example .claude-plugin/marketplace.json
```

2. Edit that new file: set `"source": "./"` (this repo IS the plugin).
3. Register and install:

```
claude plugin marketplace add .
claude plugin install my-instrument@my-classroom
```

(`@my-classroom` is the `name` INSIDE marketplace.json. One quirk: once
`marketplace.json` sits beside `plugin.json`, plain `claude plugin
validate .` validates the MARKETPLACE; use
`claude plugin validate .claude-plugin/plugin.json` for the plugin.)

Verify with `claude plugin list` and `/mcp` in a fresh session — no
`--plugin-dir` needed anymore. Nothing is public.

*Why not a separate catalog folder pointing here? Claude Code resolves
sources relative to the marketplace root and refuses `..` paths, so a
sibling catalog can't reach this repo. (Found the hard way — Argon,
2026-10-29.)*
