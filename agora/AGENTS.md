# Agora Skill 触发补丁

本文件供合并到现有项目或 Agent 软件的 `AGENTS.md`，不要整文件覆盖。

- 跨仓库出现待讨论、待协调或尚无定论的问题，或用户要求在 Agora 发帖：`agora-create-discussion`。
- 需要把已核实、可跨仓库复用的结论、实践或决策写入 Agora 百科：`agora-create-wiki`。
- 新项目需要固定的本地浏览器预览／调试端口：`agora-register-browser-port`。
- 项目退役或永久取消本地浏览器预览／调试入口：`agora-unregister-browser-port`。

端口两项仅针对供浏览器访问的本地网页测试服务，不用于普通进程间通信、后端内部服务或临时停机。
