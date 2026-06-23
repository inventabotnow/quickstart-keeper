# Publishing quickstart-keeper to GitHub

## Suggested repository file tree

```
quickstart-keeper/
├── SKILL.md                          # the skill (YAML frontmatter + behavior)
├── README.md                         # GitHub landing page
├── LICENSE                           # MIT (edit the copyright name)
├── PUBLISH.md                        # this file
├── .gitignore
├── commands/
│   └── quickstart.md                 # the /quickstart slash command
├── hooks/
│   ├── settings.json                 # ready-to-paste SessionStart hook
│   └── CLAUDE.snippet.md             # ready-to-paste CLAUDE.md snippet
└── examples/
    ├── QUICKSTART.md                 # sample generated index
    └── quickstart/
        └── checkout-flow.md          # sample deep-dive
```

## Before you publish
- `LICENSE` and the install URLs are already set to **Solaitions / `inventabotnow`**.
- If your actual GitHub org slug isn't `inventabotnow`, find-and-replace `inventabotnow` across
  `README.md` and `PUBLISH.md`.

## Exact git commands

```bash
# from inside the quickstart-keeper/ folder
git init
git add .
git commit -m "feat: quickstart-keeper — transportable QUICKSTART knowledge layer skill"
git branch -M main

# create the repo first on github.com (named quickstart-keeper), then:
git remote add origin https://github.com/inventabotnow/quickstart-keeper.git
git push -u origin main
```

Or, with the GitHub CLI (creates the repo for you):

```bash
git init && git add . && git commit -m "feat: quickstart-keeper skill"
gh repo create quickstart-keeper --public --source=. --remote=origin --push
```

## Tag a release (optional)

```bash
git tag -a v1.0.0 -m "quickstart-keeper v1.0.0"
git push origin v1.0.0
```
