# 全局 Agent 约定

[!note] 本文件供并入现有项目或 Agent 软件的 `AGENTS.md`，不要整体覆盖原文件。

## 必须加载的 Skill

以下为 `tenet` 系列 Skill:

- 准备执行任何 Git 分支切换、提交、合并或推送前：必须先加载 `tenet-git-branch-workflow`。
- 创建或修改任何 Agent Skill（含 `SKILL.md` 规范与 references 文档）前：必须先加载 `tenet-chinese-skill-creator` 与 `tenet-markdown-format`。
- 创建、修改或审查任何 Python 代码前：必须先加载 `tenet-python-general` 与 `tenet-ai-oriented-comments`。
- 编写、重构、审查或专项清理代码注释（含冗余注释清理）前：必须先加载 `tenet-ai-oriented-comments`。
- 创建、修改或审查任何 Markdown 文档（含业务文档、技术文档、README、Skill）前：必须先加载 `tenet-markdown-format`。
- 对新建的 GitHub 仓库进行初始化（检查 `main` 分支、补全 `.gitignore`、创建 `dev` 分支并设为默认分支）前：必须先加载 `tenet-github-repo-init`。
- 收到用户“GitHub 摸底研究”口令，或需要系统性调研开源项目并沉淀研究报告与代码索引前：必须先加载 `tenet-github-repo-research`。
