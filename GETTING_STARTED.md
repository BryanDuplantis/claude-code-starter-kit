# Getting Started

Read this whole file before you touch a terminal. It's short.

## Before you install anything

Claude Code is a command-line tool: you type instructions instead of clicking buttons. That's the whole trick behind why it's powerful: it can read your files, write code, run programs, and fix its own mistakes, because it's operating in the same environment you are, not a sandboxed chat window.

That also means you should understand each setup step instead of running something that does it all silently. Every step below is short. Doing it once by hand means the next time something looks broken, you'll recognize what changed.

## Step 1: Get a terminal open

- **Windows:** open PowerShell (search "PowerShell" in the Start menu).
- **Mac:** open Terminal (search "Terminal" in Spotlight).

You'll be typing commands here for the rest of setup. Nothing you type here is sent anywhere until you say so.

## Step 2: Get git, then get this kit

Git is the tool that copies (and later, updates) this kit from wherever it's hosted onto your machine. If you don't already have it:

- **Windows:** install [Git for Windows](https://git-scm.com/downloads/win). This is only to get the kit onto your machine. You can keep using plain PowerShell for everything else. (Git for Windows also gives Claude Code an optional extra capability later on, but you don't need to think about that now.)
- **Mac:** open Terminal and type `git --version`. If it's not installed, macOS will prompt you to install the developer command line tools.

New to the terminal entirely? Claude Code's own [terminal guide](https://code.claude.com/docs/en/terminal-guide) walks through the absolute basics for both Windows and Mac before you go any further.

Then, in your terminal:

```
git clone https://github.com/BryanDuplantis/claude-code-starter-kit.git
cd claude-code-starter-kit
```

You now have your own local copy. `git clone` downloaded it; `cd` moved your terminal into that folder. Everything else happens from inside it.

## Step 3: Install Claude Code

Type the install command for your system. These are copied from Anthropic's [setup page](https://code.claude.com/docs/en/setup). Claude Code changes often, so if anything here ever differs from that page, trust the page.

**Windows (PowerShell):**

```
irm https://claude.ai/install.ps1 | iex
```

**Mac (or Linux):**

```
curl -fsSL https://claude.ai/install.sh | bash
```

Each one downloads Anthropic's installer from claude.ai and runs it. It shows no progress while it downloads, so give it a minute. On Windows, if you see `'irm' is not recognized`, you're in the older Command Prompt instead of PowerShell; go back to Step 1.

Don't want a terminal-based tool at all? There's also a [Desktop app](https://claude.com/download) that runs Claude Code without typing commands. Anthropic's [Desktop docs](https://code.claude.com/docs/en/desktop) say it reads the same `CLAUDE.md` files as the terminal version, so this kit's house rules should carry over. This kit was written and tested with the terminal version only, though, so the steps below won't match the app screen for screen, and some things (like the one-time approval prompt mentioned in `CLAUDE.md`) may look different there.

**Before you go further, confirm the install actually worked.** Open a fresh terminal and run:

```
claude --version
```

You should see a version number print out (something like `2.1.211 (Claude Code)`). If instead you get "command not found" or a similar error, don't move on. That's a real problem to solve, not something to push past. `claude doctor` gives a more detailed diagnosis if you're stuck.

## Step 4: Start Claude Code and log in

A fresh terminal starts outside the kit folder, so move back into it first. If you cloned the kit from the folder your terminal opens in, that's:

```
cd claude-code-starter-kit
```

Then start Claude Code:

```
claude
```

The first time you run it, Claude Code asks you to log in. It opens a browser window where you sign in and link Claude Code to your Claude account. **You need a paid Claude plan (Pro or higher) for this to work. The free claude.ai plan does not include Claude Code access.** Confirm this before you get this far, so it's not a surprise at the login screen.

Once you're logged in, you're in a live Claude Code session, inside this folder.

## Step 5: Check which mode it's in

Look at the status line under the box where you type. A new session on a current version of Claude Code starts in **auto mode** and shows `⏵⏵ auto mode on`. In auto mode, Claude doesn't stop to ask before each file edit or command; a second model reviews its actions in the background and blocks risky ones, and Anthropic's [permission modes page](https://code.claude.com/docs/en/permission-modes) says plainly that this does not guarantee safety. Press `Shift+Tab` once to switch to **manual mode** (`⏸ manual mode on`), where Claude asks you before most file edits, commands, and network access. Pressing it again cycles through the other modes. To start in manual mode from the beginning, run `claude --permission-mode manual` instead of plain `claude`. Manual mode is a good choice while you're learning. The kit's house rule "ask before doing anything hard to undo" (in `CLAUDE.md`) is a written instruction, and Claude can miss one. Manual mode is enforced by Claude Code itself, so you see most actions before they happen.

## Step 6: Have it introduce itself

Type this into the session:

```
Read CLAUDE.md and introduce yourself. What are your house rules, and what should I know before we start?
```

This is the most important step in the whole kit. `CLAUDE.md` is a file Claude reads automatically at the start of every session in this folder. It's a plain text file with instructions, and you can read it yourself any time in a normal text editor. Having Claude explain it back to you shows you the house rules in its own words.

To check that it loaded from Claude Code's side, type `/context` and press Enter. Look for `CLAUDE.md` in the list under **Memory files**. If it's there, it loaded. If it's missing, Claude can't see your house rules, and that's a problem to fix before you go further.

## Step 7: Try the practice project

Head to [`PRACTICE_PROJECT/README.md`](PRACTICE_PROJECT/README.md) next. It's a small, low-stakes task designed to get you through one real back-and-forth with Claude Code before you try it on something that matters.

## If something breaks

Check [`GOTCHAS.md`](GOTCHAS.md) first, and once you've solved a problem yourself, add it there. That's the whole point of the file.
