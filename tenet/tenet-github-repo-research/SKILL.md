---
name: tenet-github-repo-research
description: 用于执行“GitHub 摸底研究”任务。当用户明确提及口令“GitHub 摸底研究”，或要求系统性调研 GitHub 开源仓库并沉淀结构化研究报告与代码索引时触发，规范主从 Agent 协同、Issue 追踪与 dev 分支派生工作流。
---

# GitHub 摸底研究工作流

## 适用范围与触发口令

当用户明确下达“GitHub 摸底研究”指令，要求对特定技术方向、功能实现或同类开源项目进行系统性的 GitHub 仓库调研时，必须严格启用本 Skill。

本工作流通过 GitHub Issue 追踪进度，基于 `dev` 分支派生临时分支开展工作，并利用主 Agent 统筹、多子 Agent 并行的方式，将零散的开源代码库调研转化为结构化的仓库分析与浓缩综述。

## 目标目录与产物结构

摸底研究的所有文档产物统一存放在 `docs/research` 目录下，分为“全局综述区”与“单仓分析区”两部分：

- `docs/research/github-references/related-repositories.md`：记录所有相关的目标 GitHub 开源仓库清单，或记录未能找到合适仓库时的搜索经过与具体困难。
- `docs/research/github-references/README.md`：跨仓库的全局综述报告，提炼所有目标仓库的核心结论，避免未来的 AI 或人类开发者通读全部零碎报告。
- `docs/research/github-references/source-index.md`：跨仓库的高价值代码上下文浓缩索引，作为各独立仓库 `source-index.md` 全集的真子集。
- `docs/research/repositories/<仓库名>/README.md`：单个开源仓库的核心分析结果（若原仓库名包含无法作为目录名的非法字符，统一使用中划线 `-` 替换）。
- `docs/research/repositories/<仓库名>/source-index.md`：单个开源仓库内部的关键代码上下文索引。

> [!note]
> 除上述必选核心文件外，无论是单仓目录 `docs/research/repositories/<仓库名>/` 还是综述目录 `docs/research/github-references/`，均可根据实际调研深度按需建立其他补充 Markdown 文件。

## 标准执行流程

1. **立项搜寻（创建 Issue A）**
   - **执行主体**：主 Agent。
   - **工作分支**：`dev` 分支。
   - **核心任务**：创建 GitHub Issue A，明确建立开源参考清单的目标与检索范围。

2. **摸底初筛与清单编制**
   - **执行主体**：主 Agent。
   - **工作分支**：从 `dev` 派生的独立临时分支（如 `tmp/research-repo-list`）。
   - **核心任务**：检索并筛选目标开源仓库；若未检索到有效项目，如实记录检索经过与具体困难，触发跳出机制。
   - **交付产物**：`docs/research/github-references/related-repositories.md`。
   - **流转动作**：将临时分支合并回 `dev` 分支。

3. **结项归档（关闭 Issue A）**
   - **执行主体**：主 Agent。
   - **工作分支**：`dev` 分支。
   - **流转动作**：确认清单文件已并入 `dev` 后关闭 Issue A。若触发极端情况（无有效仓库），流程在此终止并直接向用户汇报；若正常，进入单仓拆解阶段。

4. **任务拆解（创建系列 Issue B）**
   - **执行主体**：主 Agent。
   - **工作分支**：`dev` 分支。
   - **核心任务**：解析 `related-repositories.md`，为每个候选仓库分别创建一个独立的 GitHub Issue（统称“系列 Issue B”），注明其研究重点与参考价值。

5. **批量派生单仓研究分支**
   - **执行主体**：主 Agent。
   - **工作分支**：基于最新的 `dev` 分支，为系列 Issue B 中的每个 Issue 派生专属临时分支（如 `tmp/research-<仓库名>`）。

6. **并行深挖单仓（执行系列 Issue B）**
   - **执行主体**：多个子 Agent 并行接管（每个子 Agent 独立负责一个 Issue 及对应分支）。
   - **工作分支**：各自对应的单仓临时分支。
   - **核心任务**：查阅目标仓库源码与架构设计，提炼关键实现逻辑。
   - **交付产物**：在 `docs/research/repositories/<仓库名>/` 目录下建立文档：
     - `README.md`：核心分析报告（方案设计、优缺点、对本项目的借鉴意义）。
     - `source-index.md`：关键代码上下文与模块索引。
     - 其他文件按需补充。
   - **流转动作**：研究完成后，子 Agent 自行将临时分支合并回 `dev` 分支，并关闭对应的 Issue。

