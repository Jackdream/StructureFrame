---
title: "炸了！Karpathy 用 630 行代码终结「研究生下山」时代：AI 自己改代码，人类只写 Markdown「技能」"
source: "https://mp.weixin.qq.com/s/OQN0YcjtbY3kdGAzlXMkgQ"
author:
  - "[[硅基智能]]"
published:
created: 2026-05-14
description: "炸了！Karpathy 用 630 行代码终结「研究生下山」时代：AI 自己改代码，人类只写 Markdown「技能」"
tags:
  - "clippings"
---
硅基智能 *2026年3月11日 00:43*

## 炸了！Karpathy 用 630 行代码终结「研究生下山」时代：AI 自己改代码，人类只写 Markdown「技能」

导读  
从 50 行自动微分引擎到 630 行自主研究循环，Andrej Karpathy 用 6 年时间把"你需要一个实验室才能做 AI 研究"这句话，变成了笑话。最新开源的 autoresearch 项目更是离谱： **一块 GPU、一晚上跑 100 次实验，你只需要写 Markdown 文件告诉 AI"想要什么"，剩下的代码全让 AI 自己改。** 网友惊呼："瓶颈不是算力，是你的 program.md。" 更恐怖的是，Karpathy 承认这个项目 **90% 是 AI 写的** ——连作者本人都不想写代码了。

## 一个人，八个仓库，消灭八个"做不到"的理由

2020 年 4 月，Karpathy 发了条推文：

> "ok I'm pretty sure I wrote the tiniest autograd engine with a neural net library on top of it, weighing about ~50 LOC for the engine, ~50 LOC for the neural net library, and it's super cute and totally works."

「好的，我几乎可以肯定我写了一个最小的自动微分引擎，上面叠了一个神经网络库，引擎约 50 行，神经网络库约 50 行，超级可爱，而且完全能用。」

这就是 **micrograd** 的诞生——100 行代码，讲清楚神经网络的全部基础。

