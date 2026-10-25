---
name: long-story-short
description: Ends substantive replies with a short "Long story short" block, after the full answer, that says in plain words where things stand and proposes the one obvious next task, so the user can reply "Do it" to start it. Use on any reply that does work or explains something; on /long-story-short, give the block for the whole session.
---

The answer above the block stays as detailed as usual. The block lets the user skip the details,
read 10 lines, and either learn where things stand or reply "Do it".

## Format

```
---

**Long story short**

<what just happened, 1 to 3 lines>

<what it means and what is left, 1 to 3 lines, or short bullets for 3+ items>

**Next:** <one task>. <why it is the obvious next step, one sentence>.
```

- At most 10 lines of text, not counting blank lines.
- Blank line between every paragraph. Bold only the two labels.
- No headers, tables, or code blocks inside. Backticks for file or command names are fine.

## Where things stand

- Plain words, as if explaining to a friend over coffee. Explain any technical word you can't
  avoid.
- Say what changed, what works, and what is left or not verified. Simpler is not vaguer: keep
  every risk the user needs to know.
- Zoom to the right level: the task when mid-task, the session or project when a task just ended.
- If it isn't obvious why this step comes now, add one line saying why.

## Next

- One task, never a menu: the one that follows most naturally from what was just done.
- Never propose work the current request still owes. Do it first. The block is not a way to stop
  early.
- "Do it" approves the Next line exactly as written. If it includes a step that needs explicit
  approval (merging, deploying to production, touching production data, sending or publishing,
  spending money), name that step plainly, e.g. "merge and deploy to production".
- If the work is blocked on a decision only the user can make, Next is that decision, worded so
  "Do it" means your recommended answer.
- Nothing worth doing next (a plain question, fully answered)? Leave the Next line out.
- Don't repeat a next task the user declined unless new evidence makes it important.

## Example

```
---

**Long story short**

The login bug is fixed: expired sessions now send you back to the sign-in page instead of a blank
screen. I reproduced it first, then fixed it, and the new test fails without the fix.

Not checked yet: the mobile app, which uses its own session code.

**Next:** check the mobile app for the same bug. It shares the cause, so it likely has it too.
```

## When to skip it

- Replies of 5 lines or less: the block would only repeat them.
- Never in code, commit messages, PR descriptions, documents, or messages to other agents.

## Claude desktop app

If the reply ends with a next-step box (`wrap_up`), it proposes the same task, and its first
button must start the task when clicked: use the app `action` when one fits (commit, open a PR,
merge), otherwise a "Do it" reply button whose `message` is the full task as an instruction to
you. The message is never empty or just "Do it".

## /long-story-short

Give the block for the whole session (or the project, if asked). Same 10-line limit.

Write in the user's language.