7. **发起全局综述（创建 Issue C）**
   - **执行主体**：主 Agent。
   - **工作分支**：`dev` 分支。
   - **前置条件**：系列 Issue B 的全部任务均已合入 `dev` 且对应 Issue 全部关闭。
   - **核心任务**：创建 GitHub Issue C，要求整合所有单仓报告，建立跨项目的全局综述。

8. **提炼与编制综述（执行 Issue C）**
   - **执行主体**：综述子 Agent。
   - **工作分支**：从 `dev` 派生的专属临时分支（如 `tmp/research-summary`）。
   - **核心任务**：横向对比各个仓库的实现方案，提炼通用模式与关键技术差异，构建高浓度参考索引。
   - **交付产物**：在 `docs/research/github-references/` 目录下建立综述文档：
     - `README.md`：全景式技术综述，提炼各仓库的核心结论，避免后续维护者逐一翻阅分散报告。
     - `source-index.md`：跨仓库源码精选索引，汇集各项目中最具参考价值的代码片段（作为各分仓 `source-index.md` 构成的全集之真子集）。
     - 其他文件按需补充。
   - **流转动作**：编写完成后，子 Agent 自行将临时分支合并回 `dev` 分支，并关闭 Issue C。

9. **成果验收与汇总汇报**
   - **执行主体**：主 Agent。
   - **工作分支**：`dev` 分支。
   - **核心任务**：校验所有文档产物与分支状态，确认工作区干净且位于最新的 `dev` 分支，向用户汇报最终摸底研究成果。

## 极端情况：无有效参考仓库时的跳出机制

在极端情况下，经过充分检索，可能找不到任何一个有参考价值的 GitHub 开源仓库。遇到此类情况时，必须严格遵守实事求是的原则，在环节 2 直接跳出后续流程：

- **严禁强行凑数**：绝对禁止为了走完流程而强行收录无关仓库或制造垃圾分析内容。
- **如实记录检索困境**：`docs/research/github-references/related-repositories.md` 仍然必须创建。文件内容应言简意赅，客观说明已尝试的搜索方向与检索词，并向未来的 AI 或人类读者报告搜索时遭遇的具体困难与无果原因。
- **收敛分支并立即汇报**：完成 `related-repositories.md` 编写后，循例将临时分支合并回 `dev` 分支，关闭 Issue A，不再创建“系列 Issue B”与“Issue C”，直接跳出工作流并立即向人类用户报告这一消息。

> [!warning]
> 所有派生的临时分支在完成文档提交后，都必须合入 `dev` 分支并确保对应 Issue 正常关闭；各子 Agent 在合并回 `dev` 分支时若遇到并发合并冲突，应妥善解决或上报主 Agent 协调，严禁破坏其他子 Agent 已合入的研究产物。

## 阶段与职责对照表

| 阶段 | 关联 Issue | 执行主体 | 分支动作 | 核心文档产物 | 结束条件 |
| --- | --- | --- | --- | --- | --- |
| **第一阶段：仓库摸底** | Issue A | 主 Agent | 从 `dev` 派生临时分支，完成后合回 `dev` | `docs/research/github-references/related-repositories.md` | 合入 `dev` 并关闭 Issue A（若无有效仓库则直接跳出并汇报用户） |
| **第二阶段：单仓深挖** | 系列 Issue B（每仓一个） | 多个子 Agent 并行 | 每个 Issue 从 `dev` 派生独立临时分支，完成后各自合回 `dev` | `docs/research/repositories/<仓库名>/README.md` 及 `source-index.md` 等 | 所有单仓分支合入 `dev`，系列 Issue B 全部关闭 |
| **第三阶段：全局综述** | Issue C | 综述子 Agent | 从 `dev` 派生临时分支，完成后合回 `dev` | `docs/research/github-references/README.md` 及浓缩版 `source-index.md` 等 | 合入 `dev` 并关闭 Issue C，主 Agent 向用户汇报总结 |