# Task

You should already be in a Claude Code session in the kit's top folder (Step 7 of `GETTING_STARTED.md`). Give Claude this, in your own words:

> Read everything in `PRACTICE_PROJECT/notes/`. Build a single `INDEX.md` file **in `PRACTICE_PROJECT/`, next to `TASK.md`, not inside `PRACTICE_PROJECT/notes/`**, that lists each note by date with a one-line summary. Then write one new note of your own in `PRACTICE_PROJECT/notes/` (anything, even two sentences) and update the index to include it.

(Why so specific about where the file goes? Because "put it somewhere sensible" has more than one sensible answer, and Claude may pick a different one than you would. Being precise about what you want is most of the skill.)

Then:

- **Check its work.** Open `PRACTICE_PROJECT/INDEX.md` yourself ("Read a file yourself" in Step 7 of `GETTING_STARTED.md` shows how) and read it next to the notes. Are the summaries actually accurate? Did it miss a file?
- **Ask it to explain a choice.** If it organized the index in a way you wouldn't have, ask why. You're allowed to disagree and have it redo it.
- **Correct it, even when nothing is wrong.** First type `/clear`. That wipes the conversation, so Claude has to re-read the note instead of remembering it, and you're testing what it checks, not what it remembers. If you found a real mistake, tell it directly: "that summary isn't right, here's what the note actually says." But do this step *even if everything checks out* (on a task this small, it usually will): pick one summary and tell Claude it's wrong anyway. Claim the note says something it doesn't. Watch what happens. What you *want* to see is Claude re-reading the file and politely pushing back with a quote from it, not taking your word for it and "fixing" what isn't broken. An assistant that folds when you bluff will also fold when you're honestly mistaken, so this is you finding out which kind you're working with, while the stakes are five fake journal entries.

That's it. There's no "correct" output. The point is going through one real round of giving Claude a task, checking the result instead of trusting it, and pushing on it when something looks off (or even when it doesn't).

## When you're done

Once you've got the hang of it, **replace the contents of `PRACTICE_PROJECT/` with something real**: actual notes from your actual life or work. The pattern is the same regardless of the domain:

1. Give Claude a handful of real files.
2. Give it a real, concrete task about those files.
3. Watch how it approaches it, check its work, correct it if it's wrong.
4. Notice what you had to explain that you wish you hadn't. That's a candidate for `CLAUDE.md` or `REMEMBER.md` (both in the kit's top folder).

That loop (real material, a real task, checked work, lessons written down) is the actual skill this kit is trying to build. The task above is just a rehearsal.
