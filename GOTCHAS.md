# Gotchas

A running log of things that looked broken, why, and how they got fixed. Append-only: once something's in here, don't rewrite it; if it stops being true, mark it superseded instead of deleting it. The point isn't a clean file, it's a true history.

Format per entry:

```
## YYYY-MM-DD: Short title
**Symptom:** what looked broken from the outside.
**Root cause:** what was actually happening.
**Fix:** what to do about it.
```

Two entries below to start. They're real ones, carried over from the engineer whose setup this kit is adapted from. Everything after this is yours.

---

## Seed: Secrets pasted into a chat don't disappear
**Symptom:** Pasted a password or API key into a Claude conversation "just this once," assuming it's gone once the window closes.
**Root cause:** Conversations aren't ephemeral. They can get saved, searched, or referenced later, on purpose or by accident. Once a secret is in a transcript, you can't un-paste it; the only real fix is to change the credential itself.
**Fix:** Never paste secrets into chat, even when it feels like the fast path. If something needs a password or key, store it somewhere private (see `SECURITY.md`) and point Claude at *that*. Don't type the value itself. If it already happened: change the credential now, don't wait.

---

## Seed: "It finished with no error" isn't proof it worked
**Symptom:** Ran something, it completed cleanly, no red text, and later found out it hadn't actually done the thing it was supposed to.
**Root cause:** A command can exit "successfully" while silently doing nothing useful: wrong file, wrong folder, a step that got skipped quietly. A clean finish only means nothing *crashed*; it doesn't mean the real-world result showed up.
**Fix:** Before calling something done, check for the actual evidence: open the file, look at the output, confirm the thing you expected to see is really there. Ask Claude to show you the proof, not just report success.

---
