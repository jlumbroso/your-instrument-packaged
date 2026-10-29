# your-instrument-packaged — the steps, in class order

*The packaging level of the instrument series. **s4**: your server exists
in the world. **s5**: it remembers. **s6**: it has a handbook (your
SKILL.md). **s7**: it knows you. This level: **it travels as one** —
your server and your skill become a single installable thing, a Claude
Code plugin. One folder, three edits, two commands.*

## Before you start (prerequisites)

You need: **Claude Code installed** (`claude` runs in your terminal), a
**git clone** of your template copy, your **Render URL** (s4), and your
**SKILL.md** (s6). Nothing else.

## 0. Get the folder (1 minute)

**First click "Use this template"** (the green button on GitHub) to make
YOUR copy under your own account, THEN clone YOUR copy. (Cloning the
original directly means you can't push your edits or your slide later.) **This repository IS the plugin** — the folder you just cloned
is the thing that gets installed. Nothing is nested.

## 1. Three edits (5 minutes)

1. **`.mcp.json`** — replace the placeholder with YOUR server's URL —
   and while you're here, **open that URL once in a browser** (or
   `curl` it): free Render instances nap, take 30–50 s to wake, and
   Claude Code gives up connecting at 30 s. Wake it now, not at load
   time. Then:
   (the Render address from s4, ending in `/mcp`). Keep the
   `"type": "http"` line — without it the entry is silently skipped.
   Use your no-auth server (time or memory); protected-notes stays
   connected the way you already have it.
2. **`skills/my-ways/SKILL.md`** — replace the placeholder with your s6
   skill: your description in the frontmatter (keep it in "quotes" — a
   bare colon inside breaks YAML), your WHEN/HOW rules in the body.
   **Keep `name: my-ways` on line 2**: the slash command is
   `/my-instrument:<that name>`, so pasting your s6 name changes the
   command you'll look for below.
3. **`.claude-plugin/plugin.json`** — put your name in `author`.
   **Keep the plugin name `my-instrument` for tonight** — it's what the
   `/my-instrument:my-ways` command below expects (rename later and the
   slash command renames with it; never start a name with `claude-` or
   `anthropic-` — reserved).

## 2. Validate (10 seconds)

From the repository folder:

**Save all three files first.** Then, from the repository folder:

```
claude plugin validate .
```

Green means the shape is right (note: it checks SHAPE — it passes even
with placeholders still in, so eyeball your three edits). An error names the exact file and field.

## 3. Load it (the win)

**Step OUT of the folder first** — this is the point of the level:

```
cd ..
claude --plugin-dir ./your-instrument-packaged
```

(Running from INSIDE the repo makes Claude Code treat the plugin's own
`.mcp.json` as a project config and suppress the plugin's server — the
one wrong-feeling prompt of the night. From outside, no prompt, and
your instrument is proving it works away from its home folder.)

In that session: type `/` — you'll see **`/my-instrument:my-ways`**.
Run `/mcp` — your server shows as **connected**. (If it shows your OLD
server name from s4 instead, Claude Code deduplicated the same URL —
that still counts.) That's the whole level: the parts travel as one.

Five-second bonus: `claude --plugin-dir ./your-instrument-packaged plugin details my-instrument`
prints what your plugin costs per session in tokens (~59 always-on).

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
