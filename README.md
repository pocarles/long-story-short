# Long story short

I run a lot of agent sessions at the same time. Past a few, the agents stop being the slow part.
I am. Every time I switch back to a session, I have to get my head back into it and make the right
call. That's the real bottleneck.

So how do you get a lot more done without draining your mental energy, or being exhausted after a
few hours?

I designed Long story short for exactly that. The agent ends every real reply with ten plain lines
at most, often fewer: where things stand, then the one next step it would take. I read those
lines, decide, and answer "Do it" when I agree. When I need to go deeper before deciding, the full
reply is still right above.

It changed how I work. I used to start struggling beyond five or six parallel sessions. With this
skill, I go up to fifteen before I hit my limits again, and my mental fatigue is mostly under
control.

It looks like this:

> **Long story short**
>
> The login bug is fixed: when a session runs out, you now land back on the sign-in page instead
> of a blank screen. I broke it on purpose to confirm the fix is what solves it, and a check now
> catches it if it ever comes back.
>
> Not checked yet: the mobile app. It handles logins on its own, so it may have the same bug.
>
> **Next:** check the mobile app for the same bug. It shares the cause, so it likely has it too.

## What it changes

- **You're back in a session in seconds.** Your attention goes to the decision, not to rereading
  the whole reply.
- **Plain words.** Technical terms get explained, and anything risky or unchecked stays in the
  summary instead of getting buried in the details.
- **One next step, not a menu.** You don't pick between five options. "Do it" is enough to keep
  going.
- **Your "Do it" means what you think it means.** If the next step deploys to production, sends an
  email or spends money, the line says so before you approve it.
- **No stopping halfway.** If the agent still owes you work, it does that work first. The block
  can't become a polite way to quit early.
- **Finished sessions get closed.** When a task is done and nothing would be lost, the next step
  is archiving the session, so your list only shows work that is still alive.

## A word on models

This skill works because models have become really good at judging what comes next. With a weak
model, the suggested next step can be plain dumb. Don't trust it blindly: read the Next line
before you say "Do it", and read the details when something looks off.

## Install it

Give the link to your agent:

```
Install the skill from https://github.com/pocarles/long-story-short by following its INSTALL.md
```

It asks whether you want the skill on call or always on, puts it in the right place for your
tool, and tells you how to undo it.

**On call** means it runs when you ask. Type `/long-story-short` in Claude Code, or
`$long-story-short` in Codex, and you get the block for the whole session.

**Always on** is where it pays off. Every substantive reply ends with the block, and short replies
stay short. It takes one line in your agent's instructions file, which the install adds for you.

### Or do it yourself

**Claude Code**

```
/plugin install long-story-short --marketplace pocarles/long-story-short
```

**Codex, Cursor, Gemini CLI and other agents that read skills**

```
npx skills add pocarles/long-story-short -g
```

**Claude.ai**

[![Download for Claude.ai](https://img.shields.io/badge/Download-for%20Claude.ai-D97757?style=for-the-badge)](https://github.com/pocarles/long-story-short/releases/latest/download/long-story-short.zip)

Then upload the zip in Settings, under Capabilities, Skills.

**Always on.** Add this line to your instructions file (`CLAUDE.md`, `AGENTS.md` or `GEMINI.md`):

```markdown
**End every substantive reply with the long-story-short block** (load the `long-story-short` skill for the format).
```

## Good to know

- The skill is one short file, [SKILL.md](SKILL.md). Read it before you install it.
- "Do it" approves the Next line as written, nothing more. The skill gives your agent no new
  permissions: your tool's own settings still decide what it may do.
- The block follows your language. Write in French, get it in French.
- In the Claude desktop app, the next-step box offers the same task, with a button that starts it.
- In the Codex app, it can archive a finished session and its worktree for you, and turn a
  decision into choices you click.

MIT license. Made by [Pierre-Olivier Carles](https://github.com/pocarles).
