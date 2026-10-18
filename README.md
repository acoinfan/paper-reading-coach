# paper-reading-coach

让 AI Agent 当你的**论文阅读教练**，而不是论文摘要机。

读论文的目标不是背下每篇论文，而是练出能迁移的能力：看懂实验在验证什么、读懂一张没见过的图、分清「能读出来」和「真的被用上」、想到替代解释并设计对照实验。这个仓库把一套实际跑通的训练方法整理成了可以直接交给 Agent 的规则、流程和模板。

## 核心想法

- **先训练，再给答案。** Agent 先让你自己说，你说完它再纠正。你明确要求讲解时，它才直接讲。
- **记录要严格。** 只有你不看答案、独立完成的练习，才能让技能状态升级；听懂了讲解、被提示后才答对，都不算掌握。错误按类型记下来，同一个错误出现第二次要单独标出。
- **原文事实和推断分开。** 每条主张都标上【原文】【作者解释】【推断】【待验证】，并注明章节、图号。Agent 自己写错的地方也要留下更正记录。
- **一篇论文分五轮读**，每轮有明确的阅读范围、问题和产出，见 [docs/five-round-reading.md](docs/five-round-reading.md)。
- **读图有固定套路**：先念轴和图例，再看数据；每个数字都问「和什么比」，见 [docs/figure-reading.md](docs/figure-reading.md)。

## 仓库内容

| 文件 | 内容 |
|---|---|
| [MANUAL.md](MANUAL.md) | 完整手册：目标、工作流、笔记类型、Agent 的角色、复习方法、检查清单 |
| [AGENTS.md](AGENTS.md) | 直接交给 Agent 的规则（Claude Code、Codex 等能读项目指令文件的 Agent 都可以用） |
| [docs/five-round-reading.md](docs/five-round-reading.md) | 一篇论文的五轮训练流程、评分规则和复测方法 |
| [docs/figure-reading.md](docs/figure-reading.md) | 读图五问、找基线、热图和 PCA 图的读法 |
| [templates/](templates/) | 论文、方法、主题、图表、技能五种笔记模板 |
| [examples/](examples/) | 一张论文卡片和一份技能记录的示例 |

## 怎么开始

1. 新建一个空目录作为你的知识库（建议用 git 管理；也可以同时作为 Obsidian 仓库打开，双链直接能用）。
2. 把本仓库的 `AGENTS.md`、`templates/` 复制进去，按 MANUAL.md 第 14 节先建最小结构：

   ```
   your-kb/
   ├── README.md
   ├── AGENTS.md
   ├── papers/
   ├── methods/
   ├── topics/
   ├── skills/
   └── templates/
   ```

3. 在 `AGENTS.md` 末尾的「本库约定」里写上你的研究方向和论文 PDF 放在哪里。
4. 对 Agent 说：「读 AGENTS.md，按五轮流程带我读这篇论文：<论文>」。
5. 每轮结束时让 Agent 更新论文卡片和技能记录，检查 `git diff` 后再提交。

## 一个真实的例子

[examples/](examples/) 里的两份文件来自实际训练（个人信息已去除）：

- `paper-card-example.md`：一篇关于 LLM 上下文学习中物理表示的论文卡片，包括证据标签、Agent 的更正记录，以及「这篇论文证明了什么、没证明什么」。
- `skill-record-example.md`：一道「为什么梯度归因高不等于证明了因果」的练习记录，展示了如何如实记录「没有提示时答不出、提示后部分答对」。

## 致谢

流程以 MANUAL.md 为基础，在实际训练中补充了五轮阅读、严格评分和读图方法。

## 许可

本仓库内容采用 [CC BY 4.0](LICENSE) 许可：可以自由使用、修改和再分发，只需注明出处。
