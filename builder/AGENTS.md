# 构建与编译 Skill 触发补丁

> [!note]
> 本文件供并入现有项目或 Agent 软件的 `AGENTS.md`，不要整体覆盖原文件。

## 必须加载的 Skill

以下为 `builder` 系列 Skill：

- 使用 PyInstaller 打包 Python 程序或优化打包体积时，必须先加载 `builder-pyinstaller-size-optimization`。
