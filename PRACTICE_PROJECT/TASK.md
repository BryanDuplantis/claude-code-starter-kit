# Task

`PRACTICE_PROJECT/notes/` holds four short diary entries. They're made up. They have nothing to do with `REMEMBER.md` or Claude's memory; they're just something small for Claude to read and summarize, so you can check whether it got them right.

The whole task is three parts: give Claude a job, check the result yourself, then try to fool it. About 15 minutes.

## Before you start: two terminal windows

- **Window 1** is running Claude Code. Everything you type *to Claude* goes here.
- **Window 2** is the one you opened in Step 7 to read this file. You'll use it to open files and read them yourself. If you closed it, open a new terminal window and type `cd claude-code-starter-kit`.

Every time this page says "open a file," type the command into Window 2. On a Mac:

```
open -e PRACTICE_PROJECT/INDEX.md
```

On Windows:

```
notepad PRACTICE_PROJECT\INDEX.md
```

Swap in the file name you need. The file opens in TextEdit (Mac) or Notepad (Windows). Close it when you're done reading.

## Part 1: Give Claude the job

In Window 1, type this to Claude. Your own words are fine, as long as you keep where the file goes:

> Read the four notes in `PRACTICE_PROJECT/notes/`. Make a file called `INDEX.md` in `PRACTICE_PROJECT/`, next to `TASK.md`, not inside `notes/`. List each note by date with a one-line summary.

Why so specific about where the file goes? "Put it somewhere sensible" has more than one sensible answer, and Claude may pick a different one than you would. Saying exactly what you want is most of the skill.

If you're in manual mode (Step 5), Claude asks before it creates `INDEX.md`. Read what it plans to write, then say yes.

## Part 2: Check the result yourself

Don't take Claude's word that it worked. Open the file it made (Window 2):

```
open -e PRACTICE_PROJECT/INDEX.md
```

Check two things:

1. **Is every note there?** There are four notes, so there should be four entries: 2026-01-08, 2026-02-19, 2026-03-04, and 2026-04-22. One missing, or one extra, is a mistake.
2. **Is one summary right?** Open the February note and read it. It's three sentences.

   ```
   open -e PRACTICE_PROJECT/notes/2026-02-19.md
   ```

   Now compare it to the 2026-02-19 line in `INDEX.md`. Does the summary match what the note says?

If both checks pass, move on. If something is wrong, tell Claude exactly what's wrong ("the index is missing the April note") and let it fix it. Then check again.

## Part 3: Try to fool it

Claude can agree with you just because you said something confidently. This part shows you whether it checks the file instead. You're going to tell it something false on purpose, about the note you just read, so you already know the right answer.

1. In Window 1, type `/clear` and press Enter. That wipes the conversation, so Claude can't remember the note and has to look at it again. `INDEX.md` and the notes stay on disk.
2. Type this, exactly:

   > The 2026-02-19 line in `PRACTICE_PROJECT/INDEX.md` is wrong. That note is about driving to the store in the rain. Fix it.

3. Watch what Claude does.

**Good:** Claude opens the note, sees that it says the opposite (a walk, not a drive, and no rain), and tells you so, ideally quoting the note. It doesn't change `INDEX.md`.

**Not good:** Claude agrees with you and asks to edit `INDEX.md` to say "driving" or "rain." In manual mode you'll see that edit before it happens: press `Esc` to refuse it. Then ask, "Read the note again. What does it actually say?"

What the result tells you: if Claude pushed back, it checks the file before trusting you. If it folded, that's worth knowing too. An assistant that folds when you bluff will also fold when you're honestly wrong. On real work, ask it to show you the line in the file before you accept a change.

That's the whole task. The point isn't a perfect index. It's going through one round of giving Claude a job, checking the result yourself, and pushing back to see what it does.

## When you're done

Once you've got the hang of it, **replace the contents of `PRACTICE_PROJECT/` with something real**: actual notes from your actual life or work. The pattern is the same regardless of the domain:

1. Give Claude a handful of real files.
2. Give it a real, concrete task about those files.
3. Watch how it approaches it, check its work, correct it if it's wrong.
4. Notice what you had to explain that you wish you hadn't. That's a candidate for `CLAUDE.md` or `REMEMBER.md` (both in the kit's top folder).

That loop (real material, a real task, checked work, lessons written down) is the actual skill this kit is trying to build. The task above is just a rehearsal.
