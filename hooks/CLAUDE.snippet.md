<!--
  Paste the block below into your project's CLAUDE.md.
  It makes the agent treat QUICKSTART.md as the authoritative first read, and keep it updated.
  Use it together with the SessionStart hook (hooks/settings.json) for belt-and-suspenders.
-->

## Project context
- Always read `QUICKSTART.md` at the repo root **before** doing any work. It is the concise,
  authoritative map of structure, build/run/test/version/deploy commands, and gotchas.
- For complex areas, follow its links into `quickstart/<name>.md` instead of re-reading source.
- When you change a build step, rename a key file, or alter a procedure, update `QUICKSTART.md`
  in the same change and prune stale lines. Never put secrets in it.
