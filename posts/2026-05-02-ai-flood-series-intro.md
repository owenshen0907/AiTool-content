---
title: AI 简史：从“机器能不能思考”到每个人都能使用 AI
date: 2026-05-02
publishedAt: 2026-05-02T12:58:22+09:00
series: 普通人的 AI 编年史
tags: [AI, 写作, 学习, 科普, 思考]
excerpt: 这篇先用一条普通人能读懂的时间线，梳理人工智能从概念诞生、符号主义、专家系统、机器学习、深度学习，一路走到大模型和生成式 AI 的关键技术与关键人物。
draft: false
---

这两年，只要你打开任何一个信息流，基本都绕不开 AI。

有人说 ChatGPT 改变世界，有人说 Agent 会替你干活，有人说普通人再不学就来不及了。听多了以后，很容易有一种感觉：好像 AI 是突然从 2022 年某一天冒出来的，然后所有人都被卷进去了。

我一开始也有这种感觉。

但回头看，AI 不是突然出现的爆款产品，而是一条很长的河。上游有数学、哲学、计算机科学，也有几次过度乐观、几次跌入低谷；中间有一群人不断换方法、换工具、换问题；到了 ChatGPT 之后，这条河才突然冲到了普通人面前。

所以这篇不写成历史考试，也不写成论文综述。我更想像和朋友聊天一样，把这条线先讲清楚：AI 从哪里来，经历过哪些阶段，每个阶段到底在解决什么问题，又有哪些人把它往前推了一步。

如果你暂时不想记那么多人名和年份，也没关系。先抓住一句话：**AI 的历史，本质上是机器从“按人写的规则做事”，一步步走向“从数据中学习、连接工具、替人执行任务”的历史。**

:::note{title="先给一个总判断"}
AI 的历史不是一条“机器越来越像人”的直线，而是几条线不断交汇：人类怎样描述智能，机器怎样表示知识，算法怎样从数据里学习，算力怎样支撑规模，产品又怎样把能力带到普通人手里。
:::


<figure>
  <svg viewBox="0 0 1200 520" role="img" aria-label="AI 简史时间线：从机器能不能思考到 Agent 执行任务" style="width:100%;height:auto;border-radius:24px;border:1px solid #dbe5ef;background:linear-gradient(180deg,#f8fbff 0%,#ffffff 100%);box-shadow:0 18px 55px rgba(15,23,42,0.07);">
    <defs>
      <linearGradient id="aiRiver" x1="0" y1="0" x2="1" y2="0">
        <stop offset="0%" stop-color="#dbeafe" />
        <stop offset="38%" stop-color="#dcfce7" />
        <stop offset="70%" stop-color="#fef3c7" />
        <stop offset="100%" stop-color="#fee2e2" />
      </linearGradient>
      <filter id="softShadow" x="-20%" y="-20%" width="140%" height="140%">
        <feDropShadow dx="0" dy="14" stdDeviation="14" flood-color="#0f172a" flood-opacity="0.10" />
      </filter>
    </defs>
    <text x="70" y="70" fill="#0f172a" font-size="30" font-weight="800">AI 这条河：从科研问题流到普通人的工作台</text>
    <path d="M80 260 C210 150, 320 370, 450 250 S710 130, 830 245 S1030 370, 1120 235" fill="none" stroke="url(#aiRiver)" stroke-width="54" stroke-linecap="round" opacity="0.95" />
    <g filter="url(#softShadow)" font-family="system-ui, -apple-system, BlinkMacSystemFont, sans-serif">
      <g transform="translate(55 155)">
        <rect width="150" height="92" rx="22" fill="#ffffff" />
        <text x="20" y="34" fill="#0369a1" font-size="16" font-weight="800">1940s-1956</text>
        <text x="20" y="60" fill="#0f172a" font-size="18" font-weight="800">机器能否思考</text>
      </g>
      <g transform="translate(225 285)">
        <rect width="150" height="92" rx="22" fill="#ffffff" />
        <text x="20" y="34" fill="#047857" font-size="16" font-weight="800">1956-1970s</text>
        <text x="20" y="60" fill="#0f172a" font-size="18" font-weight="800">规则与推理</text>
      </g>
      <g transform="translate(395 145)">
        <rect width="150" height="92" rx="22" fill="#ffffff" />
        <text x="20" y="34" fill="#047857" font-size="16" font-weight="800">1970s-1980s</text>
        <text x="20" y="60" fill="#0f172a" font-size="18" font-weight="800">专家系统</text>
      </g>
      <g transform="translate(565 290)">
        <rect width="150" height="92" rx="22" fill="#ffffff" />
        <text x="20" y="34" fill="#92400e" font-size="16" font-weight="800">1980s-2012</text>
        <text x="20" y="60" fill="#0f172a" font-size="18" font-weight="800">机器学习</text>
      </g>
      <g transform="translate(735 130)">
        <rect width="150" height="92" rx="22" fill="#ffffff" />
        <text x="20" y="34" fill="#92400e" font-size="16" font-weight="800">2012-2022</text>
        <text x="20" y="60" fill="#0f172a" font-size="18" font-weight="800">深度学习</text>
      </g>
      <g transform="translate(905 300)">
        <rect width="150" height="92" rx="22" fill="#ffffff" />
        <text x="20" y="34" fill="#be123c" font-size="16" font-weight="800">2022 以后</text>
        <text x="20" y="60" fill="#0f172a" font-size="18" font-weight="800">GPT 时刻</text>
      </g>
      <g transform="translate(1000 120)">
        <rect width="150" height="92" rx="22" fill="#ffffff" />
        <text x="20" y="34" fill="#be123c" font-size="16" font-weight="800">现在</text>
        <text x="20" y="60" fill="#0f172a" font-size="18" font-weight="800">Agent 执行</text>
      </g>
    </g>
    <text x="72" y="465" fill="#64748b" font-size="18">不用先背术语，先看清这条主线：规则 → 数据 → 规模 → 工具 → 执行。</text>
  </svg>
  <figcaption>我理解的 AI 简史主线：它不是突然爆发，而是一条持续改道的河。</figcaption>
