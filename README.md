# teacher-skill

## 中文说明

下面是完整的中文说明。英文说明在本页下方，阅读中文不需要打开另一个文件。

### 说明

一套面向自学者的 AI 教学 Skill，尤其适合缺少现成教材和练习的自主学习。围绕学习目标建立分阶段路径，系统梳理知识点及其联系，设计综合练习与节点测试，并根据实际表现调整教学，帮助学习者从零散了解走向系统掌握和独立应用。

可安装的 Skill 是 [`SKILL.md`](SKILL.md)。其中 YAML 的 `description` 比上面这段更短，供客户端判断何时启用。本说明保留完整表述。

### 文件

| 文件 | 作用 |
| --- | --- |
| [SKILL.md](SKILL.md) | 正式 Skill。先是英文七步，随后是标注为译文的同一组中文步骤。 |
| [SKILL.zh-CN.md](SKILL.zh-CN.md) | 忠实中文译文与参照。七个步骤的表述与本页中文步骤、以及 `SKILL.md` 中的中文部分一致。它不是另一份 Skill。 |
| [README.zh-CN.md](README.zh-CN.md) | 本页中文说明的单独副本。阅读中文不必打开它。 |

仓库根目录就是 Skill 目录。`SKILL.md` 里的 `name` 为 `teacher-skill`，因此所在文件夹也必须叫这个名字。

### 七个步骤

教学过程就是下面七个步骤，按该顺序进行。可安装文件中的表述与此相同。

#### 开始学习前

1. 确认学习目的：明确学完要解决什么问题、用于什么场景、达到什么程度。
2. 判断学科性质：分析知识结构与能力形成方式，确定理解、记忆、推导、操作、创作各占什么位置。
3. 核实现有水平：结合学习经历、已有成果和诊断题，确认已掌握的能力与前置缺口。
4. 设计教学阶段：划分阶段，写清每阶段的能力目标、节点测试和通过标准。

#### 开始学习后

5. 书写知识清单：按阶段系统列出知识点，说明概念、原理、前置关系、相互联系、适用条件与实际用途，明确各项需要掌握的深度。
6. 设计综合练习：围绕阶段目标，把多个知识点结合成完整问题，明确输入、任务、约束、预期输出和评价标准，用练习检验理解与应用能力。
7. 反馈、验收与调整：分析错误原因，针对薄弱环节补练，根据节点测试结果调整后续教学。

### 安装

