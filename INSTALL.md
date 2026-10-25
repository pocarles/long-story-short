# Install guide for agents

You are an AI agent and your user gave you this repository to install the long-story-short skill.
Follow these steps. Change nothing beyond what they describe.

Repository: https://github.com/pocarles/long-story-short
The skill is `SKILL.md` at the root of the repository. `README.md` is for humans.

## 1. Ask one question

Ask your user:

> Do you want long-story-short on call (it runs when you ask for it) or always on (your agent
> uses it on every reply where it fits)? I recommend always on.

Wait for the answer. Ask it even if the skill is already installed: then skip step 2 and only do
step 3 if they chose always on.

If you cannot run commands or write files, give your user the exact command for step 2 and the
exact line and file for step 3 instead.

## 2. Install the skill

Pick the line for the harness you are running in. If a command fails, create a folder named
`long-story-short` in the skills folder listed for that harness and copy `SKILL.md` into it.

| Harness | Install | Skills folder |
|-|-|-|
| Claude Code | `claude plugin install long-story-short --marketplace pocarles/long-story-short` | `~/.claude/skills/` |
| Codex | Copy `SKILL.md` | `~/.agents/skills/` |
| Gemini CLI | `gemini skills install https://github.com/pocarles/long-story-short.git` | `~/.gemini/skills/` |
| Cursor | Copy `SKILL.md` | `~/.cursor/skills/` |
| Any other agent with skills | `npx skills add pocarles/long-story-short -g` | its own skills folder |

If you are a chat app with no file access (Claude.ai, the Claude desktop chat), you cannot install
it yourself. Send your user to the README, which has a download button for Claude.ai, and tell
them to upload the zip in Settings, under Capabilities, Skills.

If your harness has no skills at all, skip this step. For always on, paste the body of `SKILL.md`
(everything after the frontmatter) into the instructions file in step 3 instead of the one line.

## 3. Always on only

Copy the line under "Always on" in the README. Append it to your user-level instructions file;
never replace the file. Skip it if the file already mentions the skill.

| Harness | Instructions file |
|-|-|
| Claude Code | `~/.claude/CLAUDE.md` |
| Codex | `~/.codex/AGENTS.md` |
| Gemini CLI | `~/.gemini/GEMINI.md` |
| Cursor | Settings, Rules, User Rules (ask your user to paste the line) |
| Other | The file your harness reads for user-level instructions, often `AGENTS.md` |

If you are not sure which file your harness reads, ask your user rather than guessing.

## 4. Confirm

Tell your user, in a few lines:

- where you installed the skill, and whether you added the always-on line (and to which file);
- how to call it: `/long-story-short` in Claude Code, `$long-story-short` in Codex, and in any
  tool, asking for it by name;
- that it may need a new session to load;
- how to undo it: delete the skill folder and the one line you added.
