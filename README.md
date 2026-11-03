# Skills

可复用的个人 AI Agent 技能集合。当前面向 Codex，逐步收录学习、研究和日常工作中形成的技能。

A growing collection of reusable AI agent skills, currently targeting Codex, developed through learning, research, and everyday work.

[中文](#中文) · [English](#english)

## 中文

### 仓库用途

本仓库统一保存和维护 skill 源文件。每个 skill 是一个独立目录，用 `SKILL.md` 描述适用场景和执行方式，可按需安装。仓库用于持续增加技能，不局限于某个学科、论文或项目。

### 技能目录

| Skill | 用途 | 调用 |
|---|---|---|
| [interactive-tutor](interactive-tutor/SKILL.md) | 通用互动学习：小步讲解、一次一题、根据回答调整 | `$interactive-tutor` |

### Interactive Tutor：互动渐进教学

核心循环是：**讲一点 → 问一题 → 等待回答 → 针对反馈调整 → 继续学习**。

适用于语言、数学、历史、艺术、编程、论文阅读、工作技能和日常知识。根据目标选择解释、例子、翻译、判断、实际练习或作品修改，而不是所有主题都使用公式推导。

- 根据你的目标和已有基础选择起点。
- 一次只检查一个核心问题，等待你的回答后继续。
- 回答正确就推进，部分正确就修补关键缺口，不确定时换例子或降低难度。
- 先处理追问和疑惑；题目条件不足时先修正题目。
- 区分“讲过”和“真正检查过”，说明学习进度与尚未掌握的部分。
- 支持中英文调用；默认跟随你的语言，也可指定教学语言。

使用示例：

```text
使用 $interactive-tutor 带我学习英语现在完成时。我懂一般过去时，每次讲完问我一题。
```

```text
使用 $interactive-tutor 带我入门水彩配色，先用简单的配色练习检查理解。
```

```text
Use $interactive-tutor to teach me Python loops. I know variables; ask one question at a time.
```

也可说“带我一步步学”或“Teach me step by step”。支持自动选用技能的宿主可根据描述匹配；需要明确指定时使用 `$interactive-tutor`。

### 安装到 Codex

先克隆或下载本仓库，再进入仓库根目录。以下命令将 `interactive-tutor` 复制到安装目录，默认使用 `~/.codex/skills`，设置了 `CODEX_HOME` 时使用其下的 `skills`。安装副本与仓库源文件分开维护。

macOS / Linux：

```sh
skill_home="${CODEX_HOME:-$HOME/.codex}/skills"
mkdir -p "$skill_home"
if [ -e "$skill_home/interactive-tutor" ]; then
  echo "Already installed. Review or back up the existing skill before updating."
else
  cp -R ./interactive-tutor "$skill_home/interactive-tutor"
fi
```

Windows PowerShell：

```powershell
$skillHome = if ($env:CODEX_HOME) {
    Join-Path $env:CODEX_HOME 'skills'
} else {
    Join-Path $HOME '.codex/skills'
}
New-Item -ItemType Directory -Force -Path $skillHome | Out-Null
$skillTarget = Join-Path $skillHome 'interactive-tutor'
if (Test-Path $skillTarget) {
    Write-Output 'Already installed. Review or back up the existing skill before updating.'
} else {
    Copy-Item -Recurse -Path './interactive-tutor' -Destination $skillTarget
}
```

安装后在下一轮尝试 `$interactive-tutor`。如果当前会话没有刷新技能列表，开启新会话后再调用。更新时先比较或备份已有安装，再将仓库中的对应目录复制过去；修改源文件不会自动同步到安装副本。

### 仓库结构与新增技能

```text
skills/
├── README.md
├── AGENTS.md
├── .gitignore
└── interactive-tutor/
    ├── SKILL.md
    └── agents/
        └── openai.yaml
```

新增 skill 时，在根目录创建一个小写连字符命名的文件夹，编写包含 `name`、`description` 前置信息的 `SKILL.md`，再更新本 README 的中英文技能目录。按实际需要加入脚本、参考资料或 UI 元数据，避免提交个人资料和凭据。

这些技能是行为指导，不保证每次输出完全一致或事实正确。互动教学不会自动建立跨会话学习数据库；接续学习可使用对话摘要。

### 许可证

本仓库采用 [MIT 许可证](LICENSE)。允许使用、修改、分发和商业使用；分发时须保留版权声明及许可声明。内容按原样提供，不附带担保，完整条款见许可证文件。

## English

### Purpose

This repository is the source of truth for a growing collection of reusable skills. Each skill lives in its own directory and describes its scope and workflow in `SKILL.md`. Install only the skills you need. The collection is not tied to a particular subject, paper, or project.

### Skill catalog

| Skill | Purpose | Invocation |
|---|---|---|
| [interactive-tutor](interactive-tutor/SKILL.md) | Interactive learning through short explanations, one question at a time, and adaptive feedback | `$interactive-tutor` |

### Interactive Tutor

The learning loop is: **explain a little → ask one question → wait for the answer → adapt → continue**.

Use it for languages, mathematics, history, arts, programming, paper reading, professional skills, and everyday knowledge. Exercises match the subject: explanation, translation, prediction, practical tasks, or revisions to a piece of work.

- Start from the learner's goals and existing knowledge.
- Ask one focused question and wait for an actual answer.
- Advance after a sound answer, repair the key gap after a partial answer, and simplify when needed.
- Address clarification requests first and fix underspecified questions.
- Distinguish material covered from understanding actually checked.
- Invoke in English or Chinese; teaching follows your language unless you request another one. The skill instructions are currently written mainly in Chinese, with an English discovery description and explicit language guidance.

Examples:

```text
Use $interactive-tutor to help me learn the present perfect. I already understand the past simple.
```

```text
Use $interactive-tutor to teach me watercolor color mixing through small practical exercises.
```

```text
Use $interactive-tutor to teach me Python loops. I know variables; ask one question at a time.
```

Natural requests such as “Teach me step by step” can also match the skill in hosts supporting automatic selection. Use `$interactive-tutor` to select it explicitly.

### Install in Codex

Clone or download this repository and open a terminal at its root. The commands below copy the skill into `$CODEX_HOME/skills`, or `~/.codex/skills` when `CODEX_HOME` is unset. They preserve an existing installation.

macOS / Linux:

```sh
skill_home="${CODEX_HOME:-$HOME/.codex}/skills"
mkdir -p "$skill_home"
if [ -e "$skill_home/interactive-tutor" ]; then
  echo "Already installed. Review or back up the existing skill before updating."
else
  cp -R ./interactive-tutor "$skill_home/interactive-tutor"
fi
```

Windows PowerShell:

```powershell
$skillHome = if ($env:CODEX_HOME) {
    Join-Path $env:CODEX_HOME 'skills'
} else {
    Join-Path $HOME '.codex/skills'
}
New-Item -ItemType Directory -Force -Path $skillHome | Out-Null
$skillTarget = Join-Path $skillHome 'interactive-tutor'
if (Test-Path $skillTarget) {
    Write-Output 'Already installed. Review or back up the existing skill before updating.'
} else {
    Copy-Item -Recurse -Path './interactive-tutor' -Destination $skillTarget
}
```

Try `$interactive-tutor` on your next turn. If the skill list has not refreshed, start a new conversation. To update, compare or back up the installed version before replacing it with the corresponding source directory. Source edits do not automatically update installed copies.

### Layout and new skills

```text
skills/
├── README.md
├── AGENTS.md
├── .gitignore
└── interactive-tutor/
    ├── SKILL.md
    └── agents/
        └── openai.yaml
```

Add each new skill as a lowercase, hyphenated directory at the root. Include a `SKILL.md` with `name` and `description` frontmatter, and update both language versions of the catalog. Add scripts, references, or UI metadata only when needed. Keep personal materials and credentials out of the repository.

Skills guide behavior; they do not guarantee identical responses or factual correctness. Interactive Tutor does not automatically maintain a cross-session learning database. A conversation summary can help resume learning.

### License

This repository is licensed under the [MIT License](LICENSE), which permits use, modification, distribution, and commercial use, provided the copyright and permission notices are retained. The material is provided as is, without warranty. See the license file for the full terms.
