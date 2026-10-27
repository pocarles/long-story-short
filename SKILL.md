---
name: long-story-short
description: Ends a reply with a short, plain-words summary of where things stand and the one next step to take. Use at the end of any reply that does work or explains something.
---

The answer above the block stays as detailed as usual. The block is for a tired reader at the end
of a long day: they skip the details, read a few easy lines, and either understand where things
stand or reply "Do it". Every word they have to decode costs them energy. Spend it for them.

Explain it the way one person explains something to another over coffee. Don't report it. A
report lists facts and leaves the reader to work out what they mean. An explanation says what
happened, what it means for them, and what saying yes will do.

## Format

```
---

**Long story short**

<what happened, in plain words, 1 or 2 short sentences>

<what it means for them: what they can do now, what is at risk or not checked, 1 or 2 sentences,
or short bullets for 3+ items>

**Next:** <one task>. <why it comes now, and what saying yes changes for them>.
```

- Aim for 4 to 8 lines, about 60 to 100 words. Never more than 10 lines.
- Plain beats short. If explaining a point takes one more line, use it. Cut a point before you
  cut its explanation.
- Blank line between every paragraph. Bold only the two labels.
- No headers, tables, or code blocks inside. Backticks only for something the user has to type
  or click.
- No em dashes.

## Explain, don't report

- **Every fact gets its "so what".** "It's only on your Mac" is a fact. "Nobody else has it yet,
  and it isn't backed up" is what it means. Say the meaning, not just the fact.
- **Compare it to something they know.** When an idea is abstract, one short comparison from the
  user's world (their business, their products, the tools they use every day) lands faster than
  any precise term.
- **Translate developer words.** Repo, branch, commit, pull request, merge, deploy, worktree,
  migration, API, cache and the like: swap them for what they do ("put it up for review", "make
  it live", "a separate copy to work in"), or explain them in a few words the first time. A word
  counts as plain only if the user wrote it themselves. Words from a button message, a plan or
  any other text you wrote don't count, even when it was sent in the user's name.
- **Short sentences.** One idea per sentence, about 15 words at most. Don't chain clauses with
  "while", "because", "so" and "which" in one sentence: split it.
- **No codes.** Leave out order, ticket, invoice, PR, branch, file, test and tool names. Name the
  thing by who or what it is: "the Dupont order", "the Revenue page", "the login bug". Keep a code
  only if the user must type or find it to act, and then only once.
- **Few numbers.** At most two in the block, rounded ("about €26k"), and only the ones the user
  needs to decide. Say what a number means ("Revenue shows about €8k too little") rather than
  listing readings ("Revenue reads $412,880").
- **Open with what changed for the user**, or the answer to what they asked, not with the state
  of the work (branches, checks, review rounds).
- **Write it fresh.** Don't shrink the reply above; it is full of labels the user hasn't read.
- **Keep every risk** and anything not checked, said as what could go wrong for the user. Simpler
  is not vaguer.
- Zoom to the right level: the task when mid-task, the session or project when a task just ended.
- Before sending, read it as if aloud. Could the user repeat it to someone who wasn't there? Could
  they say yes or no to Next without reading anything above? If any sentence makes them stop and
  decode, rewrite it.

## Next

- One task, never a menu: the one that follows most naturally from what was just done.
- Always say why it comes now, and what saying yes changes for the user: what will happen, and
  anything that will not happen yet ("Nothing reaches the team until you say so").
- Never propose work the current request still owes. Do it first. The block is not a way to stop
  early.
- "Do it" approves the Next line exactly as written. If it includes a step that needs explicit
  approval (merging, deploying to production, touching production data, sending or publishing,
  spending money), name that step plainly, e.g. "make it live for every customer".
- If the work is blocked on a decision only the user can make, Next is that decision, worded so
  "Do it" means your recommended answer.
- Task finished and nothing left to do? Next is "archive this session", but only when nothing
  would be lost: every change committed, no PR or branch waiting on this session, nothing
  running in the background. Otherwise, Next is whatever makes it safe to close.
- Answered a question mid-conversation with nothing to do next? Leave the Next line out.
- Never propose deleting a session.
- Don't repeat a next task the user declined unless new evidence makes it important.

## Examples

```
---

**Long story short**

The login bug is fixed. When someone stays away too long, they now land on the sign-in page
instead of a blank screen. A check will catch it if it ever comes back.

Not checked: the mobile app. It handles logins on its own, like a second door with its own lock,
so it may have the same bug.

**Next:** check the mobile app for the same bug. It likely shares the cause, and checking changes
nothing for your users.
```

A report, the kind of block to avoid:

```
The team's copy of the skill is updated, but only on your Mac.

It can't get a pull request yet, because this plugins repo isn't on GitHub.

**Next:** create a private GitHub repo for it and open the pull request.
```

The same news, explained:

```
The team's version of the skill is updated, but it only exists on your Mac. Nobody on the team
has it yet, and it isn't backed up anywhere.

To review it and later send it to the team, it needs a home online, like the rest of your code
has. This folder never got one.

**Next:** give it that private home online and put the change up for review. Nothing reaches the
team until you say so.
```

Too dense:

```
**Next:** fix ORD-5520's price in the CRM. It's €18,400, while its €31,200 invoice is about
€26k before tax because it includes the shipping, so Revenue still undercounts the Dupont order.
```

Easy to read:

```
**Next:** fix the price of the Dupont order. The app lists it about €8k below its invoice, so
Revenue shows too little. Nothing else changes.
```

## When to skip it

- Replies of 5 lines or less: the block would only repeat them.
- Never in code, commit messages, PR descriptions, documents, or messages to other agents.

## Claude desktop app

The next-step box (`wrap_up`) is called before your closing message, so decide the Next line
first, then call the box, then write the reply and the block.

- **Whenever the block has a Next line, the box must carry a question and a button for it**, even
  when the task you were asked to do is finished. Next is always something the user has to approve,
  so it is always pending. A box with only a recap shows no button: that is the bug to avoid.
- The box's text follows the same rules as the block: plain words, no codes, no developer words.
  Its recap says where things stand in one or two sentences. Don't make it a third, more
  technical copy of the block.
- `ask`: the Next line as a short yes-or-no question in the same plain words, e.g. "Fix the price
  of the Dupont order?".
- First button: the app `action` when one fits (commit, open a PR, merge, archive). Otherwise a
  reply button labeled "Do it" whose `message` is the full task as an instruction to you, with
  the exact names and numbers you'll need (codes are fine there). Keep it under 300 characters:
  the app cuts longer ones. The message is never empty or just "Do it".
- A second "Not now" button is fine. Never a menu of other tasks.
- No Next line (a question answered, nothing to do): recap only, no question.

## Codex app

- There is no next-step box: the block and a typed "Do it" do the job.
- If Next is a decision only the user can make and `request_user_input` is available, ask it
  there, recommended answer first, so they can click instead of typing.
- When the user approves archiving: if this task made a worktree, archive it first with
  `archive_worktree` (it keeps a copy of unsaved work you can restore), then archive this thread
  with `set_thread_archived`, no thread id.

## /long-story-short

Give the block for the whole session (or the project, if asked). Same rules and length.

Write in the user's language.
