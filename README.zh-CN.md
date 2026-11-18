# teacher-skill

English: [README.md](README.md)

## 说明

一套面向自学者的 AI 教学 Skill，尤其适合缺少现成教材和练习的自主学习。围绕学习目标建立分阶段路径，系统梳理知识点及其联系，设计综合练习与节点测试，并根据实际表现调整教学，帮助学习者从零散了解走向系统掌握和独立应用。

可安装的 Skill 是 [`SKILL.md`](SKILL.md)。其中 YAML 的 `description` 比上面这段更短，供客户端判断何时启用。本说明保留完整表述。

## 文件

| 文件 | 作用 |
| --- | --- |
| [SKILL.md](SKILL.md) | 正式 Skill。先是英文七步，随后是标注为译文的同一组中文步骤。 |
| [SKILL.zh-CN.md](SKILL.zh-CN.md) | 忠实中文译文与参照。七个步骤的表述与 `SKILL.md` 中的中文部分一致。它不是另一份 Skill。 |
| [README.md](README.md) | 英文说明。 |

仓库根目录就是 Skill 目录。`SKILL.md` 里的 `name` 为 `teacher-skill`，因此所在文件夹也必须叫这个名字。

## 步骤

教学过程就是 [`SKILL.md`](SKILL.md) 中的七个步骤，按该顺序进行。中文标题为：

开始学习前：

1. 确认学习目的
2. 判断学科性质
3. 核实现有水平
4. 设计教学阶段

开始学习后：

5. 书写知识清单
6. 设计综合练习
7. 反馈、验收与调整

完整中文表述见 [`SKILL.zh-CN.md`](SKILL.zh-CN.md)。

## 安装

Agent Skill 是一个含有 `SKILL.md` 的目录。[Agent Skills 规范](https://agentskills.io/specification)要求 `name` 与该目录名一致，并且只使用小写字母、数字和连字符。安装时，把名为 `teacher-skill` 的文件夹放进客户端实际会读取的 skills 目录。本仓库根目录就是这个文件夹：`SKILL.md` 在仓库根上。

把本仓库当作普通项目克隆或打开，并不会因此加载这份 Skill。克隆或解压后，路径的最后一段必须是 `teacher-skill`。GitHub 的 ZIP 常常叫 `teacher-skill-main` 或 `teacher-skill-<branch>`，使用前请把文件夹改名为 `teacher-skill`。

```bash
git clone https://github.com/Lemonseaa/teacher-skill.git /path/to/skills-directory/teacher-skill
```

不指定分支的 `git clone` 使用仓库的默认分支。各客户端的目录不同。下表只列出各产品当前文档写明的位置。本仓库不表示每个代理都会读取所有这些路径，也不表示每个客户端都会自动选用这份 Skill。

### Cursor

文档：[Agent Skills](https://cursor.com/docs/skills)。

| 范围 | 目录 |
| --- | --- |
| 项目 | `.cursor/skills/` 或 `.agents/skills/` |
| 本机用户 | `~/.cursor/skills/` 或 `~/.agents/skills/` |

为兼容 Claude 与 Codex 的布局，Cursor 也会读取 `.claude/skills/`、`.codex/skills/`、`~/.claude/skills/` 和 `~/.codex/skills/`。

在 Agent 聊天中输入 `/`，然后选择 `teacher-skill`。这样调用时，Skill 附在一条消息上。请求与 description 相符时，Cursor 也可能自行采用它。

Cursor 不会自行把一个 GitHub 仓库导入为 Skill。文档中的 GitHub 安装方式要经过插件市场（`.cursor-plugin/marketplace.json`）。本仓库没有这份清单。请按上面的方式复制文件夹。

`~/.cursor/skills/` 里的 Skill 留在本机，除非打开 Sync Skills for Cloud Agents。Cursor 不会把 `~/.agents/skills/` 复制到 Cloud Agents。

### Claude Code

文档：[Extend Claude with skills](https://code.claude.com/docs/en/skills)。

| 范围 | 目录 |
| --- | --- |
| 项目 | `.claude/skills/` |
| 个人 | `~/.claude/skills/` |

用 `/teacher-skill` 调用，或提出与 description 相符的请求。Claude Code 的文档写明：个人 Skill 会在本机的各个项目中加载，而不会在 Cowork 或云端会话中加载。该文档写的是 `.claude/skills/`，不是 `.agents/skills/`。

### GitHub Copilot

文档：[Agent skills](https://docs.github.com/en/copilot/concepts/customizations/agent-skills)、[Adding agent skills for GitHub Copilot](https://docs.github.com/en/copilot/how-tos/copilot-on-github/customize-copilot/customize-cloud-agent/add-skills)、[Adding agent skills for GitHub Copilot CLI](https://docs.github.com/en/copilot/how-tos/copilot-cli/customize-copilot/add-skills)。

| 范围 | 目录 |
| --- | --- |
| 项目 | `.github/skills/`、`.claude/skills/` 或 `.agents/skills/` |
| 个人 | `~/.copilot/skills/` 或 `~/.agents/skills/` |

Copilot 文档说明，具体能用哪些位置取决于使用的界面。本机的个人 Skill 不会自动出现在每一次云端会话里。在 Copilot CLI 中，请新开一次会话，或运行 `/skills reload`，再用 `/skills info teacher-skill` 查看。在提示里写上 `/teacher-skill` 即可指定这份 Skill。请求与 description 相符时，Copilot 也可能自行选用它。

### Codex

文档：[Build skills](https://developers.openai.com/codex/skills)。

| 范围 | 目录 |
| --- | --- |
| 仓库 | 启动 Codex 的目录、其上级目录，或仓库根目录下的 `.agents/skills/` |
| 用户 | `~/.agents/skills/` |

在 Codex CLI 或 IDE 扩展中，运行 `/skills`，或输入 `$` 来提及这份 Skill。任务与 description 相符时，Codex 也可能自行选用它。新放入的 Skill 如果没有出现，请重新启动 Codex。

### GitHub CLI

`gh skill` 仍是预览功能。它的安装程序可以发现仓库根上的 `SKILL.md`，但 `gh skill publish` 会把该文件的目录名当成 `.`，因此不会接受这里的 `name: teacher-skill`。本说明不提供 `gh skill` 命令。请使用上面的文件夹复制方式。不指定版本的安装读取的是 release 或默认分支，不是尚未合并的 pull request。

## 使用

把文件夹放进客户端会读取的目录后，如果该客户端不会自行重新加载 Skill，请新开一次会话。用平常的话提出教学请求，或按该客户端的文档调用 `teacher-skill`。教学过程就是 `SKILL.md` 里的七个步骤。

## 请求示例

下面是与本 Skill 相符的请求示例，不属于 Skill 正文。

- 我想自学线性代数，没有现成教材和习题。
- 请从我现在能讲清的内容开始教我数据库，并包含节点测试。
- 我对 HTTP 只有零散笔记，希望能学到可以独立使用。
- Use teacher-skill to teach me linear algebra from scratch. I do not have a textbook or exercises.

## 许可

本仓库没有指定许可证。
