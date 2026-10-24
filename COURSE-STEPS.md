# your-instrument-packaged — the steps, in class order

*The packaging level of the instrument series. **s4**: your server exists
in the world. **s5**: it remembers. **s6**: it has a handbook (your
SKILL.md). **s7**: it knows you. This level: **it travels as one** —
your server and your skill become a single installable thing, a Claude
Code plugin. One folder, three edits, two commands.*

## 0. Get the folder (1 minute)

Use this template (the green button on GitHub) to make YOUR copy, then
clone it. **This repository IS the plugin** — the folder you just cloned
is the thing that gets installed. Nothing is nested.

## 1. Three edits (5 minutes)

1. **`.mcp.json`** — replace the placeholder with YOUR server's URL
   (the Render address from s4, ending in `/mcp`). Keep the
   `"type": "http"` line — without it the entry is silently skipped.
   Use your no-auth server (time or memory); protected-notes stays
   connected the way you already have it.
2. **`skills/my-ways/SKILL.md`** — replace the placeholder with your s6
   skill: your description line in the frontmatter, your WHEN/HOW rules
   in the body.
3. **`.claude-plugin/plugin.json`** — put your name in `author`.
   (Keep the plugin name simple; never start it with `claude-` or
   `anthropic-` — those are reserved.)

## 2. Validate (10 seconds)

From the repository folder:

```
claude plugin validate .
```

Green means the shape is right. An error names the exact file and field.

## 3. Load it (the win)

```
claude --plugin-dir .
```

In that session: type `/` — you'll see **`/my-instrument:my-ways`**
(your skill, loaded from your plugin). Run `/mcp` — your server shows
as **connected**. That's the whole level: the parts travel as one.

## 4. Feel the difference (2 minutes)

Ask Claude something your skill covers, without naming your tool.
Watch it reach — your WHEN rules deciding, your server answering, from
one installed thing. If the first call stalls ~30 seconds, that's your
free Render instance waking up; ask again.

---

**Stretch** (only if you're curious): installing it *properly* — so it
loads in every session without `--plugin-dir` — goes through a
marketplace catalog. See [`extras/marketplace/`](extras/marketplace/).

**Something looks different than these steps?** Say so in class or on
Slido — a mismatch between instructions and reality is course material
here, never your mistake.
