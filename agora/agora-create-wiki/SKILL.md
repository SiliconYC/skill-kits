---
name: agora-create-wiki
description: 当用户要求向 Agora 百科写入文档，或产生经核实、稳定且具有跨仓库复用价值的最佳实践、教训或技术决策时触发；未决问题应先发 Discussion。
---

# 在 Agora 创建或更新 Wiki

目标仓库：[SiliconYC/agora](https://github.com/SiliconYC/agora)，默认分支 `dev`。

## 何时触发

- 用户要求记录为 Agora Wiki。
- 已形成可复用且有依据的跨仓库实践、故障解决方案、规则或决策。

未验证的经验、征求意见和进行中的争议使用 `agora-create-discussion`；项目独有的技术细节保留在项目自身文档。

## 目录

- `docs/practices/`：最佳实践、故障处理、经验教训。
- `docs/decisions/`：跨仓库架构或协作决策及其理由。
- `registry/`：端口、服务等共享资源登记；端口分配与注销优先使用专门 Skill。

按需建文件，不创建占位目录。

## 执行

1. 检索现有 Wiki 与 Discussions；已有主题优先修订，不创建重复页面。
2. 核实来源，区分独立实测、源码证据与未验证说法。写明结论、适用范围、必要步骤及源仓库／Discussion／Issue／PR 链接。
3. 在 Agora `dev` 上新增或更新简洁的 Markdown，必要时更新 `README.md` 导航；保留已有内容与历史。
4. 回传文档链接；若源于讨论，在可编辑时补上双向链接。禁止提交密钥、凭证及不应共享的私密内容。
