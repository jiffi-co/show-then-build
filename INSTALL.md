# Installing show-then-build

Three ways. Pick one. All of them install at the user level, so the skill works in every project.

After any of them, start a fresh Claude Code session so it loads.

## 1. Ask Claude Code to install both skills (recommended)

show-then-build hands its build step to [build-then-break](https://github.com/jiffi-co/build-then-break), so they are better together. Paste this into Claude Code:

```text
Please install two Claude Code skills from these public repos:
https://github.com/jiffi-co/show-then-build
https://github.com/jiffi-co/build-then-break

Install both at the user level so they work in every project, and set them up so you always use them:

1. Before you install anything, read each skill's files and tell me in plain English what each one does and whether anything in them runs commands or touches my files.

2. Download each repo to a temporary folder (git clone, or the zip from GitHub if git isn't available). Copy skills/show-then-build to ~/.claude/skills/show-then-build/ and skills/build-then-break to ~/.claude/skills/build-then-break/, so each SKILL.md sits directly in its folder with its other folders beside it. On Windows, ~ is my user folder. If either skill is already there, show me what would change and ask before replacing it. Delete the temporary folders when you're done.

3. Add this section to ~/.claude/CLAUDE.md. If the file doesn't exist, create it. If it does exist, add the section at the end and don't change anything already in it.

   ## Show, then build, then break
   Before adding, changing, redesigning or fixing something that already exists, use the show-then-build skill and follow it. Show me a preview and wait for my yes before touching the real files. Tiny edits skip the preview, as the skill describes.

   For any task that writes, edits, refactors, debugs or reviews code, and before calling any plan or analysis done, use the build-then-break skill and follow it. Match effort to the stakes as the skill describes.

4. Show me the final folder structure and the exact section you added to CLAUDE.md, then tell me to start a fresh session so it all loads.
```

## 2. Ask Claude Code to install just this one

```text
Please install the show-then-build skill for Claude Code from this public repo:
https://github.com/jiffi-co/show-then-build

Install it at the user level so it works in every project, and set it up so you always use it:

1. Before you install anything, read the skill's files and tell me in plain English what it does and whether anything in it runs commands or touches my files.

2. Download the repo to a temporary folder (git clone, or the zip from GitHub if git isn't available). Copy its skills/show-then-build folder to ~/.claude/skills/show-then-build/ so SKILL.md sits directly in that folder, with the assets/ and references/ folders beside it. On Windows, ~ is my user folder. If a show-then-build skill is already there, show me what would change and ask before replacing it. Delete the temporary folder when you're done.

3. Add this section to ~/.claude/CLAUDE.md. If the file doesn't exist, create it. If it does exist, add the section at the end and don't change anything already in it.

   ## Show, then build
   Before adding, changing, redesigning or fixing something that already exists, use the show-then-build skill and follow it. Show me a preview and wait for my yes before touching the real files. Tiny edits skip the preview, as the skill describes.

4. Show me the final folder structure and the exact section you added to CLAUDE.md, then tell me to start a fresh session so it all loads.
```

## 3. Do it by hand

Mac or Linux, in a terminal:

```sh
git clone --depth 1 https://github.com/jiffi-co/show-then-build /tmp/show-then-build
mkdir -p ~/.claude/skills
cp -R /tmp/show-then-build/skills/show-then-build ~/.claude/skills/
rm -rf /tmp/show-then-build
```

Windows, in PowerShell:

```powershell
git clone --depth 1 https://github.com/jiffi-co/show-then-build "$env:TEMP\show-then-build"
New-Item -ItemType Directory -Force "$env:USERPROFILE\.claude\skills" | Out-Null
Copy-Item -Recurse -Force "$env:TEMP\show-then-build\skills\show-then-build" "$env:USERPROFILE\.claude\skills\"
Remove-Item -Recurse -Force "$env:TEMP\show-then-build"
```

Then add this to the end of `~/.claude/CLAUDE.md` (create the file if it isn't there):

```markdown
## Show, then build
Before adding, changing, redesigning or fixing something that already exists, use the show-then-build skill and follow it. Show me a preview and wait for my yes before touching the real files. Tiny edits skip the preview, as the skill describes.
```

## Check it worked

You should have:

```text
~/.claude/skills/show-then-build/
├── SKILL.md
├── assets/
│   └── preview-template.html
└── references/
    └── worked-example.md
```

In a fresh Claude Code session, ask: "Which skills do you have?" You should see show-then-build in the list.

To try it, open a project and ask for a change you'd want to see first, for example "make the home page easier to scan on a phone". You should get a preview page before anything in the project changes.

## Removing it

Delete the `~/.claude/skills/show-then-build` folder and remove the "Show, then build" section from `~/.claude/CLAUDE.md`.
