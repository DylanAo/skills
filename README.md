# Skills

可复用的个人 AI Agent 技能集合。每个技能一个独立目录，按分类按需安装。
Reusable personal AI agent skills. One directory per skill; install by category as needed.

[中文](#中文) · [English](#english)

## 中文

### 分类说明

- **Core（核心，推荐安装）**：通用基础能力，适合所有使用者，且可能被其他技能依赖。
- **Courses（专题课程，按需安装）**：面向特定学习目标的课程大纲，只对该主题感兴趣时安装；依赖 Core 中的教学技能。

技能平铺安装到宿主技能目录即可，分类仅用于选择，不需要按类建文件夹。

### 技能目录

| Skill | 类别 | 用途 | 调用 |
|---|---|---|---|
| [interactive-tutor](interactive-tutor/SKILL.md) | Core | 互动渐进教学：小步讲解、一次一题、按回答调整 | `$interactive-tutor` |
| [agent-dev-tutor](agent-dev-tutor/SKILL.md) | Courses | Agent 扩展开发课程：Skill、Hook、MCP、子代理、插件、安全与独立 Agent | `$agent-dev-tutor` |

### 使用说明

**interactive-tutor**：核心循环是"讲一点 → 问一题 → 等待回答 → 按反馈调整"。适用于任意学科，支持中英文。

```text
使用 $interactive-tutor 带我学习 Python 循环，我懂变量，每次讲完问我一题。
```

**agent-dev-tutor**：七课大纲，配合 interactive-tutor 授课，也可由支持自动匹配的宿主直接触发"教我 Agent 开发"。

```text
使用 $agent-dev-tutor 带我入门 Agent 扩展开发，我有 Linux 基础。
```

### 安装

将所需技能目录复制到宿主的技能目录（Codex 为 `${CODEX_HOME:-~/.codex}/skills`，Qoder 为 `~/.agents/skills`）。

只装核心教学技能（多数人的选择）：

```sh
cp -R ./interactive-tutor ~/.agents/skills/
```

想学习 Agent 开发课程时，两个一起装（课程依赖教学技能）：

```sh
cp -R ./interactive-tutor ./agent-dev-tutor ~/.agents/skills/
```

Windows 可用资源管理器或 `Copy-Item -Recurse` 完成同样的复制。安装后开新会话生效；源文件与安装副本分开维护，更新前先备份已有安装。

### 新增技能

在根目录新建小写连字符命名的目录，编写含 `name`、`description` 的 `SKILL.md`，归入 Core 或 Courses 并更新本 README 的中英文目录。不要提交个人资料与凭据。技能是行为指导，不保证输出完全一致或事实正确。

### 许可证

[MIT](LICENSE)。

## English

### Categories

- **Core (recommended)**: general-purpose capabilities useful to everyone; other skills may depend on them.
- **Courses (optional)**: lesson outlines for specific learning goals, installed only when interested; they rely on the Core tutoring skill.

Install skills flat into the host skill directory. Categories guide selection only; no category folders are required.

### Skill catalog

| Skill | Category | Purpose | Invocation |
|---|---|---|---|
| [interactive-tutor](interactive-tutor/SKILL.md) | Core | Interactive tutoring: short explanations, one question at a time, adaptive feedback | `$interactive-tutor` |
| [agent-dev-tutor](agent-dev-tutor/SKILL.md) | Courses | Agent extension course: Skills, Hooks, MCP, subagents, plugins, security, standalone agents | `$agent-dev-tutor` |

### Usage

**interactive-tutor** runs the loop "explain a little → ask one question → wait → adapt". Any subject, English or Chinese.

```text
Use $interactive-tutor to teach me Python loops. I know variables; ask one question at a time.
```

**agent-dev-tutor** is a seven-lesson outline taught through interactive-tutor, or triggered automatically by requests like "teach me agent development".

```text
Use $agent-dev-tutor to teach me agent extension development. I have basic Linux experience.
```

### Install

Copy each skill directory into your host's skill directory (`${CODEX_HOME:-~/.codex}/skills` for Codex, `~/.agents/skills` for Qoder).

Core tutoring skill only (the common choice):

```sh
cp -R ./interactive-tutor ~/.agents/skills/
```

For the agent development course, install both (the course depends on the tutor):

```sh
cp -R ./interactive-tutor ./agent-dev-tutor ~/.agents/skills/
```

On Windows, copy the directories with Explorer or `Copy-Item -Recurse`. Start a new session after installing. Source files and installed copies are maintained separately; back up existing installations before updating.

### Adding skills

Create a lowercase, hyphenated directory at the root with a `SKILL.md` containing `name` and `description` frontmatter, assign it to Core or Courses, and update both language catalogs above. Keep personal materials and credentials out of the repository. Skills guide behavior; they do not guarantee identical or factually correct output.

### License

[MIT](LICENSE).