</figure>


## 0. 在 AI 有名字之前：人们先问了一个问题

人工智能这个词还没出现时，人类已经在问一个更基础的问题：**机器能不能思考？**

1943 年，沃伦·麦卡洛克和沃尔特·皮茨提出了一种用数学逻辑描述神经元的模型。它很粗糙，但重要的是，它让人第一次认真想象：人的神经活动也许可以被抽象成可计算的结构。

1949 年，唐纳德·赫布提出“共同激活的神经元会更容易连接在一起”的思想，后来很多人把它概括成一句话：一起发放的神经元连接在一起。这成为后来理解神经网络学习机制的一个早期启发。

1950 年，艾伦·图灵发表《Computing Machinery and Intelligence》。他没有陷入“机器到底有没有心灵”这种很难证明的问题，而是换了一个更工程化的问法：如果一台机器在对话里能让人分不清它和人类，那我们是否可以说它表现出了智能？

这就是后来常说的图灵测试。

图灵的重要性不只在于提出一个测试，更在于他把一个哲学问题改写成了一个可操作的问题：不要先争论机器有没有灵魂，先看它能不能表现出智能行为。

这一点对后来 AI 影响很大。因为从这里开始，智能不再只是玄学讨论，而开始变成可以被建模、被实现、被测试的工程问题。

## 1. 1956：人工智能正式有了名字

1956 年，达特茅斯会议通常被视为人工智能作为一个研究领域的起点。

这场会议的提案由约翰·麦卡锡、马文·明斯基、纳撒尼尔·罗切斯特和克劳德·香农等人发起。提案里使用了“Artificial Intelligence”这个说法，并且提出一个非常大胆的想法：学习、语言、抽象、问题求解等智能特征，原则上都可以被精确描述，然后让机器来模拟。

这个判断现在看起来仍然很激进。

当时的计算机很弱，存储很小，输入输出也很原始。但这群人相信：如果智能可以被分解成符号、规则和推理步骤，那么机器就有机会执行这些步骤。

所以早期 AI 的主线，很大程度上是“符号主义”。

所谓符号主义，可以简单理解成：人先把知识写成规则，机器再按照规则推理。

比如：

- 如果 A 成立，并且 A 推出 B，那么可以得到 B。
- 如果一个病人有某些症状，就可能对应某种疾病。
- 如果棋局出现某种形态，就优先搜索某些走法。

这个阶段的关键人物包括：

- 约翰·麦卡锡：提出 AI 这个名称，也发明了 Lisp 语言，影响了早期 AI 编程。
- 马文·明斯基：推动 AI、认知科学和神经网络早期研究，也长期影响 MIT AI 实验室。
- 艾伦·纽厄尔和赫伯特·西蒙：做出 Logic Theorist、General Problem Solver 等早期程序，试图让机器进行逻辑推理和问题求解。
- 克劳德·香农：信息论奠基人，也较早研究机器下棋问题。

这一阶段的 AI 有很强的理性主义气质：只要把知识和推理过程写清楚，机器就能变聪明。

## 2. 1960s-1970s：早期乐观撞上现实

早期 AI 很快做出了一些令人兴奋的演示。

机器能证明一些数学定理，能玩简单游戏，能在受限环境里和人对话。ELIZA 这样的聊天程序虽然很简单，但已经让很多人第一次感受到“机器好像能交流”。

同时，弗兰克·罗森布拉特提出的感知机也让神经网络路线获得过一次早期关注。感知机可以看成一种非常早期的学习机器：它不是完全靠人写规则，而是通过样本调整参数。

