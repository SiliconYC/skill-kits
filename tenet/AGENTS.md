# 全局 Agent 约定

> [!note]
> 本文件供并入现有项目或 Agent 软件的 `AGENTS.md`，不要整体覆盖原文件。

## 主工作区分支保护（强制）

> [!important]
> **绝对禁止切换受保护主工作区的分支。** Git 主工作区以及用户明确指定的固定工作目录，必须一直停留在指定的永久分支。例如，指定为 `dev` 的主目录必须始终保持 `dev`，不得在该目录执行 `git switch -c`、`git checkout -b` 或任何变更当前分支的操作。该规则优先于一般的 Git 分支处理流程。

- **先识别物理工作区**：本地 Agent 准备修改代码或执行 Git 操作前，必须通过 `git worktree list --porcelain` 等命令识别主工作区、独立 Worktree 与当前分支，不能只看分支名。
- **开发必须隔离**：从受保护主工作区接手任务时，必须另建独立 Worktree 和临时分支进行开发、测试与提交；合并与冲突解决也必须在独立 Worktree 内进行。主工作区仅可在干净状态下同步和快进接收已验证提交，并推送固定永久分支，不得成为开发或冲突现场。
- **不得遗留污染**：任务完成后，必须检查主工作区仍在原永久分支且无未提交修改；原工作区不得停留在临时分支供用户验收。异常中断时须保留独立 Worktree 中的成果，不得把半成品留在主工作区。
- **异常立即停止**：如果发现受保护主工作区已位于临时分支、游离 HEAD 或存在未提交修改，不得误认作用户交付的临时工作区继续开发；先保全改动并报告或根据用户明确的恢复指令处理，禁止擅自强制切分支、丢弃或覆盖文件。

## 必须加载的 Skill

以下为 `tenet` 系列 Skill:

- 本地准备修改代码或执行任何 Git 分支、Worktree、提交、合并、推送操作前：必须先加载 `tenet-git-branch-workflow`，严格执行主工作区保护规定。
- 创建或修改任何 Agent Skill（含 `SKILL.md` 规范与 references 文档）前：必须先加载 `tenet-chinese-skill-creator` 与 `tenet-markdown-format`。
- 创建、修改或审查任何 Python 代码前：必须先加载 `tenet-python-general` 与 `tenet-ai-oriented-comments`。
- 编写、重构、审查或专项清理代码注释（含冗余注释清理）前：必须先加载 `tenet-ai-oriented-comments`。
- 创建、修改或审查任何 Markdown 文档（含业务文档、技术文档、README、Skill）前：必须先加载 `tenet-markdown-format`。
- 对新建的 GitHub 仓库进行初始化（检查 `main` 分支、补全 `.gitignore`、创建 `dev` 分支并设为默认分支）前：必须先加载 `tenet-github-repo-init`。
- 收到用户“GitHub 摸底研究”口令，或需要系统性调研开源项目并沉淀研究报告与代码索引前：必须先加载 `tenet-github-repo-research`。
