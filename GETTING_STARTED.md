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

> **Stuck before Claude Code starts?** Claude Code can't help you until it runs, but Claude in a web browser can. Open [claude.ai](https://claude.ai), paste the exact error text from your terminal (never a password or key), and ask what it means.

**Windows (PowerShell):**

```
irm https://claude.ai/install.ps1 | iex
```

**Mac (or Linux):**

```
curl -fsSL https://claude.ai/install.sh | bash
```

Each one downloads Anthropic's installer from claude.ai and runs it. It shows no progress while it downloads, so give it a minute. On Windows, if you see `'irm' is not recognized`, you're in the older Command Prompt instead of PowerShell; go back to Step 1.

When it finishes, read the last few lines it printed. Look for a section called `Setup notes:`. On a new Mac it often says:

```
Native installation exists but ~/.local/bin is not in your PATH.
```

That note is normal. The installer suggests a fix but doesn't apply it for you. You'll handle it in a moment.

This kit uses the terminal version of Claude Code, installed by the command above. You don't need to download anything from a web page. Anthropic's Claude Code page leads with a big "Download for macOS" button, and the `Claude.dmg` it gives you is the separate [Desktop app](https://code.claude.com/docs/en/desktop). If you already downloaded it, it's fine to leave it installed; Step 4 covers the one place it shows up. The app reads the same `CLAUDE.md` files, but this kit was written and tested with the terminal version only, so the steps below won't match the app screen for screen.

**Before you go further, confirm the install actually worked.** Open a fresh terminal and run:

```
claude --version
```

You should see a version number followed by `(Claude Code)`.

**If you see `zsh: command not found: claude`:** this is common on a new Mac, and it does not mean the install failed. Claude Code is installed in a folder called `~/.local/bin`, and your terminal doesn't know to look there yet. On a Mac, whose default shell is zsh, run these two lines:

```
echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.zshrc
source ~/.zshrc
```

The first line saves the setting for every new terminal window. The second applies it to the window you're in. Neither one prints anything when it works. Now run `claude --version` again. Anthropic's [install troubleshooting page](https://code.claude.com/docs/en/troubleshoot-install#verify-your-path) explains this fix and covers other problems.

**On Linux**, the shell is usually bash, which reads a different file, so follow the [troubleshooting page](https://code.claude.com/docs/en/troubleshoot-install#verify-your-path) instead of the two lines above. **On Windows**, if PowerShell says `claude` is not recognized, follow the same [troubleshooting page](https://code.claude.com/docs/en/troubleshoot-install).

Move on once `claude --version` prints a version number.

## Step 4: Start Claude Code and log in

A fresh terminal starts outside the kit folder, so move back into it first. If you cloned the kit from the folder your terminal opens in, that's:

```
cd claude-code-starter-kit
```

A quick note on where commands go. Commands like `cd` and `claude` are typed at the terminal prompt, the line that ends in `%` on a Mac (on Windows, the PowerShell prompt ends in `>` instead). Commands that start with `/`, like `/context`, are typed inside Claude Code after it starts. If you type a `/` command at the `%` prompt, you'll get an error like `zsh: no such file or directory: /doctor`. That only means it went in the wrong place.

Now start Claude Code:

```
claude
```

**First, a safety question.** Claude Code asks: "Quick safety check: Is this a project you created or one you trust?" **No, exit** is selected by default, so pressing Enter right away closes Claude Code. Press the down arrow to select **Yes, I trust this folder**, then press Enter. That's a safe answer for this kit's folder: you cloned it yourself, and you can read every file in it. Everywhere else, the rule is the opposite: choose **No, exit** for any folder you didn't create or don't fully trust.

**Then, sign in.** Claude Code opens a browser window to link to your Claude account. **You need a paid Claude plan (Pro or higher) for this to work. The free claude.ai plan does not include Claude Code access.** Confirm this before you get this far, so it's not a surprise at the login screen.

On the page that says "Claude Code would like to connect to your Claude chat account," click **Authorize**. Only click it on a page that opened right after you ran `claude` yourself, with claude.ai or claude.com in the address bar. If you didn't just run `claude`, close the tab.

If you have the Desktop app installed, the browser may then say "Finish sign-in in the Claude app." Let the app open, or click **Open Claude** if it doesn't. Then go back to your terminal window.

Once you're signed in, you're in a live Claude Code session, inside this folder. The first screen may show a line saying some MCP servers need authentication. Those are connections from your Claude account to other services. This kit doesn't use them, so you can ignore that line. You may also see a notice about auto mode; Step 5 covers it.

## Step 5: Check which mode it's in

Look at the status line under the box where you type. A new session on a current version of Claude Code usually starts in **auto mode** and shows `⏵⏵ auto mode on`. In auto mode, Claude doesn't stop to ask before each file edit or command; a second model reviews its actions in the background and blocks risky ones, and Anthropic's [permission modes page](https://code.claude.com/docs/en/permission-modes) says plainly that this does not guarantee safety.

In **manual mode** (`⏸ manual mode on`), Claude asks you before most file edits, commands, and network access. Manual mode is a good choice while you're learning. To get there:

- If the status line says auto mode, press `Shift+Tab` once, then check that it now says `⏸ manual mode on`.
- If it shows something else, like `⏵⏵ accept edits on`, keep pressing `Shift+Tab` until it says manual mode.
- If it already says manual mode, leave it.

`Shift+Tab` changes this session only. Each new `claude` starts in the default mode again, which is why `claude --permission-mode manual` exists. Run that instead of plain `claude` to start in manual mode from the beginning. The kit's house rule "ask before doing anything hard to undo" (in `CLAUDE.md`) is a written instruction, and Claude can miss one. Manual mode is enforced by Claude Code itself, so you see most actions before they happen.

## Step 6: Have it introduce itself

Type this into the session:

```
Read CLAUDE.md and introduce yourself. What are your house rules, and what should I know before we start?
```

This is the most important step in the whole kit. `CLAUDE.md` is a file Claude reads automatically at the start of every session in this folder. It's a plain text file with instructions, and you can read it yourself any time in a normal text editor. Having Claude explain it back to you shows you the house rules in its own words.

To check that it loaded from Claude Code's side, type `/context` and press Enter. Look for `CLAUDE.md` in the list under **Memory files**. If it's there, it loaded. If it's missing, Claude can't see your house rules, and that's a problem to fix before you go further.

## Step 7: Try the practice project

It's a small, low-stakes task that gets you through one real back-and-forth with Claude Code before you try it on something that matters.

Read [`PRACTICE_PROJECT/TASK.md`](PRACTICE_PROJECT/TASK.md) yourself (the next section shows how), then type the task to Claude in your own words, in this same session. Don't ask Claude to read `TASK.md` for you. It describes a test you'll run on Claude, and letting Claude read it first would spoil the test.

### Read a file yourself

Claude Code is using your terminal window, so open a second one. On a Mac, press Cmd+N in Terminal. On Windows, open another PowerShell window. Then move into the kit folder:

```
cd claude-code-starter-kit
```

On a Mac, this opens the file in TextEdit:

```
open -e PRACTICE_PROJECT/TASK.md
```

On Windows, this opens it in Notepad:

```
notepad PRACTICE_PROJECT\TASK.md
```

Swap in any file name to read a different one, like `GOTCHAS.md`. Keep this second window open: the practice task uses it to open the files Claude makes.

## If something breaks

Paste the error text into Claude Code, then type:

```
Check GOTCHAS.md for anything like this.
```

Once it's fixed, type:

```
Add what we just fixed to GOTCHAS.md.
```

That's the whole point of the file: the next time it happens, the fix is already written down. If Claude Code isn't running yet, use the claude.ai fallback from Step 3.

To read `GOTCHAS.md` yourself, see "Read a file yourself" in Step 7.