但问题很快出现了。

符号主义系统在小世界里表现不错，一旦进入真实世界就很吃力。现实语言有歧义，常识很难写成规则，环境变化太多，机器也缺少足够算力和数据。

神经网络路线也遇到限制。1969 年，明斯基和西摩尔·帕普特出版《Perceptrons》，指出单层感知机能力有限。虽然这本书后来经常被简化成“打击了神经网络”，但更准确地说，它暴露了当时方法、算力和训练技术的不足。

于是，第一次 AI 低谷逐渐出现。

这件事给后来的 AI 留下一个教训：**演示效果不等于真实能力，受限问题里的成功不等于开放世界里的成功。**

今天看很多 AI 产品时，这个教训仍然有用。

## 3. 1970s-1980s：专家系统把 AI 带进商业世界

AI 并没有因为早期受挫就消失。

到了 1970s 和 1980s，一个新的方向变得重要：专家系统。

专家系统的思路很直接：既然通用智能太难，那就先做特定领域里的专家。让人类专家把经验整理成规则库，机器根据规则进行判断和建议。

比如医学诊断、化学分析、计算机配置、企业流程决策。

这个阶段的代表人物之一是爱德华·费根鲍姆。他推动了知识工程和专家系统的发展。系统不一定“像人一样思考”，但只要在某个专业领域能给出有用建议，就有商业价值。

专家系统带来了一轮 AI 商业热潮。

但它的问题也很明显：规则维护成本太高。真实世界一变，规则就要更新；专家经验很多是模糊的，很难完整写成 if-then；系统越来越大之后，互相冲突的规则也越来越难管理。

所以 1980s 后期到 1990s 初，AI 又经历了一次低谷。

这次低谷说明：**只靠人工写规则，很难覆盖复杂世界。**

AI 需要从“人告诉机器规则”，走向“机器自己从数据里学规律”。

## 4. 1980s-2000s：机器学习接过主线

接下来，机器学习逐渐成为主线。

它的核心变化是：人不再试图把所有知识直接写进机器，而是给机器数据和目标，让它自己调整模型。

这个阶段有几条重要分支。

第一条是神经网络重新恢复生命力。

1986 年，大卫·鲁梅尔哈特、杰弗里·辛顿和罗纳德·威廉姆斯发表关于反向传播的论文。反向传播可以粗略理解成：模型做错了，就把错误一层层传回去，调整内部参数，让下次更接近正确答案。

这让多层神经网络的训练变得更实际。

第二条是统计学习。

支持向量机、决策树、随机森林、贝叶斯网络等方法开始广泛使用。弗拉基米尔·瓦普尼克推动了统计学习理论，朱迪亚·珀尔推动了概率图模型和因果推理。

这些方法不像早期符号 AI 那样强调“人类规则”，也不像今天的大模型那样庞大。它们更像一套实用工具箱：分类、预测、排序、识别模式。

第三条是计算机开始在特定任务上超过人类高手。

1997 年，IBM 的 Deep Blue 击败国际象棋世界冠军加里·卡斯帕罗夫。这个事件当时非常出圈，因为它让大众看到：机器在某些明确规则、可搜索的问题上，已经可以超过最强人类。

但 Deep Blue 也不是今天意义上的通用 AI。它更像是专门为国际象棋打造的超级系统，依赖搜索、评估函数、专用硬件和大量工程优化。

这一阶段的关键变化是：AI 从“写规则”转向“学规律”，但它还没有真正进入普通人的日常表达和创作。

## 5. 2000s-2012：数据、算力和深度学习终于碰到一起

深度学习不是 2012 年才出现的。神经网络这条线一直有人坚持，代表人物包括杰弗里·辛顿、杨立昆、约书亚·本吉奥等。

但长时间里，它缺少三个条件：足够多的数据、足够强的算力、足够有效的训练技巧。

2000 年后，互联网带来了大量数据，GPU 开始被用于通用计算，大规模数据集也逐渐出现。

其中一个关键节点是 ImageNet。

李飞飞等人推动构建 ImageNet 大规模图像数据集，让计算机视觉有了更标准、更大规模的训练和评测基础。

2012 年，Alex Krizhevsky、Ilya Sutskever 和 Geoffrey Hinton 用深度卷积神经网络 AlexNet 在 ImageNet 竞赛中取得突破性成绩。这件事通常被视为深度学习浪潮的关键引爆点。

为什么重要？

因为它证明了一个方向：当数据足够多、算力足够强、模型足够深时，神经网络可以直接从原始数据中学出很强的表示能力。

普通人可以这样理解：以前机器看图片，很多特征要人先设计；深度学习开始让机器自己从大量样本里学“什么是边缘、纹理、形状、物体”。

