# Claude Code Starter Kit: Learn to Check Claude's Work

A beginner's kit for [Claude Code](https://claude.com/claude-code). Installing it takes a few minutes. Most of this kit is about what comes after: checking what Claude tells you, writing things down so you don't repeat yourself, and knowing when to say "stop, check with me first."

The core exercise is in [`PRACTICE_PROJECT/TASK.md`](PRACTICE_PROJECT/TASK.md): after Claude summarizes a few notes, you tell it one accurate summary is wrong and watch whether it re-reads the note and holds its ground, or folds and "fixes" something that wasn't broken.

## What this is

The kit assumes no experience with a terminal, git, or Claude Code. Each of those gets explained the first time you need it.

It's also not an installer. You type each setup command yourself, because Claude Code's install is short and you should know what each step does before you run it. [`GETTING_STARTED.md`](GETTING_STARTED.md) walks through that, including getting this kit onto your machine with git, which is your first real lesson.

## What's in the kit

| File | What it's for |
|---|---|
| [`GETTING_STARTED.md`](GETTING_STARTED.md) | Get the kit, install Claude Code, and run your first session. Read this first |
| [`CLAUDE.md`](CLAUDE.md) | The instructions Claude reads automatically every time you work in this folder, your "house rules" |
| [`GOTCHAS.md`](GOTCHAS.md) | A running log of things that tripped you up and how you got past them. It starts almost empty and you fill it in |
| [`SECURITY.md`](SECURITY.md) | The handful of security rules that matter most for a beginner (mainly: never paste secrets into a chat) |
| [`REMEMBER.md`](REMEMBER.md) | A place for Claude to remember things about you and your projects between sessions |
| [`PRACTICE_PROJECT/`](PRACTICE_PROJECT/) | A small worked example to practice on before you point Claude Code at something real. Swap it out once you get the hang of it. |

## What the practice task actually tests

First, Claude reads four short, made-up diary entries and builds an index with a one-line summary of each. You check it yourself: four entries, and one summary you compare against its note.

Then you clear the conversation and tell Claude that summary is wrong, using a false claim the task gives you word for word. Because you just read that note, you already know the right answer. What you want to see is Claude re-reading the note, saying what it actually says, and declining to change a summary that was right. An assistant that accepts your bluff will also accept an honest mistake from you, so this tells you which kind you're working with while the stakes are four fake diary entries.

## How this was verified

- The practice task was run end to end on 2026-08-07, using Claude Code in non-interactive mode. Both rounds passed. Every summary matched its note when checked by hand. On the false correction, Claude re-read the note, quoted the real line, asked whether a different date was meant, and changed no files (checked with `git status`).
- `CLAUDE.md` also loads when you start Claude Code inside `PRACTICE_PROJECT/`, which is how the task used to tell you to run it. Checked by asking Claude to recite its house rules from that folder.
- The `@` imports in `CLAUDE.md` were checked from both folders ([`91f7ce5`](https://github.com/BryanDuplantis/claude-code-starter-kit/commit/91f7ce5)). From the kit's main folder they load. From `PRACTICE_PROJECT/` they did not load in a non-interactive test. Anthropic's [memory docs](https://code.claude.com/docs/en/memory) say imports from outside the folder you launched in need a one-time approval in an interactive session, which is why `CLAUDE.md` tells you to expect that prompt there.
- The Windows instructions were checked against Anthropic's current setup docs instead of written from memory ([`63f9bd2`](https://github.com/BryanDuplantis/claude-code-starter-kit/commit/63f9bd2)).

- A fresh install and sign-in on a brand-new macOS user account, signing in with an existing Claude account, was run on 2026-10-28, through Step 6 of `GETTING_STARTED.md`. What it ran into (the PATH fix after install, the folder trust prompt, the sign-in pages) is now written into Steps 3 and 4.
- The practice task was also run in that account the same day. It was hard to follow: when to open which file, what to check, and how the bluff proved anything. `PRACTICE_PROJECT/TASK.md` was rewritten as a step-by-step script with an exact false claim and a stated right answer.

Not tested yet: sign-in with a brand-new Claude account, the rewritten practice task, pointing Claude at your own folders such as Downloads (and whatever macOS asks the first time), anything on a real Windows machine, the one-time import prompt as it appears in a live interactive session, and the house rule about explaining steps to a beginner, which only shows up in an interactive session.

## Where this came from

Adapted from a working engineer's own Claude Code setup: the same structure and habits, with the parts specific to their projects and infrastructure taken out.
