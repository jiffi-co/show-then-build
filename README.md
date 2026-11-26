<p align="center">
  <img src="assets/banner.png" alt="Show, then build. A Claude Code skill. See the change before it exists, say yes, then get exactly that built." width="100%">
</p>

<p align="center">
  <a href="LICENSE"><img alt="Licence: MIT" src="https://img.shields.io/badge/licence-MIT-0f063c"></a>
  <img alt="Works with Claude Code" src="https://img.shields.io/badge/works%20with-Claude%20Code-599cff">
  <a href="https://github.com/jiffi-co/build-then-break"><img alt="Pairs with build-then-break" src="https://img.shields.io/badge/pairs%20with-build--then--break-d5e6ff"></a>
  <a href="https://clarityclub.jiffi.co"><img alt="From Jiffi Clarity Club" src="https://img.shields.io/badge/from-Jiffi%20Clarity%20Club-fff58a"></a>
</p>

# Show, then build

The expensive mistake with AI isn't bad code. It's the right code for the wrong thing.

You ask for a change. The AI builds its best guess. You look at it, realise it's not what you meant, and start again.

This skill flips the order. Claude Code shows you the change first, on a page you can open and click. You pick, you answer a few questions, you say yes. Then it builds exactly that, and checks the result against what you approved.

You don't need to be a developer to use it.

## What you get before anything is built

One page, saved in your project, that opens in any browser:

- **Before and after**, side by side.
- **A prototype you can click**, in your product's own look, at desktop and phone width.
- **Two or three options** when there's a real choice, with one recommended and the reason why.
- **A decisions form.** Every open question in one place, with the choices, a recommendation, what each choice changes, and a comment box. Press **Copy my answers** and paste them back.
- **What's not changing**, so nothing gets rebuilt by surprise.

<p align="center">
  <img src="assets/preview-example.png" alt="A preview page made by the skill: what and why, the bookings page before and after, and a clickable prototype with three options." width="80%">
</p>

<p align="center"><sub>A real preview from testing. The request was "front desk want to see just today's bookings, and the cancelled ones clutter the list. Not sure if that should be tabs or a dropdown."</sub></p>

## Install it in a minute

Open Claude Code and paste this in. It installs this skill and its partner, [build-then-break](https://github.com/jiffi-co/build-then-break), together.

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

Start a fresh session afterwards. That's it.

Want only this skill, or prefer to do it by hand? See [INSTALL.md](INSTALL.md).

## How the two skills fit

| | show-then-build | build-then-break |
|---|---|---|
| Answers | What should we build? | Is it built right? |
| Runs when | You change something that already exists and there's something to see or decide | Any time code is written, edited or reviewed |
| You do | Look, pick, say yes | Read a short report |

Show always leads into break. Break doesn't need show. A typo or a one-line bug fix skips the preview and goes straight to build-then-break.

## The six steps

It picks a level first, so a small fix stays small.

| Level | When | What happens |
|---|---|---|
| Small | Typo, wording, a config value, a bug with one obvious fix | One-line plan, then build and check. No preview. |
| Standard | A feature or change with one sensible direction | All six steps. |
| Open | A redesign, real choices, "I'm not sure how this should work" | All six steps, plus options and the decisions form. |

1. **Understand.** Restate the problem, read the real current state, note what else it touches. No code.
2. **Show.** The preview page.
3. **Wait.** Nothing in your real files changes until you answer.
4. **Spec and plan.** Written from what you approved, with a "Not shown in the preview" list so anything you haven't seen can't slip through.
5. **Build.** Step by step, each step checked, inside what you approved.
6. **Prove.** Open the real thing in a browser and compare it with the preview, point by point.

The full skill is one short file: [skills/show-then-build/SKILL.md](skills/show-then-build/SKILL.md).

## What's in the box

```text
skills/show-then-build/
├── SKILL.md                      the skill
├── assets/
│   └── preview-template.html     the page every preview starts from
└── references/
    └── worked-example.md         one change, all six steps
```

No scripts to run. No network calls. The preview page is a single file that works offline.

## How it was tested

Three tasks on a small sample project, each run with the skill and without it:

| Task | With the skill | Without it |
|---|---|---|
| A visual change with an open direction | Made a preview with three options and three questions. Real files untouched. | Picked a direction itself and changed the real page straight away. |
| A one-line bug fix | No preview. Fixed it, checked it, three-line reply. | Fixed it too. Nothing to separate them, which is the point: the skill stays out of the way. |
| Approved answers pasted back | Wrote a spec with a "Not shown in the preview" list, built the chosen option, and reported the result against the preview. With build-then-break installed, it also found and fixed three faults before reporting. | Built it well, but with no spec, no comparison with the preview, and two extras nobody had seen. |

The honest cost: the full flow took about eight minutes on the third task, against five without the skill. You spend minutes up front to avoid rebuilding later.

That's one run of each, not a study. Tell us where it falls over.

## Credits

- Based on how the Jiffi team works on changes after the first build.
- Put together by [Jake Shelley](https://github.com/jake-jiffi) at [Jiffi](https://www.jiffi.co) for [Clarity Club](https://clarityclub.jiffi.co), where we help business people build with AI properly.

## Licence

[MIT](LICENSE). Use it, change it, share it.