这一步把 AI 从手工规则，进一步推向了自动学习。

## 6. 2012-2017：AI 开始在看、听、下棋上连续突破

2012 之后，深度学习迅速扩散到计算机视觉、语音识别、机器翻译、推荐系统等领域。

杨立昆长期推动卷积神经网络在图像识别中的应用；辛顿团队推动深度学习在语音和视觉上的突破；本吉奥在表示学习、序列建模等方向影响很大。

这个阶段，AI 的能力越来越像“感知系统”：能看图、能听音、能识别模式。

2014 年，Ian Goodfellow 提出生成对抗网络 GAN。它让“机器生成图像”这件事变得更有想象空间。虽然 GAN 后来在很多场景被扩散模型超过，但它在生成式 AI 的历史里非常重要。

2016 年，DeepMind 的 AlphaGo 击败李世石。

这次和 Deep Blue 不一样。围棋的搜索空间巨大，不能只靠暴力搜索。AlphaGo 结合了深度神经网络、强化学习和树搜索，让机器在一个长期被认为很难攻克的领域取得突破。

Deep Blue 让人看到机器可以在规则明确的棋类里赢人；AlphaGo 让人感到更震撼：机器似乎开始形成超出人类直觉的策略。

这也是很多普通人第一次强烈感觉到：AI 不只是工具，它可能会产生新的“思路”。

## 7. 2017-2022：Transformer 把语言模型推到新阶段

2017 年，Google 团队发表《Attention Is All You Need》，提出 Transformer 架构。

这篇论文非常关键。

在此之前，处理语言这类序列数据，常见方法依赖循环神经网络等结构。Transformer 的核心变化，是用注意力机制让模型更好地处理序列中不同位置之间的关系，并且更适合大规模并行训练。

普通人不需要一开始理解全部数学细节，只要先抓住一个直觉：**Transformer 让模型在读一句话、一段话、一本书时，可以更有效地判断哪些部分彼此相关。**

这为后来的大语言模型铺平了道路。

随后，BERT、GPT、T5 等预训练语言模型不断出现。它们的共同思路是：先在大量文本上学习语言规律，再迁移到问答、翻译、总结、分类等任务上。

2020 年，OpenAI 发布 GPT-3。它让很多人第一次明显感到：只要模型足够大、数据足够多，语言模型不需要为每个任务重新训练，也能通过提示和少量示例完成很多事情。

这就是后来“prompt”变得重要的原因之一。

AI 开始从“一个专门模型做一个专门任务”，走向“一个大模型通过对话或提示处理很多任务”。

## 8. 2022 以后：GPT 时刻让 AI 走到普通人面前

2022 年底，ChatGPT 出圈。

它不是第一个大语言模型，也不是第一项 AI 技术突破，但它改变了 AI 和普通人的接触方式。

以前很多 AI 能力藏在搜索、推荐、识别、广告、风控、翻译系统背后，普通人不一定能直接感受到模型本身。

ChatGPT 把入口变成了聊天框。

这件事非常关键。因为聊天框降低了使用门槛：不用写代码，不用理解模型结构，不用先学一堆专业软件，只要会提问，就能开始使用。

这就是我理解的“GPT 时刻”：不是某一个模型突然代表全部未来，而是 AI 第一次以一个人人都能触摸的产品形态，正面站到了大众面前。

从这一刻开始，AI 的叙事从科研圈、工程圈，进入了普通人的工作和生活。

很多人第一次发现：

- 它能解释概念
- 它能写一封邮件
- 它能改一段文案
- 它能总结一篇文章
- 它能帮你写代码
- 它能陪你把一个想法拆成步骤

这不是“人工智能第一次有用”，而是“普通人第一次低成本感知到它有用”。

## 9. Scaling 共识和百模竞争

ChatGPT 出圈之后，还有一个变化很重要：**scaling 开始被行业广泛视为一条确定性很强的路线。**

所谓 scaling，不是简单说“模型越大越好”。更准确地说，是很多人开始相信：在一定范围内，更多算力、更大模型、更多数据、更好的训练方法，确实能持续换来能力提升。

这个判断不是 2022 年才出现。2020 年 OpenAI 的 scaling laws 研究已经把模型规模、数据规模、训练计算量和 loss 之间的关系讲得很清楚。GPT-3 也已经展示了大模型的 few-shot 能力。

但 ChatGPT 之后，这个判断从研究结论变成了商业共识。

于是出现了所谓“百模竞争”。

OpenAI、Anthropic、Google、Meta、xAI，以及国内的百度、阿里、字节、智谱、月之暗面、DeepSeek 等玩家，都开始围绕基础模型展开竞争。

这场竞争有几个维度：

- 谁的模型更强
- 谁的上下文更长
- 谁的推理能力更好
- 谁的成本更低
- 谁的速度更快
- 谁更适合代码、数学、多模态、企业场景
- 谁能把模型能力更稳定地包装成产品

