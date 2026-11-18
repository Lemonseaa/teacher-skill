# teacher-skill

中文说明：[README.zh-CN.md](README.zh-CN.md)

## Description

An AI teaching skill for self-directed learners, especially suited to learning without ready-made textbooks or exercises. It builds a staged learning path around your goals, systematically organizes concepts and their connections, designs integrated exercises and checkpoint assessments, and adapts teaching based on your performance—helping you progress from fragmented knowledge to systematic understanding and independent application.

[`SKILL.md`](SKILL.md) is the installable skill. Its YAML `description` is shorter than the paragraph above: clients use that field to decide when the skill applies. This README keeps the full description.

## Files

| File | Role |
| --- | --- |
| [SKILL.md](SKILL.md) | Canonical skill. English steps, then the same steps in Chinese, labeled as a translation. |
| [SKILL.zh-CN.md](SKILL.zh-CN.md) | Faithful Chinese translation and reference. The seven-step wording matches the Chinese section of `SKILL.md`. This file is not a second skill. |
| [README.zh-CN.md](README.zh-CN.md) | Chinese README. |

The repository root is the skill directory. `name` in `SKILL.md` is `teacher-skill`, which matches a folder of that name.

## Steps

The procedure is the seven steps in [`SKILL.md`](SKILL.md), in that order. Their titles are:

Before learning begins:

1. Confirm the learning purpose
2. Judge the nature of the subject
3. Verify the current level
4. Design the teaching stages

After learning begins:

5. Write the knowledge inventory
6. Design integrated exercises
7. Feedback, acceptance, and adjustment

The Chinese titles and full wording are in [`SKILL.zh-CN.md`](SKILL.zh-CN.md).

## Installation

An Agent Skill is a directory that contains `SKILL.md`. The [Agent Skills specification](https://agentskills.io/specification) requires `name` to match that directory's name, using lowercase letters, numbers, and hyphens. Install this skill by placing a folder named `teacher-skill` — this repository, with `SKILL.md` at its root — into a skills directory the client actually reads.

Cloning or opening this repository as a project does not by itself load the skill. Copy or clone it so the last path segment is `teacher-skill`. A GitHub ZIP is often named `teacher-skill-main` or `teacher-skill-<branch>`; rename that folder to `teacher-skill` before use.

```bash
git clone https://github.com/Lemonseaa/teacher-skill.git /path/to/skills-directory/teacher-skill
```

`git clone` without a branch name uses the repository's default branch. Clients differ. The locations below are the ones named in each product's current documentation. This repository does not claim that every agent loads every path, or that a skill is selected automatically in every client.

### Cursor

Documentation: [Agent Skills](https://cursor.com/docs/skills).

| Scope | Directory |
| --- | --- |
| Project | `.cursor/skills/` or `.agents/skills/` |
| User, on this machine | `~/.cursor/skills/` or `~/.agents/skills/` |

Cursor also loads `.claude/skills/`, `.codex/skills/`, `~/.claude/skills/`, and `~/.codex/skills/` for compatibility with Claude and Codex layouts.

In Agent chat, type `/` and choose `teacher-skill`. A skill invoked that way attaches to one message. Cursor can also apply the skill when the request matches the description.

Cursor does not import a GitHub repository as a skill on its own. Its docs describe GitHub install through a plugin marketplace (`.cursor-plugin/marketplace.json`). This repository does not include that manifest. Use the folder copy above.

Skills in `~/.cursor/skills/` stay on this machine unless you turn on Sync Skills for Cloud Agents. Cursor does not copy `~/.agents/skills/` to Cloud Agents.

### Claude Code

Documentation: [Extend Claude with skills](https://code.claude.com/docs/en/skills).

| Scope | Directory |
| --- | --- |
| Project | `.claude/skills/` |
| Personal | `~/.claude/skills/` |

Invoke it with `/teacher-skill`, or ask in a way that matches the description. Claude Code's docs say personal skills load in projects on this machine, and not in Cowork or cloud sessions. Claude Code's skills page documents `.claude/skills/`, not `.agents/skills/`.

### GitHub Copilot

Documentation: [Agent skills](https://docs.github.com/en/copilot/concepts/customizations/agent-skills), [Adding agent skills for GitHub Copilot](https://docs.github.com/en/copilot/how-tos/copilot-on-github/customize-copilot/customize-cloud-agent/add-skills), and [Adding agent skills for GitHub Copilot CLI](https://docs.github.com/en/copilot/how-tos/copilot-cli/customize-copilot/add-skills).

| Scope | Directory |
| --- | --- |
| Project | `.github/skills/`, `.claude/skills/`, or `.agents/skills/` |
| Personal | `~/.copilot/skills/` or `~/.agents/skills/` |

Copilot's docs say supported locations depend on the surface. A personal skill on this machine is not automatically available to every cloud session. In Copilot CLI, start a new session or run `/skills reload`, then `/skills info teacher-skill`. To ask for the skill in a prompt, include `/teacher-skill`. Copilot can also select it when the request matches the description.

### Codex

Documentation: [Build skills](https://developers.openai.com/codex/skills).

| Scope | Directory |
| --- | --- |
| Repository | `.agents/skills/` in the directory where you launch Codex, a parent directory, or the repository root |
| User | `~/.agents/skills/` |

In Codex CLI or the IDE extension, run `/skills` or type `$` to mention the skill. Codex can also select it when the task matches the description. If a newly added skill does not appear, restart Codex.

### GitHub CLI

`gh skill` is in preview. Its installer can discover a root `SKILL.md`, but `gh skill publish` compares that file's directory name with `.` and does not accept `name: teacher-skill` there. This README does not give a `gh skill` command. Use the folder copy above. An install that does not name a version reads a release or the default branch, not an unmerged pull request.

## Usage

After the folder is in a directory your client reads, start a new session if the client does not reload skills on its own. Ask for teaching in ordinary language, or invoke `teacher-skill` the way that client documents. The skill's procedure is the seven steps in `SKILL.md`.

## Example requests

These examples show requests that match the skill. They are not part of the skill instructions.

- I want to learn linear algebra on my own, and I do not have a textbook or exercises.
- Teach me how databases work, starting from what I can already explain, and include checkpoint tests.
- I only have scattered notes on HTTP. Help me reach the point where I can use it on my own.
- 请用 teacher-skill 带我从零学习线性代数，我没有现成教材和习题。

## License

No license is specified for this repository.
