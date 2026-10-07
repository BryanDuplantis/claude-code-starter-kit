# Security

Short version: **don't type secrets into a chat window, and don't hand out more access than a task needs.** Everything below is detail on those two ideas.

## The rule that matters most

**Never paste a password, API key, token, or any credential directly into a Claude conversation**, even in a local session, even if Claude asks for it. See `GOTCHAS.md` for why: chats aren't guaranteed to disappear.

If something needs a credential:
- Store it somewhere private on your machine (a password manager, an environment variable, a config file that isn't checked into git) and let Claude read *that location*. Never type the value itself into the chat.
- If Claude ever suggests pasting a secret directly as the easy option, that's the wrong default, so ask it for the safer path instead.

## If a secret does leak

Don't try to "clean up" the conversation. Assume the leaked credential is now compromised. **Rotate it** (change the password, regenerate the API key) immediately, then continue. The conversation can't be un-said; the credential can be changed.

## Least privilege, in plain terms

When you connect Claude to something else (email, a cloud drive, a calendar, an API), give it the narrowest access that does the job:

- Read-only when you're not asking it to change anything.
- A scoped/limited API key over a full-admin one, if the service offers the choice.
- Don't leave a powerful connection turned on "just in case" after you're done using it for that task.

## Before running something you don't fully understand

If Claude suggests running a command and you don't know what it does, ask it to explain first, especially anything involving `delete`, `remove`, `rm`, `drop`, or anything that sounds like it sends something externally. This isn't about not trusting Claude; it's the same habit you'd want with any tool that can take real action on your behalf.