这一阶段很像一次基础设施竞赛。

每家公司都在做自己的“发动机”。模型能力本身变成了核心资产，也变成了所有应用的底座。

但基础模型混战也暴露出一个问题：如果只比模型，普通用户很难长期感知差异。今天 A 模型领先一点，明天 B 模型追上来；今天榜单第一，过几周又被刷新。

所以 AI 很快进入下一阶段：模型不再只是回答问题，而要和传统软件、数据、工具、终端和工作流结合。


<figure>
  <svg viewBox="0 0 1200 560" role="img" aria-label="GPT 时刻之后，从基础模型竞争走向应用层连接" style="width:100%;height:auto;border-radius:24px;border:1px solid #e2e8f0;background:linear-gradient(135deg,#f8fafc 0%,#eef6ff 45%,#fff7ed 100%);box-shadow:0 18px 55px rgba(15,23,42,0.07);">
    <defs>
      <marker id="arrowHead" markerWidth="12" markerHeight="12" refX="10" refY="6" orient="auto">
        <path d="M0,0 L12,6 L0,12 z" fill="#64748b" />
      </marker>
    </defs>
    <text x="70" y="70" fill="#0f172a" font-size="30" font-weight="800">GPT 时刻之后：只比模型不够，模型要接入真实世界</text>
    <g font-family="system-ui, -apple-system, BlinkMacSystemFont, sans-serif">
      <rect x="80" y="150" width="250" height="190" rx="30" fill="#0f172a" />
      <text x="115" y="205" fill="#ffffff" font-size="26" font-weight="800">基础模型</text>
      <text x="115" y="245" fill="#cbd5e1" font-size="18">Scaling</text>
      <text x="115" y="278" fill="#cbd5e1" font-size="18">多模态</text>
      <text x="115" y="311" fill="#cbd5e1" font-size="18">推理 / 代码 / 长上下文</text>
      <path d="M350 245 H465" stroke="#64748b" stroke-width="4" marker-end="url(#arrowHead)" />
      <rect x="485" y="118" width="265" height="70" rx="22" fill="#ffffff" stroke="#bfdbfe" />
      <text x="515" y="162" fill="#0f172a" font-size="20" font-weight="800">RAG：接知识库</text>
      <rect x="485" y="210" width="265" height="70" rx="22" fill="#ffffff" stroke="#bbf7d0" />
      <text x="515" y="254" fill="#0f172a" font-size="20" font-weight="800">Tool call：调工具</text>
      <rect x="485" y="302" width="265" height="70" rx="22" fill="#ffffff" stroke="#fde68a" />
      <text x="515" y="346" fill="#0f172a" font-size="20" font-weight="800">MCP / CLI / Skill</text>
      <path d="M770 153 H890" stroke="#64748b" stroke-width="4" marker-end="url(#arrowHead)" />
      <path d="M770 245 H890" stroke="#64748b" stroke-width="4" marker-end="url(#arrowHead)" />
      <path d="M770 337 H890" stroke="#64748b" stroke-width="4" marker-end="url(#arrowHead)" />
      <rect x="910" y="150" width="220" height="190" rx="30" fill="#ffffff" stroke="#fecaca" />
      <text x="950" y="210" fill="#be123c" font-size="26" font-weight="900">Agent</text>
      <text x="950" y="252" fill="#475569" font-size="18">理解目标</text>
      <text x="950" y="285" fill="#475569" font-size="18">拆任务</text>
      <text x="950" y="318" fill="#475569" font-size="18">调用工具并执行</text>
      <text x="85" y="465" fill="#475569" font-size="19">这一步之后，AI 不只是“会回答”，而是开始能接知识、接工具、接终端、接流程。</text>
    </g>
  </svg>
  <figcaption>GPT 时刻之后的关键变化：基础模型继续竞争，但应用层开始围绕连接和执行展开。</figcaption>
</figure>


## 10. 从“会回答”到“会连接”：RAG、tool call、MCP、CLI、skill

大模型本身有几个天然限制。

它训练时学到的知识会过期；它不知道你公司的内部资料；它不能天然访问你的数据库、浏览器、文件系统和业务系统；它也不应该凭空编造事实。

所以 GPT 时刻之后，一个重要方向就是：**让大模型连接外部世界。**

这就出现了几类关键技术和工程模式。

### RAG：把外部知识接进来

RAG，全称 Retrieval-Augmented Generation，可以理解成“先检索，再生成”。

模型回答问题之前，先从文档库、知识库、网页、数据库里找相关内容，再基于这些内容生成答案。

这解决了两个问题：

1. 模型不用把所有知识都记在参数里。
2. 回答可以更贴近最新资料和私有资料。

