# Getting Started

Read this whole file before you touch a terminal. It's short.

## Before you install anything

Claude Code is a command-line tool — you type instructions instead of clicking buttons. That's the whole trick behind why it's powerful: it can read your files, write code, run programs, and fix its own mistakes, because it's operating in the same environment you are, not a sandboxed chat window.

That also means it's worth understanding each setup step instead of running something that does it all silently. You're not disabling anything by doing it by hand — every step below is genuinely this short. Doing it once means the next time something looks broken, you'll actually recognize what changed.

## Step 1 — Get a terminal open

- **Windows:** open PowerShell (search "PowerShell" in the Start menu).
- **Mac:** open Terminal (search "Terminal" in Spotlight).

You'll be typing commands here for the rest of setup. Nothing you type here is sent anywhere until you say so.

## Step 2 — Get git, then get this kit

Git is the tool that copies (and later, updates) this kit from wherever it's hosted onto your machine. If you don't already have it:

- **Windows:** install [Git for Windows](https://git-scm.com/downloads/win). This is only to get the kit onto your machine — you can keep using plain PowerShell for everything else. (Git for Windows also gives Claude Code an optional extra capability later on, but you don't need to think about that now.)
- **Mac:** open Terminal and type `git --version` — if it's not installed, macOS will prompt you to install the developer command line tools.

New to the terminal entirely? Claude Code's own [terminal guide](https://code.claude.com/docs/en/terminal-guide) walks through the absolute basics for both Windows and Mac before you go any further.

Then, in your terminal:

```
git clone https://github.com/BryanDuplantis/claude-code-starter-kit.git
cd claude-code-starter-kit
```

You now have your own local copy. `git clone` downloaded it; `cd` moved your terminal into that folder. Everything else happens from inside it.

## Step 3 — Install Claude Code

Go to **[claude.com/claude-code](https://claude.com/claude-code)** and follow the current install instructions for your OS.

We're deliberately not pasting exact install commands into this file. Claude Code changes fast — install methods that were correct a few months ago (npm-based installs, for example) have already gone stale once. The docs page is always more current than anything written here. If this file and the docs page ever disagree, trust the docs page.

Don't want a terminal-based tool at all? There's also a [Desktop app](https://claude.com/download) that gives you Claude Code without typing commands. This kit assumes the terminal version, because learning the terminal a little is part of the point — but the app exists if you want to try Claude Code itself first before committing to that.

**Before you go further, confirm the install actually worked.** Open a fresh terminal and run:

```
claude --version
```

You should see a version number print out (something like `2.1.211 (Claude Code)`). If instead you get "command not found" or a similar error, don't move on — that's a real problem to solve, not something to push past. `claude doctor` gives a more detailed diagnosis if you're stuck.

## Step 4 — Log in

The installer will prompt you to authenticate — this opens a browser window and links Claude Code to your Claude account. **You need a paid Claude plan (Pro or above) for this to work — the free claude.ai plan does not include Claude Code access.** Confirm this before you get this far, so it's not a surprise at the login screen.

## Step 5 — Open this folder in Claude Code

Back in your terminal, from inside the `claude-code-starter-kit` folder:

```
claude
```

You're now in a live Claude Code session, inside this folder.

## Step 6 — Have it introduce itself

Type this into the session:

```
Read CLAUDE.md and introduce yourself — what are your house rules, and what should I know before we start?
```

This is the most important step in the whole kit. `CLAUDE.md` is a file Claude reads automatically at the start of every session in this folder — it's not magic, it's just a text file with instructions, and you can read it yourself any time in a normal text editor. Having Claude explain it back to you is a good way to confirm it actually loaded and to see the house rules in its own words.

## Step 7 — Try the practice project

Head to [`PRACTICE_PROJECT/README.md`](PRACTICE_PROJECT/README.md) next. It's a small, low-stakes task designed to get you through one real back-and-forth with Claude Code before you try it on something that matters.

## If something breaks

Check [`GOTCHAS.md`](GOTCHAS.md) first — and once you've solved a problem yourself, add it there. That's the whole point of the file.
