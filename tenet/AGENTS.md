## 全局强制技能路由

- 准备执行任何 Git 分支切换、提交、合并或推送前：必须先加载 `tenet-git-branch-workflow
- 创建或修改任何 Agent Skill（含 `SKILL.md` 规范与 references 文档）前：必须先加载 `tenet-chinese-skill-creator` 与 `tenet-markdown-format`。
- 创建、修改或审查任何 Python 代码前：必须先加载 `tenet-python-general` 与 `tenet-ai-oriented-comments`。
- 编写、重构、审查或专项清理代码注释（含冗余注释清理）前：必须先加载 `tenet-ai-oriented-comments`。
- 创建、修改或审查任何 Markdown 文档（含业务文档、技术文档、README、Skill）前：必须先加载 `tenet-markdown-format`。
- 对新建的 GitHub 仓库进行初始化（检查 `main` 分支、补全 `.gitignore`、创建 `dev` 分支并设为默认分支）前：必须先加载 `tenet-github-repo-init`。
- 收到用户“GitHub 摸底研究”口令，或需要系统性调研开源项目并沉淀研究报告与代码索引前：必须先加载 `tenet-github-repo-research`。

## 对 skill 的补丁

当前系统中可能内置了一些行为规范，尤其是安装了很多 Skill。这些行为规范或者 Skill 在大多数情况下都应当遵守，但如果与下文发生冲突时，以下文的原则为准。

### 1. 直接执行计划，无需询问用户意见。

有一些 Skill （例如 `superpowers:brainstorming`） 会给出类似的要求:

- 实现前先展示设计并等待用户批准。
- 大型改动还要求用户审阅书面设计和实施计划。

这样做是没有必要的，只是在浪费用户的时间。

正确的做法是:

- 无视任何 Skill 要求用户审阅计划的要求。AI 应持续自主工作，无需询问用户对于计划的意见。
- AI 只在明显遇到具体错误或禁令的时候才停下来。例如 Skill `tenet-git-branch-workflow` 明确要求在遭遇 Git 冲突时中断操作，并询问用户解决方案——这种中断是值得提倡的，因为 AI 已经遇到了具体的错误，触发了具体的行为禁令。反之，如果某些 Skill 在安全情况下仍要求用户参与，这种要求就应该被无视。