对企业和个人知识库来说，RAG 很重要。因为很多有价值的信息并不在公开训练数据里，而在你自己的文档、项目记录、会议纪要、代码仓库和业务系统里。

### Tool calling：让模型调用工具

Tool calling，也可以叫 function calling，解决的是另一个问题：模型不能只说，它还要能调用外部能力。

比如：

- 查天气
- 查数据库
- 调接口
- 发邮件
- 创建日程
- 执行一段代码
- 调用支付、搜索、地图、CRM 等系统

模型负责理解用户意图、决定什么时候调用工具、生成参数；真正的执行交给外部系统。

这一步非常关键。因为它把 AI 从“会说话的模型”，推进到了“会操作系统能力的中间层”。

### MCP：让工具连接变得更标准

当工具越来越多，一个现实问题就出现了：每个模型、每个应用、每个工具都各接一套接口，会非常混乱。

MCP，也就是 Model Context Protocol，就是试图把模型和外部工具、数据源之间的连接标准化。

你可以把它粗略理解成：给 AI 应用接工具的一种通用插头。

如果这个方向成熟，模型就更容易连接文件、数据库、代码仓库、设计工具、浏览器、企业系统，而不是每个应用都重复造一遍集成。

### CLI 和开发环境：让模型进入真实工作台

对开发者来说，AI 进入 CLI 是另一个重要节点。

聊天窗口适合问问题，但真正开发时，很多动作发生在终端、代码仓库、测试命令、日志、构建脚本和部署流程里。

当 AI 能进入 CLI，它就不只是“给你建议”，而是可以：

- 读代码
- 改文件
- 跑测试
- 看报错
- 修 bug
- 生成提交
- 调整脚本
- 在长任务里持续执行

这也是为什么 Codex CLI、Claude Code 这类工具会重要。它们把模型从聊天框推进到真实开发环境。

### Skill：把经验封装成可复用能力

当 AI 只是每次重新对话，它的使用成本还是很高。

Skill 的意义在于：把一套稳定流程封装起来，让模型下次可以直接按流程做。

比如：

- 怎么生成一篇内容
- 怎么部署一个站点
- 怎么处理图片资产
- 怎么写一份周报
- 怎么审查一段代码
- 怎么把会议纪要变成任务

这类能力一旦封装成 skill，AI 就不只是“聪明”，而是开始“熟练”。

我自己现在越来越关心这一点：未来真正有用的 AI，不只是模型本身，而是模型加上工具、上下文、流程和长期记忆形成的系统。

## 11. Agent：AI 从助手变成执行者

当 RAG、tool calling、MCP、CLI、skill 这些东西组合起来，一个更大的方向就出现了：Agent。

Agent 和普通聊天机器人的差别，不是名字更酷，而是职责变了。

聊天机器人主要回答问题；Agent 需要围绕目标持续行动。

一个简单的 Agent 流程大概是：

1. 理解目标
2. 制定计划
3. 调用工具
4. 观察结果
5. 修正计划
6. 继续执行
7. 产出结果
8. 必要时请求人类确认

这就是从“问答”到“执行”的转变。

早期研究里，ReAct 把 reasoning 和 acting 放在一起讨论；Toolformer 让语言模型学习何时调用 API；Voyager 这类工作则展示了模型如何在环境里积累技能。这些研究和工程实践一起，把 Agent 的想象空间打开了。

到应用层，Manus 这类通用 AI agent 让普通人看到：AI 不只是给你一段答案，它可以帮你做市场调研、整理资料、写代码、生成报告、规划旅行，甚至在云端异步跑任务。

OpenManus、OpenClaw、Hermes Agent 这类开源或自托管 agent 项目，则代表了另一条线：把 agent 放到个人电脑、服务器、消息平台、终端和本地工具链里，让它更接近个人工作系统。

这些产品和项目不一定最后都留下来，名字也会变化。但它们共同说明一件事：AI 正在从“一个应用”变成“一个可以操作应用的层”。

这会带来生产效率的变化。

过去你要自己完成一整串动作：查资料、复制、整理、写初稿、做表格、改格式、发邮件、同步到项目管理工具。

现在更合理的方式可能变成：你定义目标和边界，Agent 拆任务、调用工具、执行中间步骤，你负责判断结果、修正方向、批准关键动作。

这不是完全自动化，也不是人被替代。

更准确地说，是工作分工变了：

- 人负责目标、判断、边界、审美和责任
- AI 负责搜索、生成、执行、整理、检查和重复劳动

这就是我理解的“生产效率爆炸”的来源。

不是因为 AI 每次回答都完美，而是因为大量原本卡在中间环节的操作，开始可以被模型和工具链接起来。


