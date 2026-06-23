---
description: Read QUICKSTART.md if it exists, or bootstrap it with quickstart-keeper if it doesn't.
argument-hint: "[optional: a topic to focus on, or 'update' / 'deep-dive <name>']"
---

You are running the **`/quickstart`** command. Use the **quickstart-keeper** skill.

Do this:

1. **Check** whether `QUICKSTART.md` exists at the repo root.

2. **If it EXISTS** → *read mode*:
   - Read `QUICKSTART.md` first. If `$ARGUMENTS` names an area that maps to a
     `quickstart/<name>.md` deep dive, read that file too.
   - Honor the `git:` decision stored in its front-matter — do **not** re-ask the commit/ignore
     question.
   - Give me a short, high-signal summary: project structure, key commands, and any gotcha
     relevant to `$ARGUMENTS`. Don't dump the whole file back to me.

3. **If it does NOT exist** → *bootstrap mode*:
   - Explore the repo (layout, build/run/test/version/deploy commands) — bounded effort.
   - Ask the **one-time git question** exactly as the skill specifies (commit vs `.gitignore`),
     apply the choice, and store the `quickstart-keeper:` marker in the front-matter.
   - Write a concise `QUICKSTART.md` from the skill's template. Never include secret values.

4. **If `$ARGUMENTS` is `update`** → apply Behavior 4: update `QUICKSTART.md` for whatever
   changed recently, prune stale lines, and spin off a `quickstart/<name>.md` deep dive if an
   area is complex enough to warrant it.

Argument: $ARGUMENTS