Agent Skill 是一个含有 `SKILL.md` 的目录。[Agent Skills 规范](https://agentskills.io/specification)要求 `name` 与该目录名一致，并且只使用小写字母、数字和连字符。安装时，把名为 `teacher-skill` 的文件夹放进客户端实际会读取的 skills 目录。本仓库根目录就是这个文件夹：`SKILL.md` 在仓库根上。

把本仓库当作普通项目克隆或打开，并不会因此加载这份 Skill。克隆或解压后，路径的最后一段必须是 `teacher-skill`。GitHub 的 ZIP 常常叫 `teacher-skill-main` 或 `teacher-skill-<branch>`，使用前请把文件夹改名为 `teacher-skill`。

```bash
git clone https://github.com/Lemonseaa/teacher-skill.git /path/to/skills-directory/teacher-skill
```

不指定分支的 `git clone` 使用仓库的默认分支。各客户端的目录不同。下表只列出各产品当前文档写明的位置。本仓库不表示每个代理都会读取所有这些路径，也不表示每个客户端都会自动选用这份 Skill。

#### Cursor

文档：[Agent Skills](https://cursor.com/docs/skills)。

| 范围 | 目录 |
| --- | --- |
| 项目 | `.cursor/skills/` 或 `.agents/skills/` |
| 本机用户 | `~/.cursor/skills/` 或 `~/.agents/skills/` |

为兼容 Claude 与 Codex 的布局，Cursor 也会读取 `.claude/skills/`、`.codex/skills/`、`~/.claude/skills/` 和 `~/.codex/skills/`。

在 Agent 聊天中输入 `/`，然后选择 `teacher-skill`。这样调用时，Skill 附在一条消息上。请求与 description 相符时，Cursor 也可能自行采用它。

Cursor 不会自行把一个 GitHub 仓库导入为 Skill。文档中的 GitHub 安装方式要经过插件市场（`.cursor-plugin/marketplace.json`）。本仓库没有这份清单。请按上面的方式复制文件夹。

`~/.cursor/skills/` 里的 Skill 留在本机，除非打开 Sync Skills for Cloud Agents。Cursor 不会把 `~/.agents/skills/` 复制到 Cloud Agents。

#### Claude Code

文档：[Extend Claude with skills](https://code.claude.com/docs/en/skills)。

| 范围 | 目录 |
| --- | --- |
| 项目 | `.claude/skills/` |
| 个人 | `~/.claude/skills/` |

用 `/teacher-skill` 调用，或提出与 description 相符的请求。Claude Code 的文档写明：个人 Skill 会在本机的各个项目中加载，而不会在 Cowork 或云端会话中加载。该文档写的是 `.claude/skills/`，不是 `.agents/skills/`。

#### GitHub Copilot

文档：[Agent skills](https://docs.github.com/en/copilot/concepts/customizations/agent-skills)、[Adding agent skills for GitHub Copilot](https://docs.github.com/en/copilot/how-tos/copilot-on-github/customize-copilot/customize-cloud-agent/add-skills)、[Adding agent skills for GitHub Copilot CLI](https://docs.github.com/en/copilot/how-tos/copilot-cli/customize-copilot/add-skills)。

| 范围 | 目录 |
| --- | --- |
| 项目 | `.github/skills/`、`.claude/skills/` 或 `.agents/skills/` |
| 个人 | `~/.copilot/skills/` 或 `~/.agents/skills/` |

Copilot 文档说明，具体能用哪些位置取决于使用的界面。本机的个人 Skill 不会自动出现在每一次云端会话里。在 Copilot CLI 中，请新开一次会话，或运行 `/skills reload`，再用 `/skills info teacher-skill` 查看。在提示里写上 `/teacher-skill` 即可指定这份 Skill。请求与 description 相符时，Copilot 也可能自行选用它。

#### Codex

文档：[Build skills](https://developers.openai.com/codex/skills)。

| 范围 | 目录 |
| --- | --- |
| 仓库 | 启动 Codex 的目录、其上级目录，或仓库根目录下的 `.agents/skills/` |
| 用户 | `~/.agents/skills/` |

在 Codex CLI 或 IDE 扩展中，运行 `/skills`，或输入 `$` 来提及这份 Skill。任务与 description 相符时，Codex 也可能自行选用它。新放入的 Skill 如果没有出现，请重新启动 Codex。

#### GitHub CLI

`gh skill` 仍是预览功能。它的安装程序可以发现仓库根上的 `SKILL.md`，但 `gh skill publish` 会把该文件的目录名当成 `.`，因此不会接受这里的 `name: teacher-skill`。本说明不提供 `gh skill` 命令。请使用上面的文件夹复制方式。不指定版本的安装读取的是 release 或默认分支，不是尚未合并的 pull request。

### 使用

把文件夹放进客户端会读取的目录后，如果该客户端不会自行重新加载 Skill，请新开一次会话。用平常的话提出教学请求，或按该客户端的文档调用 `teacher-skill`。教学过程就是上面的七个步骤。

### 请求示例

下面是与本 Skill 相符的请求示例，不属于 Skill 正文。

- 我想自学线性代数，没有现成教材和习题。
- 请从我现在能讲清的内容开始教我数据库，并包含节点测试。
- 我对 HTTP 只有零散笔记，希望能学到可以独立使用。
- Use teacher-skill to teach me linear algebra from scratch. I do not have a textbook or exercises.

### 许可

本仓库没有指定许可证。

## English

The Chinese documentation is in the section above on this page.

### Description

An AI teaching skill for self-directed learners, especially suited to learning without ready-made textbooks or exercises. It builds a staged learning path around your goals, systematically organizes concepts and their connections, designs integrated exercises and checkpoint assessments, and adapts teaching based on your performance—helping you progress from fragmented knowledge to systematic understanding and independent application.

[`SKILL.md`](SKILL.md) is the installable skill. Its YAML `description` is shorter than the paragraph above: clients use that field to decide when the skill applies. This README keeps the full description.

### Files

| File | Role |
| --- | --- |
| [SKILL.md](SKILL.md) | Canonical skill. English steps, then the same steps in Chinese, labeled as a translation. |
| [SKILL.zh-CN.md](SKILL.zh-CN.md) | Faithful Chinese translation and reference. The seven-step wording matches the Chinese steps on this page and the Chinese section of `SKILL.md`. This file is not a second skill. |
| [README.zh-CN.md](README.zh-CN.md) | Chinese-only copy of the Chinese section on this page. Chinese readers do not need to open it. |

The repository root is the skill directory. `name` in `SKILL.md` is `teacher-skill`, which matches a folder of that name.

### The seven steps

The procedure is these seven steps, in this order. The installable files use the same wording.

#### Before learning begins

1. Confirm the learning purpose: Make clear what problem should be solved once learning is complete, what situations it will be used in, and what level should be reached.
2. Judge the nature of the subject: Analyze the knowledge structure and how ability is formed, and determine the place of understanding, memory, derivation, operation, and creation.
3. Verify the current level: Drawing on learning history, existing results, and diagnostic questions, confirm the abilities already mastered and the gaps in prerequisites.
4. Design the teaching stages: Divide into stages, and write out each stage's ability goals, checkpoint tests, and passing criteria.

#### After learning begins

5. Write the knowledge inventory: List the knowledge points systematically by stage. Explain the concepts, principles, prerequisite relationships, interconnections, conditions of use, and practical uses, and make clear how deeply each item needs to be mastered.
6. Design integrated exercises: Around the stage goals, combine multiple knowledge points into complete problems. Specify the input, task, constraints, expected output, and evaluation criteria, and use the exercises to test understanding and the ability to apply it.
7. Feedback, acceptance, and adjustment: Analyze the causes of errors, provide targeted practice for weak points, and adjust subsequent teaching based on the results of checkpoint tests.

### Installation

An Agent Skill is a directory that contains `SKILL.md`. The [Agent Skills specification](https://agentskills.io/specification) requires `name` to match that directory's name, using lowercase letters, numbers, and hyphens. Install this skill by placing a folder named `teacher-skill` — this repository, with `SKILL.md` at its root — into a skills directory the client actually reads.

Cloning or opening this repository as a project does not by itself load the skill. Copy or clone it so the last path segment is `teacher-skill`. A GitHub ZIP is often named `teacher-skill-main` or `teacher-skill-<branch>`; rename that folder to `teacher-skill` before use.

```bash
git clone https://github.com/Lemonseaa/teacher-skill.git /path/to/skills-directory/teacher-skill
```

`git clone` without a branch name uses the repository's default branch. Clients differ. The locations below are the ones named in each product's current documentation. This repository does not claim that every agent loads every path, or that a skill is selected automatically in every client.

#### Cursor

Documentation: [Agent Skills](https://cursor.com/docs/skills).

| Scope | Directory |
| --- | --- |
| Project | `.cursor/skills/` or `.agents/skills/` |
| User, on this machine | `~/.cursor/skills/` or `~/.agents/skills/` |

Cursor also loads `.claude/skills/`, `.codex/skills/`, `~/.claude/skills/`, and `~/.codex/skills/` for compatibility with Claude and Codex layouts.

In Agent chat, type `/` and choose `teacher-skill`. A skill invoked that way attaches to one message. Cursor can also apply the skill when the request matches the description.

Cursor does not import a GitHub repository as a skill on its own. Its docs describe GitHub install through a plugin marketplace (`.cursor-plugin/marketplace.json`). This repository does not include that manifest. Use the folder copy above.

Skills in `~/.cursor/skills/` stay on this machine unless you turn on Sync Skills for Cloud Agents. Cursor does not copy `~/.agents/skills/` to Cloud Agents.

#### Claude Code

Documentation: [Extend Claude with skills](https://code.claude.com/docs/en/skills).

| Scope | Directory |
| --- | --- |
| Project | `.claude/skills/` |
| Personal | `~/.claude/skills/` |

Invoke it with `/teacher-skill`, or ask in a way that matches the description. Claude Code's docs say personal skills load in projects on this machine, and not in Cowork or cloud sessions. Claude Code's skills page documents `.claude/skills/`, not `.agents/skills/`.

#### GitHub Copilot

Documentation: [Agent skills](https://docs.github.com/en/copilot/concepts/customizations/agent-skills), [Adding agent skills for GitHub Copilot](https://docs.github.com/en/copilot/how-tos/copilot-on-github/customize-copilot/customize-cloud-agent/add-skills), and [Adding agent skills for GitHub Copilot CLI](https://docs.github.com/en/copilot/how-tos/copilot-cli/customize-copilot/add-skills).

| Scope | Directory |
| --- | --- |
| Project | `.github/skills/`, `.claude/skills/`, or `.agents/skills/` |
| Personal | `~/.copilot/skills/` or `~/.agents/skills/` |

Copilot's docs say supported locations depend on the surface. A personal skill on this machine is not automatically available to every cloud session. In Copilot CLI, start a new session or run `/skills reload`, then `/skills info teacher-skill`. To ask for the skill in a prompt, include `/teacher-skill`. Copilot can also select it when the request matches the description.

#### Codex

Documentation: [Build skills](https://developers.openai.com/codex/skills).

| Scope | Directory |
| --- | --- |
| Repository | `.agents/skills/` in the directory where you launch Codex, a parent directory, or the repository root |
| User | `~/.agents/skills/` |

In Codex CLI or the IDE extension, run `/skills` or type `$` to mention the skill. Codex can also select it when the task matches the description. If a newly added skill does not appear, restart Codex.

#### GitHub CLI

`gh skill` is in preview. Its installer can discover a root `SKILL.md`, but `gh skill publish` compares that file's directory name with `.` and does not accept `name: teacher-skill` there. This README does not give a `gh skill` command. Use the folder copy above. An install that does not name a version reads a release or the default branch, not an unmerged pull request.

### Usage

After the folder is in a directory your client reads, start a new session if the client does not reload skills on its own. Ask for teaching in ordinary language, or invoke `teacher-skill` the way that client documents. The skill's procedure is the seven steps above.

### Example requests

These examples show requests that match the skill. They are not part of the skill instructions.

- I want to learn linear algebra on my own, and I do not have a textbook or exercises.
- Teach me how databases work, starting from what I can already explain, and include checkpoint tests.
- I only have scattered notes on HTTP. Help me reach the point where I can use it on my own.
- 请用 teacher-skill 带我从零学习线性代数，我没有现成教材和习题。

### License

No license is specified for this repository.