<figure>
  <svg viewBox="0 0 1200 560" role="img" aria-label="人和 Agent 的新分工：人负责目标判断，AI 负责执行整理" style="width:100%;height:auto;border-radius:24px;border:1px solid #e2e8f0;background:linear-gradient(180deg,#ffffff 0%,#f8fafc 100%);box-shadow:0 18px 55px rgba(15,23,42,0.07);">
    <defs>
      <marker id="flowArrow" markerWidth="12" markerHeight="12" refX="10" refY="6" orient="auto">
        <path d="M0,0 L12,6 L0,12 z" fill="#334155" />
      </marker>
    </defs>
    <text x="70" y="70" fill="#0f172a" font-size="30" font-weight="800">Agent 时代的分工：人不消失，人从重复操作里上移</text>
    <g font-family="system-ui, -apple-system, BlinkMacSystemFont, sans-serif">
      <rect x="80" y="130" width="300" height="310" rx="34" fill="#ecfeff" stroke="#a5f3fc" />
      <text x="120" y="190" fill="#155e75" font-size="28" font-weight="900">人负责</text>
      <text x="120" y="240" fill="#334155" font-size="20">目标</text>
      <text x="120" y="280" fill="#334155" font-size="20">边界</text>
      <text x="120" y="320" fill="#334155" font-size="20">判断</text>
      <text x="120" y="360" fill="#334155" font-size="20">审美</text>
      <text x="120" y="400" fill="#334155" font-size="20">最终责任</text>
      <path d="M410 285 H520" stroke="#334155" stroke-width="4" marker-end="url(#flowArrow)" />
      <rect x="535" y="190" width="130" height="190" rx="26" fill="#0f172a" />
      <text x="573" y="250" fill="#ffffff" font-size="24" font-weight="900">任务</text>
      <text x="565" y="292" fill="#cbd5e1" font-size="18">计划</text>
      <text x="565" y="325" fill="#cbd5e1" font-size="18">反馈</text>
      <path d="M680 285 H790" stroke="#334155" stroke-width="4" marker-end="url(#flowArrow)" />
      <rect x="820" y="130" width="300" height="310" rx="34" fill="#fff7ed" stroke="#fed7aa" />
      <text x="860" y="190" fill="#9a3412" font-size="28" font-weight="900">AI 负责</text>
      <text x="860" y="240" fill="#334155" font-size="20">搜索</text>
      <text x="860" y="280" fill="#334155" font-size="20">生成</text>
      <text x="860" y="320" fill="#334155" font-size="20">执行</text>
      <text x="860" y="360" fill="#334155" font-size="20">整理</text>
      <text x="860" y="400" fill="#334155" font-size="20">检查重复劳动</text>
    </g>
    <text x="82" y="500" fill="#64748b" font-size="18">重点不是“人被替代”，而是人把目标和判断说清楚，把中间大量机械步骤交给 Agent。</text>
  </svg>
  <figcaption>我更愿意把 Agent 看成新的协作分工，而不是一句简单的“AI 替代人”。</figcaption>
</figure>


## 12. 回头看：AI 每一阶段其实都在补一块短板

把这段历史压缩一下，大概可以这样看：

| 阶段 | 核心问题 | 代表路线 | 代表人物或产品 |
| --- | --- | --- | --- |
| 1940s-1956 | 机器能不能表现出智能 | 计算理论、早期神经模型 | 图灵、麦卡洛克、皮茨、赫布 |
| 1956-1970s | 能不能把智能写成规则 | 符号主义、逻辑推理 | 麦卡锡、明斯基、纽厄尔、西蒙 |
| 1970s-1980s | 能不能在专业领域解决问题 | 专家系统、知识工程 | 费根鲍姆、MYCIN、XCON |
| 1980s-2000s | 能不能从数据里学规律 | 机器学习、统计学习、反向传播 | 辛顿、鲁梅尔哈特、瓦普尼克、珀尔 |
| 2012 前后 | 能不能让模型自己学特征 | 深度学习、CNN、GPU、大数据集 | 李飞飞、Krizhevsky、Sutskever、Hinton |
| 2016 前后 | 能不能在复杂决策中超过人类 | 深度强化学习、搜索 | AlphaGo、David Silver、Demis Hassabis |
| 2017-2022 | 能不能用一个模型处理语言任务 | Transformer、大语言模型 | Vaswani 团队、BERT、GPT-3 |
| 2022-2023 | 能不能让普通人直接使用 AI | 对话产品、生成式 AI、多模态 | ChatGPT、Claude、Gemini、Midjourney 等 |
| 2023-2025 | 能不能把模型接入真实数据和工具 | RAG、tool calling、CLI、MCP、skill | LangChain、OpenAI function calling、MCP、Codex CLI、Claude Code 等 |
| 2025 以后 | 能不能围绕目标持续执行任务 | Agent、长任务、个人工作流、自托管执行环境 | Manus、OpenManus、OpenClaw、Hermes Agent 等 |

这条线说明一件事：AI 不是突然爆发的。

