---
title: "LeCun 当众炮轰：你们的 AI Agent 连后果都预测不了，「可能很危险」！融 10 亿美元另起炉灶"
source: "https://mp.weixin.qq.com/s/xI2k7rTTaYcoPAK7DH6sGw"
author:
  - "[[智能纪元]]"
published:
created: 2026-05-15
description: "LeCun 当众炮轰：你们的 AI Agent 连后果都预测不了，「可能很危险」！融 10 亿美元另起炉灶"
tags:
  - "clippings"
---
智能纪元 *2026年5月15日 05:22*

导读  
【导读】图灵奖得主 Yann LeCun 在 Brown 大学演讲中直言：当前几乎所有 AI Agent 都无法预测自己行动的后果。他认为没有世界模型的 Agent 根本谈不上可靠，甚至可能带来危险。他创办的 AMI Labs 已融资超 10 亿美元，估值 35 亿，赌的就是 LLM 路线走不通。

## 「它们只管行动，后果是别人的事」

今天，Haider 在 X 上发了一段 LeCun 的观点摘录，把这位图灵奖得主关于 Agent 可靠性的判断推到了台前。

![Haider 转述 LeCun 观点的推文（分段1）](https://mmbiz.qpic.cn/mmbiz_jpg/yxr7ld7e0HozAQcO1IVTkk6nwt1n8zs0Q8ZceCdurDCCtIWgsuxficCcojXKFroTI5a0q8Mpy4bUN8h8ImST9ictTuibSGq8aWHbwTftjrrlYc/640?wx_fmt=jpeg&from=appmsg&watermark=1&tp=webp&wxfrom=5&wx_lazy=1#imgIndex=0)

Haider 转述 LeCun 观点的推文（分段1）

▲ Haider 转述 LeCun 观点，引发大量讨论

帖子的核心论点：

> "Yann LeCun says you cannot build a reliable agentic system without a world model."

「没有世界模型，就造不出可靠的 Agent 系统。」

> "They can't predict the consequences of their actions before taking them. 'they just act, and whatever happens next is someone else's problem'."

「它们无法在行动前预测后果——只管动手，出了事是别人的问题。」

说法够狠。但有没有出处？

有。而且 LeCun 本人说得比这更狠。

## Brown 大学演讲：「AI 很烂」

根据 Brown 大学 2026 年 4 月 1 日的官方报道，LeCun 今年在 Pembroke Hall 做了一场讲座，全场座无虚席。

![Brown University 讲座报道](data:image/svg+xml,%3C%3Fxml version='1.0' encoding='UTF-8'%3F%3E%3Csvg width='1px' height='1px' viewBox='0 0 1 1' version='1.1' xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg stroke='none' stroke-width='1' fill='none' fill-rule='evenodd' fill-opacity='0'%3E%3Cg transform='translate(-249.000000, -126.000000)' fill='%23FFFFFF'%3E%3Crect x='249' y='126' width='1' height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

Brown University 讲座报道

▲ Brown 大学官方报道，标题直接写明「a new approach to AI」

开场白只有两个词：

> "AI sucks."

「AI 很烂。」

然后他解释了为什么：

> "We have systems that can manipulate language, and they fool us into thinking they are smart because they manipulate language. But in fact, they are completely helpless when it comes to the physical world."

「现有系统会操纵语言，让我们误以为它们聪明。但面对物理世界，它们完全无助。」

接下来他直接点名 Agent：

> "everybody these days in AI is talking about agentic systems — systems that can produce actions in the world — and almost none of those systems at the moment are capable of predicting the outcome… of their actions. It's a very bad way to produce an action… if you're not able to predict the consequences of it. In fact, it might be dangerous."

「如今 AI 领域人人都在谈 agentic systems——能在真实世界中产生行动的系统——但眼下几乎没有一个能预测自身行动的结果。不能预测后果就行动，这种方式很糟糕。事实上， **可能很危险** 。」

最后这个判断最重。图灵奖得主、Meta 前首席 AI 科学家、FAIR 创始人，在常春藤名校的讲座上，当着全场观众的面，给当前整个 Agent 生态下了定性。

## LeCun 要的「世界模型」到底是什么？

很多人的第一反应是：LLM 已经"知道"很多关于世界的知识了啊？它能回答物理问题、写代码、做数学推理，怎么就没有世界模型了？

这里有一个关键区别。

LeCun 早在 2022 年就在 position paper《A Path Towards Autonomous Machine Intelligence》里定义过他所说的世界模型：

![OpenReview 论文页面](data:image/svg+xml,%3C%3Fxml version='1.0' encoding='UTF-8'%3F%3E%3Csvg width='1px' height='1px' viewBox='0 0 1 1' version='1.1' xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg stroke='none' stroke-width='1' fill='none' fill-rule='evenodd' fill-opacity='0'%3E%3Cg transform='translate(-249.000000, -126.000000)' fill='%23FFFFFF'%3E%3Crect x='249' y='126' width='1' height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

OpenReview 论文页面

▲ LeCun 2022 年发表的 AMI 路线图论文，OpenReview 上已有 67 条讨论

论文的核心问题：

> "How could machines learn to reason and plan?"

「机器如何学会推理和规划？」

他给出的答案组合： **configurable predictive world model** （可配置预测世界模型）+ **intrinsic motivation** （内在动机）+ **hierarchical joint embedding architectures** （层级联合嵌入架构）。

简单来说：LeCun 要的世界模型，能在你行动之前，先在内部"跑一遍模拟"，预测这个行动会让外部世界变成什么样。你决定删一个文件之前，模型内部先模拟删完之后系统状态会怎样变化；你让机器人走过一扇门之前，它先在内部"看到"门后面的空间。

这跟 LLM 的 next-token prediction 完全是两码事。LLM 预测的是 **下一个词** ，LeCun 要预测的是 **下一步世界状态** 。

## JEPA：从论文走向代码

LeCun 不光在台上喊。Meta AI 在他主导下已经推出了两个实验性成果。

2023 年 6 月，Meta 发布了 **I-JEPA** ——基于 LeCun 提出的联合嵌入预测架构的第一个模型。

![Meta I-JEPA 博客页面](data:image/svg+xml,%3C%3Fxml version='1.0' encoding='UTF-8'%3F%3E%3Csvg width='1px' height='1px' viewBox='0 0 1 1' version='1.1' xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg stroke='none' stroke-width='1' fill='none' fill-rule='evenodd' fill-opacity='0'%3E%3Cg transform='translate(-249.000000, -126.000000)' fill='%23FFFFFF'%3E%3Crect x='249' y='126' width='1' height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

Meta I-JEPA 博客页面

▲ Meta 官方博客介绍 I-JEPA，强调「learn internal models of how the world works」

I-JEPA 的核心思路：通过创建外部世界的内部模型来学习，在抽象表示空间中比较和预测，而非逐像素重建。

> "create machines that can learn internal models of how the world works so that they can learn much more quickly, plan how to accomplish complex tasks, and readily adapt to unfamiliar situations."

「造出能学习世界运作方式的内部模型的机器，让它们更快学习、规划复杂任务、适应陌生情境。」

效果上，I-JEPA 用一个 632M 参数的 visual transformer，在 16 张 A100 上训练不到 72 小时，每类只用 12 个标注样本就在 ImageNet 上取得了有竞争力的表现。

2024 年 2 月，Meta 又推出 **V-JEPA** ，从图片扩展到视频。Meta 称其为 **物理世界模型的早期示例** ——能检测和理解物体之间的细粒度交互。LeCun 的评价：

> "V-JEPA is a step toward a more grounded understanding of the world so machines can achieve more generalized reasoning and planning."

「V-JEPA 是迈向更扎实的世界理解的一步，让机器实现更通用的推理和规划。」

不过，I-JEPA 和 V-JEPA 都还在研究阶段，离"可靠 Agent"这个目标还很远。但它们展示了一条截然不同的路线—— **在抽象表示空间里预测世界变化，而非靠语言拼接出答案** 。

## 10 亿美元的赌注

LeCun 最近的动作更大。

据 WIRED 报道，他联合创办的 **Advanced Machine Intelligence (AMI) Labs** 已宣布融资超过 **10 亿美元** ，估值 **35 亿美元** 。目标只有一个：开发 AI world models。

MIT Technology Review 的报道标题更直白：《Yann LeCun's new venture is a contrarian bet against large language models》——LeCun 的新公司，赌的就是 LLM 这条路走不通。

LeCun 对 WIRED 说了句更绝的：

> "The idea that you're going to extend the capabilities of LLMs to the point that they're going to have human-level intelligence is complete nonsense."

「认为可以把 LLM 的能力延伸到人类级智能——完全是胡说八道。」

从 Meta 内部研究到 10 亿美元创业，LeCun 用真金白银表明了立场。

## 评论区吵翻了

帖子下面的争论可以分成三派。

**支持派** 认为 LeCun 戳中了当前 Agent 的核心缺陷。有人总结：next-token prediction 和 next-state-of-the-world prediction 根本就是两个目标。让当前 LLM Agent 执行多步骤任务，它只能根据当前反馈做出反应，没有能力在内部模拟接下来三步会发生什么。

**工程折中派** 承认问题存在，但认为可以用工程手段缓解。比如给 Agent 加一个 judge agent，在重要变更前先审查是否会破坏系统；或者加一层 lightweight "expectation layer"，让 Agent 行动前预测预期结果，行动后对比偏差。这些方案在实践中确实有效，但跟 LeCun 说的完整 world model 还差了好几个数量级。

**质疑派** 则认为"LLM 完全不能预测后果"这个说法太绝对。LLM 在文本中完全可以表达 if-then 因果推理，在文件操作、代码修改等任务中也清楚自己的目标。这个反驳有道理，但要看场景——LeCun 的批评主要指向需要与物理世界或复杂系统交互的情况，而非纯文本问答。

## 好用和可靠之间，隔着一个世界模型

当前 LLM Agent 已经在创造真实价值——coding agents、browser agents、客服自动化——生产环境里实打实跑着。

但 LeCun 指出的问题同样真实：这些 Agent 的可靠性高度依赖外部兜底——sandbox、权限边界、人工审核、重试逻辑。模型本身不理解"这一步会不会搞崩系统"，它只知道"根据当前 context，下一步应该输出什么"。

**当前 Agent 有用，但还不够可靠。工程层能兜底，但兜不住所有。**

LeCun 押注的方向，是让模型从内部就具备预测后果的能力。10 亿美元、35 亿估值——这个赌注已经摆上台面了。

至于他能不能赢，这可能是未来五年 AI 领域最值得关注的悬念之一。

---

— END —

— END —

作者提示: 个人观点，仅供参考

继续滑动看下一个

未来跃迁

向上滑动看下一个