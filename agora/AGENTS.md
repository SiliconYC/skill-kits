# 跨仓库知识协作 Skill 触发补丁

[!note] 本文件供并入现有项目或 Agent 软件的 `AGENTS.md`，不要整体覆盖原文件。

以下为 `agora` 系列 Skill:

- 日常开发、调试或研究中，主动留意有长期价值、值得其他仓库复用的经验与教训。
    1. 发现有价值但尚待核实的信息时，加载：`agora-create-discussion`。
    2. 某个重要的做法、教训或决策已核实后，加载：`agora-create-wiki`。
- 如果你需要创建或移除本地网页项目，请先关注端口问题：
    1. 新项目预留本地浏览器预览端口时，加载：`agora-register-browser-port`。
    2. 项目退役或永久取消本地网页测试入口时，加载：`agora-unregister-browser-port`。
