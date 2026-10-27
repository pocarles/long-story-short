---
name: long-story-short
description: Ends a reply with a short, plain-words summary of where things stand and the one next step to take. Use at the end of any reply that does work or explains something.
---

The answer above the block stays as detailed as usual. The block lets the user skip the details,
read 10 lines, and either learn where things stand or reply "Do it".

## Format

```
---

**Long story short**

<the result, in terms the user cares about, 1 to 3 lines>

<what it means for them and what is left, 1 to 3 lines, or short bullets for 3+ items>

**Next:** <one task>. <why it is the obvious next step, one sentence>.
```

- At most 10 lines of text (about 120 words), not counting blank lines. Count before sending.
- Blank line between every paragraph. Bold only the two labels.
- No headers, tables, or code blocks inside. Backticks only for something the user has to type
  or click.
- No em dashes.

## Say it plainly

- Write for someone switching back in from other work: they haven't read the reply above, and
  they may not be technical.
- Write the block fresh instead of shrinking the reply above. Don't carry over its labels
  (ticket or PR numbers, branch, file, test or tool names) unless the user needs one to act.
- Open with what changed for the user, or the answer to what they asked, not with the state of
  the work (branches, checks, review rounds).
- Call things by what they do for the user ("the Revenue page"), not by their technical name.
- When an idea is abstract, one short comparison from the user's world helps more than a precise
  term.
- Explain any technical word you can't avoid, in a few plain words, the first time. A word the
  user uses themselves is already plain to them: keep it.
- Keep every risk and anything not checked, said as what could go wrong for the user. Simpler is
  not vaguer.
- Zoom to the right level: the task when mid-task, the session or project when a task just ended.
- If it isn't obvious why this step comes now, add one line saying why.
- Too much for 10 lines? Drop the least important point, never the plain explanation of a point
  you keep.
- Before sending, check: could the user repeat it to someone who wasn't there, and say yes or no
  to Next without reading anything above?

## Next

- One task, never a menu: the one that follows most naturally from what was just done.
- Never propose work the current request still owes. Do it first. The block is not a way to stop
  early.
- "Do it" approves the Next line exactly as written. If it includes a step that needs explicit
  approval (merging, deploying to production, touching production data, sending or publishing,
  spending money), name that step plainly, e.g. "merge and deploy to production".
- If the work is blocked on a decision only the user can make, Next is that decision, worded so
  "Do it" means your recommended answer.
- Task finished and nothing left to do? Next is "archive this session", but only when nothing
  would be lost: every change committed, no PR or branch waiting on this session, nothing
  running in the background. Otherwise, Next is whatever makes it safe to close.
- Answered a question mid-conversation with nothing to do next? Leave the Next line out.
- Never propose deleting a session.
- Don't repeat a next task the user declined unless new evidence makes it important.

## Example

```
---

**Long story short**

The login bug is fixed: when a session runs out, you now land back on the sign-in page instead
of a blank screen. I broke it on purpose to confirm the fix is what solves it, and a check now
catches it if it ever comes back.

Not checked yet: the mobile app. It handles logins on its own, so it may have the same bug.

**Next:** check the mobile app for the same bug. It shares the cause, so it likely has it too.
```

## When to skip it

- Replies of 5 lines or less: the block would only repeat them.
- Never in code, commit messages, PR descriptions, documents, or messages to other agents.

## Claude desktop app

If the reply ends with a next-step box (`wrap_up`), it proposes the same task, and its first
button must start the task when clicked: use the app `action` when one fits (commit, open a PR,
merge, archive), otherwise a "Do it" reply button whose `message` is the full task as an
instruction to you. The message is never empty or just "Do it".

## Codex app

- There is no next-step box: the block and a typed "Do it" do the job.
- If Next is a decision only the user can make and `request_user_input` is available, ask it
  there, recommended answer first, so they can click instead of typing.
- When the user approves archiving: if this task made a worktree, archive it first with
  `archive_worktree` (it keeps a copy of unsaved work you can restore), then archive this thread
  with `set_thread_archived`, no thread id.

## /long-story-short

Give the block for the whole session (or the project, if asked). Same 10-line limit.

Write in the user's language.
