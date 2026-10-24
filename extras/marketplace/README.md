# Stretch: install it properly (no --plugin-dir)

`--plugin-dir` loads your plugin for one session. To make it load in
EVERY session, Claude Code installs plugins from a *marketplace* — a
catalog folder that points at plugin folders.

1. Make a catalog folder anywhere, e.g. `~/my-market/.claude-plugin/`,
   and put `marketplace.json` in it (start from
   [`marketplace.json.example`](marketplace.json.example) — set `source`
   to the path of your cloned plugin repository, and note a local
   `source` must start with `./` or `../`).
2. Register and install:

```
claude plugin marketplace add ~/my-market
claude plugin install my-instrument@my-classroom
```

(`@my-classroom` is the `name` INSIDE marketplace.json, not the folder
name.) Verify with `claude plugin list` and `/mcp` in a new session.
Nothing needs to be public.
