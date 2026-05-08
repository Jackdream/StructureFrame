---
title: "腾讯混元干了件大事：Skill Graphs"
source: "https://mp.weixin.qq.com/s/9haSDoOJ1KVTjHbzsXa5Qg"
author:
  - "[[PaperRAG]]"
published:
created: 2026-05-07
description:
tags:
  - "clippings"
---
PaperRAG *2026年5月2日 21:06*

想象你在训练一个 AI 操作命令行终端。直觉告诉你：给它安排越多的练习任务，它就会越强。但腾讯混元团队的最新研究发现，这个直觉可能是错的——真正决定训练效果的不是任务数量，而是 AI 在执行这些任务时经历了多少种 **不同的场景和技能组合** 。

![图片](https://mmbiz.qpic.cn/sz_mmbiz_png/0DOaHQeiaNPGmLz9ujf1ZmehvbC8OCqJibm1CDtmKZz0UVsl9F4t6mshZo1iaTibm0NAkwf2iaTYrGuBSsvrc9YoFwv1WePzcE2w6oXu5YYFrbbI/640?wx_fmt=png&from=appmsg&watermark=1&tp=webp&wxfrom=5&wx_lazy=1#imgIndex=0)

他们构建了一张包含 **8.2 万个场景节点** 、 **5.7 万项技能** 的"技能图谱"，从图中采样多样化的工作流路径来生成训练任务。结果：用这种方式训练的 **Qwen3-32B** （320 亿参数），在权威终端 Agent 基准 Terminal-Bench 2.0 上得分 \*\*29.6%\*\*，直接超越了参数量是它 15 倍的 **Qwen 3 Coder 480B** （23.9%）。

## 问题在哪：堆任务数量，不管轨迹多样性

终端 Agent 是指用大语言模型驱动、通过命令行界面完成复杂任务的 AI 系统。训练这样的 Agent 需要大量"执行轨迹"——也就是 AI 在终端里一步步操作的全过程记录。

现有的合成训练数据方法主要走两条路：要么让 LLM 生成分类体系来扩展领域覆盖（但往往和真实使用脱节），要么从 GitHub 仓库反推任务（但局限在软件工程场景）。两条路都只关心"生成多少任务"，却没有控制 AI 在这些任务里到底经历了多少种不同的"场景×技能"组合。

![轨迹多样性对比](https://mmbiz.qpic.cn/sz_mmbiz_png/0DOaHQeiaNPES3aT7Vut6JnIVeTt1cwkC56qkAHI2WhufNp3IIp5icZRZpYq3TLicx5ZFXfLH8GAUOc4ALBicvwwniaghich0XXAl18525BibhEiczg/640?wx_fmt=png&from=appmsg&watermark=1&tp=webp&wxfrom=5&wx_lazy=1#imgIndex=1)

轨迹多样性对比

论文用数据直接展示了这个问题：现有数据集中，不同任务让 Agent 经历的场景和技能高度重叠，轨迹冗余严重。

## 核心方法：用图谱结构控制训练轨迹的多样性

**SkillSynth** 的核心思路是把 AI 操作终端的过程抽象成"场景-技能"序列。

- **场景** ：AI 在某个决策点面临的状态（比如"视频文件已下载但未压缩"）
- **技能** ：AI 在这个状态下执行的一组动作（比如"用 ffmpeg 压缩视频"）

每个技能从一个"前置场景"指向一个"后置场景"，形成有向图。图中的一条路径，就对应一个真实的多步骤工作流。

![图片](data:image/svg+xml,%3C%3Fxml version='1.0' encoding='UTF-8'%3F%3E%3Csvg width='1px' height='1px' viewBox='0 0 1 1' version='1.1' xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg stroke='none' stroke-width='1' fill='none' fill-rule='evenodd' fill-opacity='0'%3E%3Cg transform='translate(-249.000000, -126.000000)' fill='%23FFFFFF'%3E%3Crect x='249' y='126' width='1' height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

这个图谱的规模非常可观： **82,073 个场景节点** 、 **57,214 条技能边** 、 **185,529 个 LLM 验证的桥接关系** 。85.6% 的节点连通在最大连通分量中，意味着绝大多数技能都能串联成完整的工作流。

![图片](data:image/svg+xml,%3C%3Fxml version='1.0' encoding='UTF-8'%3F%3E%3Csvg width='1px' height='1px' viewBox='0 0 1 1' version='1.1' xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg stroke='none' stroke-width='1' fill='none' fill-rule='evenodd' fill-opacity='0'%3E%3Cg transform='translate(-249.000000, -126.000000)' fill='%23FFFFFF'%3E%3Crect x='249' y='126' width='1' height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

构建过程分五步：从 ClawHub 和 GitHub 过滤技能 → LLM 推断每个技能的前置/后置场景 → 聚类去重 → 跨技能对齐（后置场景匹配下一个技能的前置场景）→ 合并过滤。

采样策略也很关键：用 **逆频率加权** ——被访问少的节点和边优先被选中，避免路径扎堆在热门节点上。这保证了采样出的路径在"场景×技能"空间上的均匀覆盖。

## 自动生成：多 Agent 协作，一次跑出 3560 个验证过的任务

采样出路径后，一个多 Agent 协作流程把抽象路径变成具体的可执行任务：

1. **规划器** 把路径转化成结构化的子目标和预期输出
2. **构造器** 根据计划生成完整任务实例（指令、文件系统快照、容器环境、验证脚本、参考解法）
3. **双验证** ：执行验证（跑参考解法确保任务可解）+ 评分验证（LLM 判断指令和测试是否对齐）
4. 不通过则进入修复循环，最多 **3 轮修复** ，每轮最多 20 次工具调用
![图片](data:image/svg+xml,%3C%3Fxml version='1.0' encoding='UTF-8'%3F%3E%3Csvg width='1px' height='1px' viewBox='0 0 1 1' version='1.1' xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg stroke='none' stroke-width='1' fill='none' fill-rule='evenodd' fill-opacity='0'%3E%3Cg transform='translate(-249.000000, -126.000000)' fill='%23FFFFFF'%3E%3Crect x='249' y='126' width='1' height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

一次全自动运行的成绩单：从 3,721 条采样路径中产出 **3,560 个通过验证的任务实例** ， **95.7% 的 oracle 通过率** ，平均成本仅 **$27.3/个** 。这些任务难度不低——Claude Opus 4.6 平均需要 **37 步** 才能解决， **121 个任务三次尝试都没解出来** 。

## 实验结果：多样性 > 数量

核心对比数据：

| 方法 | TB 1.0 | TB 2.0 |
| --- | --- | --- |
| Qwen3-8B + 单技能 | 8.7% | 5.3% |
| Qwen3-8B + 随机多技能 | 13.4% | 11.6% |
| Qwen3-8B + **SkillSynth** | **17.1%** | **13.5%** |
| Qwen3-32B + 单技能 | 25.4% | 21.3% |
| Qwen3-32B + 随机多技能 | 30.8% | 25.8% |
| Qwen3-32B + **SkillSynth** | **33.8%** | **29.6%** |
| Qwen 3 Coder 480B（未用 SkillSynth） | — | 23.9% |

SkillSynth 比单技能基线高 **8.4 分** （TB 1.0），比随机组合多技能基线高 **3.0 分** 。多样性指标更直接：SkillSynth 轨迹的唯一"场景-技能"覆盖率比单技能高 \*\*31%\*\*，比随机多技能高 \*\*19%\*\*。

![图片](data:image/svg+xml,%3C%3Fxml version='1.0' encoding='UTF-8'%3F%3E%3Csvg width='1px' height='1px' viewBox='0 0 1 1' version='1.1' xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg stroke='none' stroke-width='1' fill='none' fill-rule='evenodd' fill-opacity='0'%3E%3Cg transform='translate(-249.000000, -126.000000)' fill='%23FFFFFF'%3E%3Crect x='249' y='126' width='1' height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

消融实验还揭示了一个重要发现：随机拼凑多个技能（不经过图谱引导）效果明显更差，因为随机组合缺乏 **工作流连贯性** ——生成的任务包含多个细碎要求，但实际执行步骤很少。

![图片](data:image/svg+xml,%3C%3Fxml version='1.0' encoding='UTF-8'%3F%3E%3Csvg width='1px' height='1px' viewBox='0 0 1 1' version='1.1' xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg stroke='none' stroke-width='1' fill='none' fill-rule='evenodd' fill-opacity='0'%3E%3Cg transform='translate(-249.000000, -126.000000)' fill='%23FFFFFF'%3E%3Crect x='249' y='126' width='1' height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

## 这意味着什么

**SkillSynth 已经不只是论文里的方法了** 。它生成的任务实例已被腾讯混元团队用于训练 **Hy3 Preview** 模型，直接提升了终端场景下的 Agent 能力。

![技能领域分布](data:image/svg+xml,%3C%3Fxml version='1.0' encoding='UTF-8'%3F%3E%3Csvg width='1px' height='1px' viewBox='0 0 1 1' version='1.1' xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg stroke='none' stroke-width='1' fill='none' fill-rule='evenodd' fill-opacity='0'%3E%3Cg transform='translate(-249.000000, -126.000000)' fill='%23FFFFFF'%3E%3Crect x='249' y='126' width='1' height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

技能领域分布

图谱本身还在持续扩展——随着 ClawHub 社区贡献更多技能，图谱自动生长，任务的多样性持续提升。目前图谱已覆盖编码、文档处理、DevOps、安全等常见领域，也包括音频语音、3D 仿真、IoT 硬件等长尾领域。

![图谱度分布](data:image/svg+xml,%3C%3Fxml version='1.0' encoding='UTF-8'%3F%3E%3Csvg width='1px' height='1px' viewBox='0 0 1 1' version='1.1' xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg stroke='none' stroke-width='1' fill='none' fill-rule='evenodd' fill-opacity='0'%3E%3Cg transform='translate(-249.000000, -126.000000)' fill='%23FFFFFF'%3E%3Crect x='249' y='126' width='1' height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

图谱度分布

对 AI 从业者来说，这篇论文传递的核心信息很明确： **训练 Agent 的胜负手不在参数量，也不在任务数量，而在训练轨迹的多样性** 。如果你在做 Agent 训练数据，与其堆量，不如用图谱结构控制"场景×技能"的覆盖密度。

```
论文标题: Toward Scalable Terminal Task Synthesis via Skill Graphs
论文链接: https://arxiv.org/abs/2604.25727v1
```

Agent · 目录

继续滑动看下一个

PaperToday

向上滑动看下一个