它每一次前进，都在补上一块过去缺失的东西：规则不够，就引入学习；数据不够，就建设数据集；算力不够，就利用 GPU；模型不够通用，就做预训练和大模型；入口太难，就做成聊天框和产品。

## 13. 普通人该怎样理解这段历史

对普通人来说，了解 AI 简史不是为了背年份和人名。

更重要的是建立几个判断。

### 第一，AI 经常高估短期，低估长期

AI 历史上不止一次出现热潮，也不止一次跌入低谷。

每一次热潮里，都会有人觉得通用智能马上来了；每一次低谷里，又会有人觉得这条路走不通。

但长期看，AI 确实一直在积累。算法、数据、硬件、工程、产品，每一层都在往前推。

所以面对今天的 AI 热潮，既不要盲目兴奋，也不要简单否定。

### 第二，真正改变普通人的，往往不是论文，而是产品入口

Transformer 很重要，但普通人真正感受到 AI，是因为 ChatGPT 这样的产品把能力变成了可使用的界面。

技术突破如果没有产品形态，影响会停留在专业圈；产品入口如果足够简单，就会把技术带到日常生活。

所以后面看 AI，不只要看模型，还要看它怎样进入真实场景。

### 第三，AI 的核心变化是从“人写规则”走向“机器学模式”

早期 AI 试图让人把知识写成规则。

今天的大模型则更像是从海量数据中学会语言、图像、代码和世界知识的统计模式，再通过提示和对话完成任务。

这不代表它真的像人一样理解世界，也不代表它永远可靠。但它确实改变了人和机器协作的方式。

### 第四，普通人的机会在工作流里

如果只把 AI 当成一个问答工具，很容易用几次就停。

更重要的是把它接进自己的流程：学习、写作、复盘、做产品、写代码、整理资料、生成素材、检查逻辑。

这也是我后面想继续写的方向：先理解历史，再回到今天，看看普通人怎样把 AI 放进真实生活。

## 结尾：先把河流看清楚，再决定怎么下水

如果你读到这里，已经不需要记住所有名字。

AI 简史不是一串冷冰冰的年份。

它更像是一条不断改道的河：有时靠逻辑规则推进，有时靠专家知识推进，有时靠统计学习推进，有时靠神经网络、数据、算力和大模型一起推进。

今天我们站在这条河边，看到的是最热闹的一段：聊天机器人、文生图、AI 视频、Agent、自动化工作流。

但如果不知道上游发生过什么，就很容易被当下的浪花吓到，或者被短期热点牵着走。

所以这个专栏的第一步，我想先把大线索搭起来。

后面再一篇一篇往下拆：图灵测试到底重要在哪，达特茅斯会议为什么给 AI 命名，专家系统为什么兴起又衰落，深度学习为什么爆发，Transformer 为什么成为今天大模型的底座，ChatGPT 又为什么真正让 AI 出圈。

先看清楚历史，再谈怎么使用。

这是普通人进入 AI 洪流时，比较稳的一种开始方式。

## 参考资料

- Alan Turing, [Computing Machinery and Intelligence](https://academic.oup.com/mind/article/LIX/236/433/986238)
- John McCarthy 等， [A Proposal for the Dartmouth Summer Research Project on Artificial Intelligence](https://www-formal.stanford.edu/jmc/history/dartmouth/dartmouth.html)
- David Rumelhart、Geoffrey Hinton、Ronald Williams， [Learning representations by back-propagating errors](https://www.nature.com/articles/323533a0)
- Alex Krizhevsky、Ilya Sutskever、Geoffrey Hinton， [ImageNet Classification with Deep Convolutional Neural Networks](https://papers.neurips.cc/paper/4824-imagenet-classification-with-deep-convolutional-neural-networks)
- David Silver 等， [Mastering the game of Go with deep neural networks and tree search](https://www.nature.com/articles/nature16961)
- Ashish Vaswani 等， [Attention Is All You Need](https://arxiv.org/abs/1706.03762)
- Tom Brown 等， [Language Models are Few-Shot Learners](https://arxiv.org/abs/2005.14165)
- Jared Kaplan 等， [Scaling Laws for Neural Language Models](https://openai.com/research/scaling-laws-for-neural-language-models)
- Patrick Lewis 等， [Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks](https://arxiv.org/abs/2005.11401)
- Shunyu Yao 等， [ReAct: Synergizing Reasoning and Acting in Language Models](https://arxiv.org/abs/2210.03629)
- Timo Schick 等， [Toolformer: Language Models Can Teach Themselves to Use Tools](https://arxiv.org/abs/2302.04761)
- Anthropic， [Model Context Protocol](https://www.anthropic.com/news/model-context-protocol)
- OpenAI， [Function calling / tool calling](https://platform.openai.com/docs/guides/function-calling)
