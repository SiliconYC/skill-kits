---
name: agora-create-discussion
description: 当用户要求在 Agora 发起讨论，或跨仓库开发出现需要他人参与的开放问题、方案争议、协作冲突和变更预告时触发；不用于沉淀已经验证的正式知识。
---

# 在 Agora 创建 Discussion

目标：[SiliconYC/agora Discussions](https://github.com/SiliconYC/agora/discussions)。

## 何时触发

- 用户要求在 Agora 发帖，或需要跨仓库开发者讨论未决问题、方案、风险和依赖。
- 有可供其他仓库借鉴但尚待核实的经验，需要征求意见。

单仓库的任务执行、故障追踪和 PR 审查留在原仓库；已核实且稳定的结论应使用 `agora-create-wiki`。

## 执行

1. 搜索已有 Discussions 和 Wiki；有相同话题则优先补充已有讨论，避免重复。
2. 选择仓库已有且最合适的讨论分类。标题具体；正文只写背景、涉及仓库、待解决问题、已知证据与相关 Issue/PR 链接。
3. 区分事实、猜测与提案；不把讨论内容写成最终规则，不粘贴密码或令牌。
4. 使用具备权限的 GitHub 讨论功能提交，返回 Discussion URL；如当前工具不能创建 Discussion，明确说明并交付可直接发布的草稿，不以 Issue 冒充。
5. 讨论达成可复用且已核实的结论后，再用 `agora-create-wiki` 沉淀，并在两边互相链接。