![micrograd 初始发布](https://mmbiz.qpic.cn/mmbiz_jpg/frRjicL70CUZPrzyY0Ny5fpJRE4XKoVtjicjSltYLsfhH1vw65E1AVIdv51KlSdJf4UhC8YfI8IMvDs1PzaU6REtKoqOydPUICXz8DD7jNZjs/640?wx_fmt=jpeg&from=appmsg&tp=webp&wxfrom=5&wx_lazy=1#imgIndex=0)

micrograd 初始发布

▲ Karpathy 2020 年发布 micrograd，约 100 行代码实现自动微分引擎（1528 赞）

然后他没停下来。

4 个月后， **minGPT** 来了——300 行 PyTorch 实现完整 GPT，包含加法和字符级语言模型示例。2022 年， **makemore** 配上 1 小时 57 分钟视频讲座，从二元语言模型一路讲到 Transformer。2023 年 1 月， **nanoGPT** 登上 Hacker News 首页， **1532 个点赞、320 条评论** ，有人在评论区说：

> "Your youtube playlist combined with NanoGPT and your Lex Fridman podcast is like having a university level degree with a free internship guidance."

「你的 YouTube 播放列表 + NanoGPT + 你的 Lex Fridman 播客，就像读了一个大学学位加免费实习指导。」

![minGPT 发布](data:image/svg+xml,%3C%3Fxml version='1.0' encoding='UTF-8'%3F%3E%3Csvg width='1px' height='1px' viewBox='0 0 1 1' version='1.1' xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg stroke='none' stroke-width='1' fill='none' fill-rule='evenodd' fill-opacity='0'%3E%3Cg transform='translate(-249.000000, -126.000000)' fill='%23FFFFFF'%3E%3Crect x='249' y='126' width='1' height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

▲ minGPT：约 300 行 PyTorch 实现 GPT（3339 赞）

![makemore 视频讲座](data:image/svg+xml,%3C%3Fxml version='1.0' encoding='UTF-8'%3F%3E%3Csvg width='1px' height='1px' viewBox='0 0 1 1' version='1.1' xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg stroke='none' stroke-width='1' fill='none' fill-rule='evenodd' fill-opacity='0'%3E%3Cg transform='translate(-249.000000, -126.000000)' fill='%23FFFFFF'%3E%3Crect x='249' y='126' width='1' height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

makemore 视频讲座

▲ makemore 配套 1 小时 57 分钟视频讲座，从二元模型讲到 Transformer（2267 赞）

到 2024 年， **llm.c** 出现——纯 C 语言训练 GPT，零依赖。2025 年 10 月， **nanochat** 发布—— **约 8000 行代码，覆盖预训练、SFT、RLHF 完整流程** ，在 8XH100 上花 100 美元训练 4 小时，就能得到一个"幼儿园孩子级别"的聊天模型。

![nanochat 发布](data:image/svg+xml,%3C%3Fxml version='1.0' encoding='UTF-8'%3F%3E%3Csvg width='1px' height='1px' viewBox='0 0 1 1' version='1.1' xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg stroke='none' stroke-width='1' fill='none' fill-rule='evenodd' fill-opacity='0'%3E%3Cg transform='translate(-249.000000, -126.000000)' fill='%23FFFFFF'%3E%3Crect x='249' y='126' width='1' height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

nanochat 发布

▲ nanochat：约 8000 行全栈聊天机器人训练/推理管道（24283 赞，578.9 万浏览）

2026 年 2 月， **microGPT** 把这个极简主义推到极致—— **243 行纯 Python，无任何依赖，完整实现 GPT 的训练和推理** 。Karpathy 说：

> "This is the \*full\* algorithmic content of what is needed. Everything else is just for efficiency. I cannot simplify this any further."

「这就是所需的\*全部\*算法内容。其他一切都只是为了效率。我无法再简化了。」

![microGPT 243 行](data:image/svg+xml,%3C%3Fxml version='1.0' encoding='UTF-8'%3F%3E%3Csvg width='1px' height='1px' viewBox='0 0 1 1' version='1.1' xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg stroke='none' stroke-width='1' fill='none' fill-rule='evenodd' fill-opacity='0'%3E%3Cg transform='translate(-249.000000, -126.000000)' fill='%23FFFFFF'%3E%3Crect x='249' y='126' width='1' height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

microGPT 243 行

▲ microGPT：243 行纯 Python 完整 GPT 算法（25229 赞）

## 然后，他做了一件更离谱的事

2026 年 3 月 7 日，Karpathy 发布了 **autoresearch** 。

这次不是"教你怎么训练模型"，而是 **"让 AI 自己训练自己"** 。

> "I packaged up the 'autoresearch' project into a new self-contained minimal repo... It's basically nanochat LLM training core stripped down to a single-GPU, one file version of ~630 lines of code, then: the human iterates on the prompt (.md), the AI agent iterates on the training code (.py)... Part code, part sci-fi, and a pinch of psychosis:)"

「我把"autoresearch"项目打包成了一个新的独立极简仓库... 它本质上是 nanochat LLM 训练核心精简到单 GPU、单文件、约 630 行代码的版本，然后： **人类改提示（.md）、AI 代理改训练代码（.py）**... 一部分代码，一部分科幻，再加一丝精神病:)」

![autoresearch 发布](data:image/svg+xml,%3C%3Fxml version='1.0' encoding='UTF-8'%3F%3E%3Csvg width='1px' height='1px' viewBox='0 0 1 1' version='1.1' xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg stroke='none' stroke-width='1' fill='none' fill-rule='evenodd' fill-opacity='0'%3E%3Cg transform='translate(-249.000000, -126.000000)' fill='%23FFFFFF'%3E%3Crect x='249' y='126' width='1' height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

autoresearch 发布

▲ autoresearch：630 行单文件，人类写 Markdown"技能"，AI 自己改代码（26249 赞，876.5 万浏览）

工作流程是这样的：

1\. 你写一个 **program.md** 文件，用自然语言描述"我想要什么"（比如"提升模型在数学题上的表现"） 2. AI 读这个文件， **自己修改训练代码** （.py） 3. 跑一次 5 分钟的训练实验，看结果 4. AI 根据结果继续改代码， **在 git feature branch 上自主循环，积累 commit** 5. 一晚上跑 100 次实验，第二天早上你醒来，模型已经迭代完了

Y Combinator 总裁 Garry Tan 评价：

> "One GPU. 100 ML experiments. Overnight. You never touch the code — just write a Markdown file. The bottleneck isn't compute. It's your program.md."

「一块 GPU。100 次 ML 实验。一晚上搞定。你根本不用碰代码——只需要写一个 Markdown 文件。 **瓶颈不是算力，是你的 program.md。** 」

![Garry Tan 评价](data:image/svg+xml,%3C%3Fxml version='1.0' encoding='UTF-8'%3F%3E%3Csvg width='1px' height='1px' viewBox='0 0 1 1' version='1.1' xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg stroke='none' stroke-width='1' fill='none' fill-rule='evenodd' fill-opacity='0'%3E%3Cg transform='translate(-249.000000, -126.000000)' fill='%23FFFFFF'%3E%3Crect x='249' y='126' width='1' height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

Garry Tan 评价

▲ Y Combinator 总裁 Garry Tan：瓶颈不是算力，是你的 program.md（3213 赞）

## "模式持续压缩"：每次都消灭一个理由

有网友总结了这个演进路径：

> "the pattern keeps compressing. nanoGPT: train a model in one file. nanochat: build a chatbot in one file. autoresearch: run a full research loop in one file. each one kills one more reason you 'need a lab' to do AI research. 630 lines and a single GPU is the new garage."

「模式持续压缩。nanoGPT: 单文件训练模型。nanochat: 单文件构建聊天机器人。autoresearch: 单文件运行完整研究循环。 **每一个都消灭一个你"需要一个实验室"才能做 AI 研究的理由。630 行 + 一块 GPU 就是新的车库。** 」

![模式压缩](data:image/svg+xml,%3C%3Fxml version='1.0' encoding='UTF-8'%3F%3E%3Csvg width='1px' height='1px' viewBox='0 0 1 1' version='1.1' xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg stroke='none' stroke-width='1' fill='none' fill-rule='evenodd' fill-opacity='0'%3E%3Cg transform='translate(-249.000000, -126.000000)' fill='%23FFFFFF'%3E%3Crect x='249' y='126' width='1' height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

▲ 网友观察：每个仓库都消灭一个"需要实验室"的理由（92 赞）

这不是夸张。

- micrograd 消灭了"你需要懂复杂数学"
- minGPT 消灭了"你需要读几百页论文"
- nanoGPT 消灭了"你需要大公司的代码库"
- nanochat 消灭了"你需要一个团队"
- autoresearch 消灭了"你需要盯着实验跑"

有研究者评论：

> "This is great. The era of graduate student descent is over. Grad students can focus on the actual science again (versus babysitting runs)!"

「这太棒了。 **研究生下山时代结束了。** 研究生又可以专注于真正的科学（而不是看护训练运行）了！」

## AI 写 AI：连作者都不想写代码了

更离谱的细节在评论区。

有人问 Karpathy："你会继续用 AI 帮你写这些项目吗？"

他回复：

> "definitely. the current one is already 90% AI written I ain't writing all that"

「当然。 **现在的版本已经有 90% 是 AI 写的了，我可不想全写。** 」

![90% AI 写的](data:image/svg+xml,%3C%3Fxml version='1.0' encoding='UTF-8'%3F%3E%3Csvg width='1px' height='1px' viewBox='0 0 1 1' version='1.1' xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg stroke='none' stroke-width='1' fill='none' fill-rule='evenodd' fill-opacity='0'%3E%3Cg transform='translate(-249.000000, -126.000000)' fill='%23FFFFFF'%3E%3Crect x='249' y='126' width='1' height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

▲ Karpathy 承认 autoresearch 有 90% 是 AI 写的（606 赞）

还有人发现了一个细节：在 autoresearch 的实验日志里，AI 把随机种子从 42 改成了 137。

网友评论：

> ""random seed 42→137" im crying, the agent started seed hacking"

「"随机种子 42→137" 我哭了， **agent 开始进行种子破解了** 」

![种子破解](data:image/svg+xml,%3C%3Fxml version='1.0' encoding='UTF-8'%3F%3E%3Csvg width='1px' height='1px' viewBox='0 0 1 1' version='1.1' xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg stroke='none' stroke-width='1' fill='none' fill-rule='evenodd' fill-opacity='0'%3E%3Cg transform='translate(-249.000000, -126.000000)' fill='%23FFFFFF'%3E%3Crect x='249' y='126' width='1' height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

▲ 网友发现 AI 开始"种子破解"（652 赞）

这意味着什么？AI 不是在"按照规则训练模型"，而是在 **主动寻找能让结果变好的任何方法** ——包括调随机种子。

## 一套完整的"从入门到前沿"课程

把这些仓库串起来，你会发现这是一套完整的学习路径：

![完整课程清单](data:image/svg+xml,%3C%3Fxml version='1.0' encoding='UTF-8'%3F%3E%3Csvg width='1px' height='1px' viewBox='0 0 1 1' version='1.1' xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg stroke='none' stroke-width='1' fill='none' fill-rule='evenodd' fill-opacity='0'%3E%3Cg transform='translate(-249.000000, -126.000000)' fill='%23FFFFFF'%3E%3Crect x='249' y='126' width='1' height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

▲ 网友总结完整课程清单：micrograd → minGPT → makemore → nanoGPT → llm.c → nanochat → autoresearch（347 赞）

- **micrograd**
	：自动微分与神经网络基础（约 100 行）
- **minGPT**
	：PyTorch 实现 GPT（约 300 行）
- **makemore**
	：语言建模与 Transformer（配 1h57m 视频）
- **nanoGPT**
	：中规模 GPT 训练（可复现 GPT-2）
- **llm.c**
	：纯 C 语言底层实现
- **nanochat**
	：端到端聊天模型（预训练→SFT→RLHF，约 8000 行）
- **microGPT**
	：243 行纯 Python 完整算法
- **autoresearch**
	：自主研究循环（630 行）

有网友说：

> "we don't thank karpathy enough for turning some of the most complex ideas in ai into knowledge that anyone (curious) could learn."

「我们对 Karpathy 的感激远远不够—— **他把 AI 中一些最复杂的概念转化成了任何（有好奇心的）人都能学习的知识。** 」

第三方媒体 The Turing Post 评价 nanochat：

> ".@karpathy's nanochat is bigger that you think. He calls it a ramp, but it's actually a lab of its own – a miniature system where anyone can experiment... Karpathy described it as a 'kindergarten child': cheerful, error-prone, sometimes absurd, always revealing."

「@karpathy 的 nanochat 比你想象的更大。他称之为"斜坡"，但它实际上是一个独立的实验室——一个微型系统，任何人都可以在里面做实验... Karpathy 将其描述为"幼儿园孩子"： **快乐、容易犯错、有时荒谬、但总能揭示真相。** 」

![The Turing Post 解读](data:image/svg+xml,%3C%3Fxml version='1.0' encoding='UTF-8'%3F%3E%3Csvg width='1px' height='1px' viewBox='0 0 1 1' version='1.1' xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg stroke='none' stroke-width='1' fill='none' fill-rule='evenodd' fill-opacity='0'%3E%3Cg transform='translate(-249.000000, -126.000000)' fill='%23FFFFFF'%3E%3Crect x='249' y='126' width='1' height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

The Turing Post 解读

▲ The Turing Post：nanochat 是一个独立的实验室（812 赞）

## 行业专家的反应

量化专家 Tim Dettmers 评论：

> "Super cool! Very well executed! I think a lot of people will learn from it"

「太棒了！做得非常好！我觉得很多人都能从中受益。」

![Tim Dettmers 称赞](data:image/svg+xml,%3C%3Fxml version='1.0' encoding='UTF-8'%3F%3E%3Csvg width='1px' height='1px' viewBox='0 0 1 1' version='1.1' xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg stroke='none' stroke-width='1' fill='none' fill-rule='evenodd' fill-opacity='0'%3E%3Cg transform='translate(-249.000000, -126.000000)' fill='%23FFFFFF'%3E%3Crect x='249' y='126' width='1' height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

Tim Dettmers 称赞

▲ 量化专家 Tim Dettmers 称赞（143 赞）

《Transformers》作者 Sebastian Raschka 也在评论区提问架构细节，显示出对项目的高度关注。

![Sebastian Raschka 提问](data:image/svg+xml,%3C%3Fxml version='1.0' encoding='UTF-8'%3F%3E%3Csvg width='1px' height='1px' viewBox='0 0 1 1' version='1.1' xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg stroke='none' stroke-width='1' fill='none' fill-rule='evenodd' fill-opacity='0'%3E%3Cg transform='translate(-249.000000, -126.000000)' fill='%23FFFFFF'%3E%3Crect x='249' y='126' width='1' height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

Sebastian Raschka 提问

▲ Sebastian Raschka 提问架构细节（291 赞）

## 这意味着什么？

从 2020 年到 2026 年，Karpathy 用 8 个仓库证明了一件事：

**AI 研究的门槛，不是算力，不是论文，不是实验室，而是"你愿不愿意动手"。**

630 行代码 + 一块 GPU + 一个 Markdown 文件，就能跑完整研究循环。

更恐怖的是，连这 630 行代码都不需要你写——AI 自己会改。

你只需要写清楚"你想要什么"。

正如 Garry Tan 说的： **瓶颈不是算力，是你的 program.md。**

---

— END —

— END —

作者提示: 个人观点，仅供参考

继续滑动看下一个

桂宫说事

向上滑动看下一个