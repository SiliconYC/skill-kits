# 全局 Agent 约定

> [!note]
> 本文件供并入现有项目或 Agent 软件的 `AGENTS.md`，不要整体覆盖原文件。

## 主工作区分支保护

当你发现当前工作区中的 Git 分支名称为以下四项之一时：

- `main`
- `dev`
- `smart`
- `golden-gate`

请务必保护当前工作区。即：

- 禁止将当前工作区的 Git 分支切换到其它分支。
- 禁止直接在本工作区修改文件。
- 任何编辑操作都要派生到独立 Worktree 进行，完工后再合并回当前工作区的分支。

## 必须加载的 Skill

以下为 `tenet` 系列 Skill:

- 本地准备修改代码或执行任何 Git 分支、Worktree、提交、合并、推送操作前：必须先加载 `tenet-git-branch-workflow`，严格执行主工作区保护规定。
- 创建或修改任何 Agent Skill（含 `SKILL.md` 规范与 references 文档）前：必须先加载 `tenet-chinese-skill-creator` 与 `tenet-markdown-format`。
- 创建、修改或审查任何 Python 代码前：必须先加载 `tenet-python-general` 与 `tenet-ai-oriented-comments`。
- 编写、放置或审查 Python 测试脚本及测试数据文件前：必须先加载 `tenet-python-testing`。
- 编写、重构、审查或专项清理代码注释（含冗余注释清理）前：必须先加载 `tenet-ai-oriented-comments`。
- 创建、修改或审查任何 Markdown 文档（含业务文档、技术文档、README、Skill）前：必须先加载 `tenet-markdown-format`。
- 对新建的 GitHub 仓库进行初始化（检查 `main` 分支、补全 `.gitignore`、创建 `dev` 分支并设为默认分支）前：必须先加载 `tenet-github-repo-init`。
- 收到用户“GitHub 摸底研究”口令，或需要系统性调研开源项目并沉淀研究报告与代码索引前：必须先加载 `tenet-github-repo-research`。
