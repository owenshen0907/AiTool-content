---
title: 我为什么开始给自己做一个“自进化个人 Agent”
date: 2026-05-02
series: 产品日记
tags: [产品, AI, Agent, evomap-farmer, AiTool, system-design]
excerpt: 我真正缺的不是更强的模型，而是一条连续的个人工作链：上层由 Codex、Claude Code、openclaw 承接日常工作，下层由 EvoMap 里的 Evolver 负责 skill 迭代，中间再由我自己的工作系统把项目脉络、资源、经验和公开表达接起来。
draft: false
---

最近我逐渐确认，我的问题不在于还没找到最强的 Agent，而在于我的工作已经天然分层。

最上面，是我每天直接使用的工具层：Codex、Claude Code 和 openclaw。

再往下一层，才是 EvoMap。更准确地说，是 EvoMap 里的 Evolver。它不直接参与我当天的代码实现或信息查询，而是负责 skill 迭代、经验沉淀和能力外循环。

所以我面对的真实问题不是工具能力不足，而是：**日常工作层与能力演化层之间，还缺一条稳定、连续、可回溯的个人工作链。**

这个缺口带来的结果很直接。即使同一个项目一直在推进，我仍然需要反复补背景、补状态、补判断，最后把时间消耗在重新理解自己已经做过什么。

因此，我想做的并不是再找一个更强的 Agent，而是建立一套能把这些工具和底层演化能力接起来、并持续沉淀过程的个人工作系统。

## 先把结构分清：使用层在上，演化层在下

如果只看使用层，我每天主要在两类场景之间切换：

- 在电脑前：写代码、改页面、调接口、验证结果
- 不在电脑前：查资料、补信息、记录下一步、保留临时判断

但再往下拆，我必须把 EvoMap 单独拿出来看。

因为它不是一个和 Codex、Claude Code、openclaw 并排的日常工具。我更愿意把它定义为更底层的能力基础设施：通过 Evolver 判断哪些方法值得沉淀，哪些 skill 值得继续演化。

<figure>
  <svg viewBox="0 0 1200 760" role="img" aria-label="我现在的多层工作场景图" style="width:100%;height:auto;border-radius:24px;border:1px solid #e2e8f0;background:linear-gradient(180deg,#f8fbff 0%,#ffffff 100%);">
    <defs>
      <linearGradient id="sceneA" x1="0" y1="0" x2="1" y2="1">
        <stop offset="0%" stop-color="#dbeafe"></stop>
        <stop offset="100%" stop-color="#eff6ff"></stop>
      </linearGradient>
      <linearGradient id="sceneB" x1="0" y1="0" x2="1" y2="1">
        <stop offset="0%" stop-color="#dcfce7"></stop>
        <stop offset="100%" stop-color="#f0fdf4"></stop>
      </linearGradient>
      <linearGradient id="sceneC" x1="0" y1="0" x2="1" y2="1">
        <stop offset="0%" stop-color="#fef3c7"></stop>
        <stop offset="100%" stop-color="#fff7ed"></stop>
      </linearGradient>
      <marker id="sceneArrow" markerWidth="12" markerHeight="12" refX="10" refY="6" orient="auto">
        <path d="M0,0 L12,6 L0,12 z" fill="#64748b"></path>
      </marker>
    </defs>
    <text x="70" y="78" font-size="34" font-weight="700" fill="#0f172a">我现在面对的，不只是多工具，而是多层工作</text>
    <text x="70" y="116" font-size="18" fill="#475569">上面是我每天直接切换的使用层，下面还有一层专门负责能力迭代的底座。</text>
    <rect x="70" y="170" width="470" height="360" rx="28" fill="url(#sceneA)" stroke="#bfdbfe"></rect>
    <text x="108" y="218" font-size="18" font-weight="700" fill="#1d4ed8">场景 A / 我在电脑前</text>
    <text x="108" y="265" font-size="34" font-weight="700" fill="#0f172a">开发执行</text>
    <text x="108" y="305" font-size="18" fill="#334155">重点是把事情真的做出来。</text>
    <rect x="108" y="345" width="180" height="140" rx="24" fill="#ffffff" stroke="#bfdbfe"></rect>
    <text x="132" y="385" font-size="16" font-weight="700" fill="#0f172a">Codex</text>
    <text x="132" y="418" font-size="14" fill="#475569">综合能力强</text>
    <text x="132" y="442" font-size="14" fill="#475569">代码 / 图像 / 执行面广</text>
    <rect x="322" y="345" width="180" height="140" rx="24" fill="#ffffff" stroke="#bfdbfe"></rect>
    <text x="346" y="385" font-size="16" font-weight="700" fill="#0f172a">Claude Code</text>
    <text x="346" y="418" font-size="14" fill="#475569">代码攻坚更强</text>
    <text x="346" y="442" font-size="14" fill="#475569">更适合复杂问题</text>
    <text x="108" y="498" font-size="15" fill="#475569">这一侧的核心是：实现、调试、验证、重构。</text>
    <rect x="660" y="170" width="470" height="360" rx="28" fill="url(#sceneB)" stroke="#bbf7d0"></rect>
    <text x="698" y="218" font-size="18" font-weight="700" fill="#15803d">场景 B / 我不在电脑前</text>
    <text x="698" y="265" font-size="34" font-weight="700" fill="#0f172a">查询与记录</text>
    <text x="698" y="305" font-size="18" fill="#334155">重点是别让线索散掉。</text>
    <rect x="748" y="345" width="310" height="140" rx="24" fill="#ffffff" stroke="#bbf7d0"></rect>
    <text x="726" y="385" font-size="16" font-weight="700" fill="#0f172a">openclaw</text>
    <text x="726" y="418" font-size="14" fill="#475569">平时不参与主编程链路</text>
    <text x="726" y="442" font-size="14" fill="#475569">更像离身助手：查、记、留线索</text>
    <text x="698" y="498" font-size="15" fill="#475569">这一侧的核心是：补信息、留判断、别把线索弄丢。</text>
    <line x1="540" y1="370" x2="660" y2="370" stroke="#64748b" stroke-width="4" marker-end="url(#sceneArrow)"></line>
    <line x1="660" y1="430" x2="540" y2="430" stroke="#94a3b8" stroke-width="4" marker-end="url(#sceneArrow)"></line>
    <text x="562" y="348" font-size="14" fill="#475569">同一个项目</text>
    <text x="553" y="458" font-size="14" fill="#475569">同一条脉络</text>
    <rect x="160" y="560" width="880" height="82" rx="28" fill="#eef2ff" stroke="#c7d2fe"></rect>
    <text x="202" y="602" font-size="18" font-weight="700" fill="#3730a3">更下一层 / EvoMap 里的 Evolver</text>
    <text x="202" y="630" font-size="15" fill="#475569">这一层不直接替我干活，而是负责 skill 迭代、经验沉淀和能力外循环。</text>
    <rect x="250" y="680" width="700" height="54" rx="27" fill="url(#sceneC)" stroke="#fed7aa"></rect>
    <text x="284" y="715" font-size="16" font-weight="700" fill="#9a3412">我真正缺的，不是再多一个工具，而是把这几层稳定接起来。</text>
  </svg>
  <figcaption>我现在的问题不是工具太少，而是使用层和能力演化层之间，还没有一条真正顺手的连接线。</figcaption>
</figure>

如果把这个问题压缩成一句话：

> **我缺的不是更强的模型能力，而是连续的个人工作链。**

## 核心问题不是能力不足，而是工作链会断

只要跨工具、跨场景、跨时间推进，断点就会出现：

- Codex 里的实现判断，不会自然进入下一次讨论
- Claude Code 里的攻坚思路，跨天之后往往只剩结论
- openclaw 记录下来的查询结果，未必能回流到项目主线
- skill 在变化，但有效方法缺少稳定的迭代机制
- 服务器、账号、路径、部署方式这类资源信息，会持续被使用，却长期散落在各处

这些都不是执行问题，而是连续性问题。

<figure>
  <svg viewBox="0 0 1200 680" role="img" aria-label="为什么工作会断的原因图" style="width:100%;height:auto;border-radius:24px;border:1px solid #e2e8f0;background:#ffffff;">
    <defs>
      <marker id="breakArrow" markerWidth="12" markerHeight="12" refX="10" refY="6" orient="auto">
        <path d="M0,0 L12,6 L0,12 z" fill="#64748b"></path>
      </marker>
    </defs>
    <text x="70" y="80" font-size="34" font-weight="700" fill="#0f172a">同一个项目为什么会越做越容易失忆</text>
    <text x="70" y="118" font-size="18" fill="#475569">问题不是没有记录，而是这些记录没有被组织成一条连续的项目线。</text>
    <rect x="430" y="180" width="340" height="90" rx="24" fill="#eff6ff" stroke="#bfdbfe"></rect>
    <text x="470" y="234" font-size="22" font-weight="700" fill="#0f172a">同一个项目，在多个 Agent 和场景里推进</text>
    <rect x="110" y="340" width="220" height="90" rx="24" fill="#ffffff" stroke="#e2e8f0"></rect>
    <text x="144" y="392" font-size="18" font-weight="700" fill="#0f172a">代码上下文断</text>
    <rect x="370" y="340" width="220" height="90" rx="24" fill="#ffffff" stroke="#e2e8f0"></rect>
    <text x="404" y="392" font-size="18" font-weight="700" fill="#0f172a">项目状态断</text>
    <rect x="630" y="340" width="220" height="90" rx="24" fill="#ffffff" stroke="#e2e8f0"></rect>
    <text x="668" y="392" font-size="18" font-weight="700" fill="#0f172a">skill 演化断</text>
    <rect x="890" y="340" width="220" height="90" rx="24" fill="#ffffff" stroke="#e2e8f0"></rect>
    <text x="922" y="392" font-size="18" font-weight="700" fill="#0f172a">资源信息断</text>
    <line x1="520" y1="270" x2="220" y2="338" stroke="#94a3b8" stroke-width="3" marker-end="url(#breakArrow)"></line>
    <line x1="560" y1="270" x2="480" y2="338" stroke="#94a3b8" stroke-width="3" marker-end="url(#breakArrow)"></line>
    <line x1="640" y1="270" x2="740" y2="338" stroke="#94a3b8" stroke-width="3" marker-end="url(#breakArrow)"></line>
    <line x1="680" y1="270" x2="1000" y2="338" stroke="#94a3b8" stroke-width="3" marker-end="url(#breakArrow)"></line>
    <rect x="300" y="510" width="600" height="92" rx="28" fill="#fef2f2" stroke="#fecaca"></rect>
    <text x="344" y="560" font-size="24" font-weight="700" fill="#991b1b">结果不是没做事，而是每隔一段时间就要重新理解自己。</text>
  </svg>
  <figcaption>我现在最不想承受的成本，已经不是写代码本身，而是不断重新找回项目上下文。</figcaption>
</figure>

## 把问题拆开后，只剩四类

我后来不再问“要不要做一个大系统”，而是先问：反复出现的问题到底是什么。

拆开之后，我看到的其实只有四类：

1. **多 Agent 协同问题**：同一个项目在多个工具之间推进，如何保持连续
2. **持续记忆问题**：状态、判断、阻塞和下一步，如何在回看时仍然清晰
3. **skill 迭代问题**：哪些 workflow 真正有效，如何通过更下一层的 Evolver 累积下来
4. **对外表达问题**：哪些内部过程值得被提炼为公开内容

<figure>
  <svg viewBox="0 0 1200 640" role="img" aria-label="第一性原理拆解图" style="width:100%;height:auto;border-radius:24px;border:1px solid #e2e8f0;background:linear-gradient(180deg,#ffffff 0%,#f8fafc 100%);">
    <defs>
      <marker id="firstArrow" markerWidth="12" markerHeight="12" refX="10" refY="6" orient="auto">
        <path d="M0,0 L12,6 L0,12 z" fill="#64748b"></path>
      </marker>
    </defs>
    <text x="70" y="78" font-size="34" font-weight="700" fill="#0f172a">如果不从“做个大系统”开始，而是从问题本身开始</text>
    <text x="70" y="116" font-size="18" fill="#475569">事情反而没有那么抽象。每一类问题，都有它更自然的承接层。</text>
    <rect x="110" y="180" width="220" height="110" rx="28" fill="#eff6ff" stroke="#bfdbfe"></rect>
    <text x="144" y="228" font-size="18" font-weight="700" fill="#1d4ed8">多 Agent 协同</text>
    <text x="144" y="258" font-size="15" fill="#334155">同一个项目在不同工具之间接不上</text>
    <rect x="380" y="180" width="220" height="110" rx="28" fill="#eff6ff" stroke="#bfdbfe"></rect>
    <text x="414" y="228" font-size="18" font-weight="700" fill="#1d4ed8">持续记忆</text>
    <text x="414" y="258" font-size="15" fill="#334155">状态、判断、下一步没被稳定组织</text>
    <rect x="650" y="180" width="220" height="110" rx="28" fill="#eff6ff" stroke="#bfdbfe"></rect>
    <text x="684" y="228" font-size="18" font-weight="700" fill="#1d4ed8">skill 演化</text>
    <text x="684" y="258" font-size="15" fill="#334155">有效 workflow 没有进入长期循环</text>
    <rect x="920" y="180" width="220" height="110" rx="28" fill="#eff6ff" stroke="#bfdbfe"></rect>
    <text x="954" y="228" font-size="18" font-weight="700" fill="#1d4ed8">对外表达</text>
    <text x="954" y="258" font-size="15" fill="#334155">值得说出去的内容没有出口</text>
    <line x1="220" y1="290" x2="220" y2="380" stroke="#94a3b8" stroke-width="4" marker-end="url(#firstArrow)"></line>
    <line x1="490" y1="290" x2="490" y2="380" stroke="#94a3b8" stroke-width="4" marker-end="url(#firstArrow)"></line>
    <line x1="760" y1="290" x2="760" y2="380" stroke="#94a3b8" stroke-width="4" marker-end="url(#firstArrow)"></line>
    <line x1="1030" y1="290" x2="1030" y2="380" stroke="#94a3b8" stroke-width="4" marker-end="url(#firstArrow)"></line>
    <rect x="110" y="400" width="220" height="100" rx="24" fill="#f0fdf4" stroke="#bbf7d0"></rect>
    <text x="144" y="446" font-size="18" font-weight="700" fill="#15803d">衔接层</text>
    <text x="144" y="474" font-size="15" fill="#334155">把多个工具的线索接起来</text>
    <rect x="380" y="400" width="220" height="100" rx="24" fill="#f0fdf4" stroke="#bbf7d0"></rect>
    <text x="414" y="446" font-size="18" font-weight="700" fill="#15803d">项目脉络层</text>
    <text x="414" y="474" font-size="15" fill="#334155">保留阶段判断，而不只是任务名</text>
    <rect x="650" y="400" width="220" height="100" rx="24" fill="#f0fdf4" stroke="#bbf7d0"></rect>
    <text x="684" y="446" font-size="18" font-weight="700" fill="#15803d">进化层</text>
    <text x="684" y="474" font-size="15" fill="#334155">让 skill 和经验慢慢长回来</text>
    <rect x="920" y="400" width="220" height="100" rx="24" fill="#f0fdf4" stroke="#bbf7d0"></rect>
    <text x="954" y="446" font-size="18" font-weight="700" fill="#15803d">公开内容层</text>
    <text x="954" y="474" font-size="15" fill="#334155">把值得公开的部分变成产品日记</text>
    <rect x="300" y="548" width="600" height="54" rx="27" fill="#fff7ed" stroke="#fed7aa"></rect>
    <text x="338" y="582" font-size="16" font-weight="700" fill="#9a3412">所谓“自进化个人 Agent”，不是一个大而全工具，而是把这几层逐步接顺。</text>
  </svg>
  <figcaption>我后来决定不再先想“做一个什么产品”，而是先把问题拆到能落地的最小层面。</figcaption>
</figure>

## 所以，我不想再做一个传统项目管理工具

我不想再回到这条熟悉但低效的路径：

- 再开一套任务系统
- 再建一套卡片结构
- 再手工维护状态
- 再把真实发生过的过程翻译成另一套表述

这套方法并非无效，只是不适合我当前的工作形态。

我的判断是：**工作应该先真实发生，项目脉络应该从真实工作里自然长出；skill 应该先在底层持续迭代，再决定哪些结果值得进入公开层。**

如果要给这套系统一个清晰定义，我更愿意把它看成五层：

1. Codex / Claude Code / openclaw：我每天直接切换的日常工具层
2. EvoMap / Evolver：负责 skill 迭代和经验沉淀的能力进化底层
3. evomap-farmer：连接使用层与演化层的私有工作组织层
4. AiTool-content：面向公开表达的内容草稿层
5. AiTool：最终面向外部的公开呈现层

<figure>
  <svg viewBox="0 0 1200 860" role="img" aria-label="自进化个人 Agent 的五层结构图" style="width:100%;height:auto;border-radius:24px;border:1px solid #e2e8f0;background:#ffffff;">
    <defs>
      <marker id="layerArrow" markerWidth="12" markerHeight="12" refX="10" refY="6" orient="auto">
        <path d="M0,0 L12,6 L0,12 z" fill="#64748b"></path>
      </marker>
    </defs>
    <text x="70" y="78" font-size="34" font-weight="700" fill="#0f172a">我想做的，不是一个工具，而是一条从日常工作到底层进化、再到公开表达的链路</text>
    <text x="70" y="116" font-size="18" fill="#475569">最上面是我每天在用的工具，最下面才是能力演化；中间还得有一层真正属于我自己的工作组织。</text>
    <rect x="160" y="170" width="880" height="88" rx="28" fill="#eff6ff" stroke="#bfdbfe"></rect>
    <text x="210" y="210" font-size="18" font-weight="700" fill="#1d4ed8">第一层：日常工具层</text>
    <text x="210" y="238" font-size="16" fill="#334155">Codex / Claude Code / openclaw —— 这是我每天直接切换、直接干活的一层</text>
    <line x1="600" y1="258" x2="600" y2="322" stroke="#94a3b8" stroke-width="4" marker-end="url(#layerArrow)"></line>
    <rect x="160" y="330" width="880" height="102" rx="28" fill="#eef2ff" stroke="#c7d2fe"></rect>
    <text x="210" y="372" font-size="18" font-weight="700" fill="#3730a3">第二层：能力进化底层（EvoMap / Evolver）</text>
    <text x="210" y="404" font-size="16" fill="#334155">这一层不直接替我完成任务，而是负责 skill 迭代、经验沉淀和能力外循环</text>
    <line x1="600" y1="432" x2="600" y2="486" stroke="#94a3b8" stroke-width="4" marker-end="url(#layerArrow)"></line>
    <rect x="160" y="494" width="880" height="102" rx="28" fill="#f0fdf4" stroke="#bbf7d0"></rect>
    <text x="210" y="536" font-size="18" font-weight="700" fill="#15803d">第三层：私有工作层（evomap-farmer）</text>
    <text x="210" y="568" font-size="16" fill="#334155">把上面工具产生的线索，和下面 Evolver 积累的经验，组织成我自己的项目脉络</text>
    <line x1="600" y1="596" x2="600" y2="648" stroke="#94a3b8" stroke-width="4" marker-end="url(#layerArrow)"></line>
    <rect x="160" y="656" width="880" height="90" rx="28" fill="#fff7ed" stroke="#fed7aa"></rect>
    <text x="210" y="698" font-size="18" font-weight="700" fill="#c2410c">第四层：公开内容草稿层（AiTool-content）</text>
    <text x="210" y="726" font-size="16" fill="#334155">不是所有工作都公开，只把值得说清楚的阶段判断提炼成产品日记或公开记录</text>
    <line x1="600" y1="746" x2="600" y2="780" stroke="#94a3b8" stroke-width="4" marker-end="url(#layerArrow)"></line>
    <rect x="160" y="790" width="880" height="50" rx="26" fill="#f8fafc" stroke="#e2e8f0"></rect>
    <text x="210" y="822" font-size="16" font-weight="700" fill="#0f172a">第五层：公开呈现层（AiTool /notes）—— 让别人看懂，也让我以后能回来看懂</text>
  </svg>
  <figcaption>我现在更愿意把这件事看成一条五层链路：工具在上，Evolver 在下，中间必须有一层属于我自己的工作组织。</figcaption>
</figure>

## 产品日记不是附属产物，而是系统的一部分

如果这套系统只解决本地连续性，它最多只是一个更好用的个人工作台。

我真正想做的，是把内部过程逐步提炼成公开表达，再让这些表达反过来约束下一轮工作。

所以，产品日记不是收尾动作，而是这条链里的反馈层：

- 它逼我把阶段判断说清楚，而不是停留在“我大概知道”
- 它把一轮工作的路径、结果和未决问题压缩成可回看的记录
- 它会暴露论证里仍然含混的部分，逼我回到系统里继续修正
- 它也会成为下一轮产品决策和 skill 迭代的输入

<figure>
  <svg viewBox="0 0 1200 720" role="img" aria-label="产品日记作为迭代记录页的示意图" style="width:100%;height:auto;border-radius:24px;border:1px solid #dbe2ea;background:linear-gradient(180deg,#fbfdff 0%,#f8fafc 100%);">
    <defs>
      <marker id="loopArrow" markerWidth="12" markerHeight="12" refX="10" refY="6" orient="auto">
        <path d="M0,0 L12,6 L0,12 z" fill="#64748b"></path>
      </marker>
      <linearGradient id="notePaper" x1="0" y1="0" x2="0" y2="1">
        <stop offset="0%" stop-color="#ffffff"></stop>
        <stop offset="100%" stop-color="#f8fafc"></stop>
      </linearGradient>
    </defs>
    <rect x="50" y="46" width="1100" height="628" rx="28" fill="url(#notePaper)" stroke="#dbe2ea"></rect>
    <text x="84" y="92" font-size="34" font-weight="700" fill="#0f172a">我更希望产品日记像一张“迭代记录页”</text>
    <text x="84" y="128" font-size="18" fill="#475569">它不是把工作重新包装一遍，而是把本轮工作压缩成下一轮可以继续使用的判断。</text>
    <rect x="88" y="188" width="286" height="184" rx="26" fill="#ffffff" stroke="#e2e8f0"></rect>
    <text x="122" y="234" font-size="20" font-weight="700" fill="#0f172a">本轮工作</text>
    <text x="122" y="270" font-size="15" fill="#334155">实现、调试、查询、验证</text>
    <text x="122" y="300" font-size="15" fill="#334155">大量细节都发生在这里</text>
    <text x="122" y="330" font-size="15" fill="#334155">但如果不整理，很快就会散掉</text>
    <rect x="452" y="166" width="312" height="206" rx="26" fill="#eff6ff" stroke="#bfdbfe"></rect>
    <text x="488" y="214" font-size="20" font-weight="700" fill="#1d4ed8">阶段判断</text>
    <text x="488" y="252" font-size="15" fill="#334155">问题到底是什么</text>
    <text x="488" y="282" font-size="15" fill="#334155">哪些路径有效</text>
    <text x="488" y="312" font-size="15" fill="#334155">哪些假设需要继续验证</text>
    <text x="488" y="342" font-size="15" fill="#334155">哪些事情现在明确不做</text>
    <rect x="838" y="194" width="268" height="178" rx="26" fill="#f0fdf4" stroke="#bbf7d0"></rect>
    <text x="872" y="242" font-size="20" font-weight="700" fill="#15803d">下一轮输入</text>
    <text x="872" y="278" font-size="15" fill="#334155">继续做什么</text>
    <text x="872" y="308" font-size="15" fill="#334155">补什么证据</text>
    <text x="872" y="338" font-size="15" fill="#334155">结构该怎么改</text>
    <rect x="306" y="430" width="592" height="162" rx="28" fill="#fff7ed" stroke="#fed7aa"></rect>
    <text x="344" y="478" font-size="22" font-weight="700" fill="#c2410c">产品日记</text>
    <text x="344" y="514" font-size="16" fill="#334155">把路径、结果、未决问题整理成公开记录。</text>
    <text x="344" y="544" font-size="16" fill="#334155">它的作用不是“发出去”就结束，而是暴露论证空白，并把有效判断送回系统。</text>
    <line x1="374" y1="280" x2="452" y2="266" stroke="#64748b" stroke-width="4" marker-end="url(#loopArrow)"></line>
    <line x1="764" y1="266" x2="838" y2="282" stroke="#64748b" stroke-width="4" marker-end="url(#loopArrow)"></line>
    <line x1="968" y1="372" x2="790" y2="430" stroke="#94a3b8" stroke-width="4" marker-end="url(#loopArrow)"></line>
    <line x1="420" y1="430" x2="248" y2="372" stroke="#94a3b8" stroke-width="4" marker-end="url(#loopArrow)"></line>
    <text x="90" y="636" font-size="15" fill="#64748b">发布不是终点，反馈才是价值。</text>
  </svg>
  <figcaption>产品日记的价值，不在于“发出去”，而在于把一次工作压缩成下一轮可继续使用的判断。</figcaption>
</figure>

## 回到 evomap-farmer：它应该承担的是组织层

现阶段的 evomap-farmer 已经具备可用性，但它更接近一个把多类能力摆在一起的工作台，还不是一套围绕工作对象收束过的信息架构。

现在左侧大致是这些栏目：

- 统一工作台
- Credit 总览
- 执行草稿箱
- 进化链路
- 悬赏任务
- 学习资产
- 服务市场
- 官方底层
- 账本

问题不在于这些栏目是否成立，而在于它们更多按实现来源和系统能力展开，还没有完全转成“我到底围绕什么对象持续工作”。

我当前的判断如下：

| 当前模块 | 现在的价值 | 主要问题 | 更合适的位置 |
| --- | --- | --- | --- |
| 统一工作台 | 已经把主要信息放到一页，方向正确 | 仍然偏结果混排，不够对象化 | 保留为默认首页 |
| Credit 总览 | 方便看节点和积分 | 对个人 Agent 主线来说过重 | 收成系统状态区 |
| 执行草稿箱 | 适合承接 adapter pipeline | 名称偏技术，不够自然 | 并入“发布 / 执行中心” |
| 进化链路 | 适合查看证据和 skill 演化 | 目前更像后台控制台 | 保留，但明确为“技能进化” |
| 学习资产 / 服务市场 / 官方底层 | 跟 EvoMap 生态强相关 | 更像系统功能，不像工作对象 | 下沉为二级导航 |
| 账本 | 对审计和消费有价值 | 不该成为主入口之一 | 收进系统层或折叠层 |

如果只从后续演进看，我希望它最终不是围绕“页面名”扩张，而是围绕**对象**扩张。

## 下一步先定义信息架构，而不是继续扩功能

我现在的判断很明确：优先级最高的不是技术拆分，而是先定义我每天究竟围绕哪些对象工作。

### 第一层：导航应该围绕工作对象，而不是功能来源

我希望后续左侧目录逐步收成下面这个顺序：

1. 工作台
2. 今日收件箱
3. 项目脉络
4. 资源库
5. 技能进化
6. 对外发布
7. 执行中心
8. 系统账本

这八项分别对应：

- 工作台：负责总览和例外，不承载全部细节
- 今日收件箱：承接当天新增线索、待确认项和上下文提示
- 项目脉络：承接跨天推进的主题、阶段判断和下一步
- 资源库：承接服务器、工具、路径、外部资料等可复用信息
- 技能进化：承接 skill、workflow 和经验复盘
- 对外发布：承接产品日记、公开稿和草稿出口
- 执行中心：承接悬赏、Runner 和执行链路
- 系统账本：承接节点、积分和执行审计

这套结构对应的是我的工作对象，而不是系统功能列表。

<figure>
  <svg viewBox="0 0 1200 760" role="img" aria-label="围绕工作对象组织导航的信息架构草稿" style="width:100%;height:auto;border-radius:24px;border:1px solid #dbe2ea;background:linear-gradient(180deg,#fcfcfd 0%,#f8fafc 100%);">
    <rect x="44" y="42" width="1112" height="676" rx="28" fill="#ffffff" stroke="#dbe2ea"></rect>
    <text x="80" y="90" font-size="32" font-weight="700" fill="#0f172a">信息架构草稿：先按对象组织，再按系统能力补齐</text>
    <text x="80" y="126" font-size="18" fill="#475569">我不想先画“系统有什么”，而是先画“我每天到底在处理什么”。</text>
    <rect x="82" y="168" width="248" height="504" rx="24" fill="#f8fafc" stroke="#e2e8f0"></rect>
    <text x="114" y="214" font-size="20" font-weight="700" fill="#0f172a">导航顺序 v0.1</text>
    <rect x="106" y="238" width="198" height="44" rx="14" fill="#dbeafe"></rect>
    <text x="130" y="267" font-size="16" font-weight="700" fill="#1d4ed8">工作台</text>
    <text x="114" y="316" font-size="15" fill="#334155">今日收件箱</text>
    <text x="114" y="352" font-size="15" fill="#334155">项目脉络</text>
    <text x="114" y="388" font-size="15" fill="#334155">资源库</text>
    <text x="114" y="424" font-size="15" fill="#334155">技能进化</text>
    <text x="114" y="460" font-size="15" fill="#334155">对外发布</text>
    <text x="114" y="496" font-size="15" fill="#334155">执行中心</text>
    <text x="114" y="532" font-size="15" fill="#334155">系统账本</text>
    <text x="114" y="594" font-size="14" fill="#64748b">上半区先放工作对象</text>
    <text x="114" y="618" font-size="14" fill="#64748b">系统能力退到更后面</text>
    <rect x="370" y="174" width="334" height="178" rx="24" fill="#eff6ff" stroke="#bfdbfe"></rect>
    <text x="404" y="220" font-size="20" font-weight="700" fill="#1d4ed8">今日收件箱</text>
    <text x="404" y="254" font-size="15" fill="#334155">当天新增线索、待确认项、上下文提示</text>
    <text x="404" y="286" font-size="15" fill="#334155">先判断要不要处理，不急着转成待办</text>
    <rect x="744" y="174" width="334" height="178" rx="24" fill="#f0fdf4" stroke="#bbf7d0"></rect>
    <text x="778" y="220" font-size="20" font-weight="700" fill="#15803d">项目脉络</text>
    <text x="778" y="254" font-size="15" fill="#334155">主题、阶段判断、关键阻塞、下一条 prompt</text>
    <text x="778" y="286" font-size="15" fill="#334155">它负责跨天连续，不负责模拟任务板</text>
    <rect x="370" y="392" width="334" height="178" rx="24" fill="#fff7ed" stroke="#fed7aa"></rect>
    <text x="404" y="438" font-size="20" font-weight="700" fill="#c2410c">资源库</text>
    <text x="404" y="472" font-size="15" fill="#334155">服务器、工具、路径、资料、账号引用</text>
    <text x="404" y="504" font-size="15" fill="#334155">它承接会被反复调用的信息</text>
    <rect x="744" y="392" width="334" height="178" rx="24" fill="#fef2f2" stroke="#fecaca"></rect>
    <text x="778" y="438" font-size="20" font-weight="700" fill="#991b1b">技能进化 / 对外发布</text>
    <text x="778" y="472" font-size="15" fill="#334155">一个承接内部复盘，一个承接公开表达</text>
    <text x="778" y="504" font-size="15" fill="#334155">它们都来自工作对象，而不是独立悬空</text>
    <rect x="370" y="608" width="708" height="58" rx="20" fill="#f8fafc" stroke="#e2e8f0"></rect>
    <text x="404" y="644" font-size="16" font-weight="700" fill="#334155">不是减少功能，而是先让对象站稳，再决定系统能力放在哪里。</text>
  </svg>
  <figcaption>这张草图更接近我想要的方向：先让工作对象站住，再决定系统能力放在哪里。</figcaption>
</figure>

### 第二层：先立住工作对象，再决定技术模块

如果这套系统继续扩展，我有几个非常明确的原则：

- 不先问还能增加什么功能，而先问我每天到底在处理什么
- 不把一切都压成任务，因为很多内容本质上只是线索、证据、判断和资源
- 不为了管理而管理，而是让真实工作自然沉淀为可回看的脉络
- 不轻易删除过程，因为旧判断本身就是以后理解自己的依据

因此，在我心里，这套系统最核心的对象更接近下面这些：

- 工作证据：这一天真实发生过什么
- 今日线索：哪些值得继续跟进，哪些只需要暂时保留
- 项目脉络：一个主题当前走到哪里，下一步应该朝哪里推进
- 资源引用：服务器、工具、账号、资料这类会被反复调用的信息
- 技能经验：哪些方法真正有效，哪些只是偶然成功
- 公开草稿：哪些内部过程值得整理成对外可读的内容
- 执行记录：哪些尝试已经发生，成本和结果分别是什么

对我来说，这些对象最重要的不是技术意义上的操作完整性，而是它们是否被正确组织。

很多内容并不适合直接删除，而更适合归档、折叠或抑制。因为这套系统不是普通后台，它更像一套长期工作痕迹。如果痕迹被清理得过于干净，后面就很难解释当时为什么会形成那个判断。

如果只能优先做一个核心页面，我会先做“项目脉络详情页”。因为它最能代表这套系统的核心：不是看一串任务，而是看一个主题如何由线索、判断、资源和输出逐步展开。

<figure>
  <svg viewBox="0 0 1200 760" role="img" aria-label="项目脉络详情页的工作草图" style="width:100%;height:auto;border-radius:24px;border:1px solid #dbe2ea;background:linear-gradient(180deg,#fbfcfd 0%,#f8fafc 100%);">
    <rect x="46" y="42" width="1108" height="676" rx="28" fill="#ffffff" stroke="#dbe2ea"></rect>
    <text x="82" y="90" font-size="32" font-weight="700" fill="#0f172a">项目脉络页草图：看一个主题如何被持续推进</text>
    <text x="82" y="126" font-size="18" fill="#475569">如果只能先做一个核心页面，我会先做这一页，因为它最能把判断、证据、资源和输出接起来。</text>
    <rect x="82" y="166" width="776" height="98" rx="24" fill="#eff6ff" stroke="#bfdbfe"></rect>
    <text x="116" y="208" font-size="20" font-weight="700" fill="#1d4ed8">主题：自进化个人 Agent</text>
    <text x="116" y="238" font-size="15" fill="#334155">当前阶段：scoping · 当前重点：先把多 Agent 工作流、项目脉络和产品日记链路收顺</text>
    <rect x="890" y="166" width="230" height="234" rx="24" fill="#f8fafc" stroke="#e2e8f0"></rect>
    <text x="922" y="212" font-size="18" font-weight="700" fill="#0f172a">右侧便签</text>
    <text x="922" y="246" font-size="14" fill="#334155">- 当前阻塞</text>
    <text x="922" y="274" font-size="14" fill="#334155">- 待验证假设</text>
    <text x="922" y="302" font-size="14" fill="#334155">- 下一条 prompt</text>
    <text x="922" y="330" font-size="14" fill="#334155">- 暂不处理事项</text>
    <rect x="82" y="300" width="500" height="144" rx="24" fill="#f8fafc" stroke="#e2e8f0"></rect>
    <text x="116" y="344" font-size="18" font-weight="700" fill="#0f172a">当前判断</text>
    <text x="116" y="376" font-size="15" fill="#334155">- 问题不是工具不足，而是工作链缺少连续组织</text>
    <text x="116" y="404" font-size="15" fill="#334155">- EvoMap / Evolver 是底层进化能力，不是日常工具层</text>
    <rect x="620" y="300" width="500" height="144" rx="24" fill="#f8fafc" stroke="#e2e8f0"></rect>
    <text x="654" y="344" font-size="18" font-weight="700" fill="#0f172a">关键证据</text>
    <text x="654" y="376" font-size="15" fill="#334155">- 多 Agent 切换导致上下文回填成本很高</text>
    <text x="654" y="404" font-size="15" fill="#334155">- 查询结果、资源信息和 skill 经验缺少稳定回流路径</text>
    <rect x="82" y="476" width="500" height="144" rx="24" fill="#fff7ed" stroke="#fed7aa"></rect>
    <text x="116" y="520" font-size="18" font-weight="700" fill="#c2410c">资源引用</text>
    <text x="116" y="552" font-size="15" fill="#334155">- 服务器 / 路径 / 工具 / 账号引用</text>
    <text x="116" y="580" font-size="15" fill="#334155">- openclaw 带回来的资料和线索</text>
    <rect x="620" y="476" width="500" height="144" rx="24" fill="#f0fdf4" stroke="#bbf7d0"></rect>
    <text x="654" y="520" font-size="18" font-weight="700" fill="#15803d">输出与下一步</text>
    <text x="654" y="552" font-size="15" fill="#334155">- 生成产品日记草稿</text>
    <text x="654" y="580" font-size="15" fill="#334155">- 继续下一轮结构调整和验证</text>
    <rect x="82" y="646" width="1038" height="42" rx="16" fill="#fefce8" stroke="#fde68a"></rect>
    <text x="116" y="673" font-size="15" fill="#334155">时间线：05/02 明确五层链路 → 05/02 收紧导航思路 → 05/02 形成第一篇产品日记草稿</text>
  </svg>
  <figcaption>如果只能先做一个核心页面，我会做“项目脉络页”，因为它最能把判断、证据、资源和输出真正接在一起。</figcaption>
</figure>

## 下一步我会怎么推进

如果把这篇当作第一篇产品日记，我下一步不会试图一次做完整系统，而是先打通最短闭环：

1. 先把“项目脉络”这个核心对象做稳
2. 让 openclaw 带回来的信息更自然地进入资源库和收件箱，而不是混进编程主链路
3. 让产品日记从真实工作里自然长出草稿，同时保留人工确认
4. 再把 evomap-farmer 的导航和整体结构，从页面驱动逐步收束为对象驱动

我不想再做一个传统的项目管理模块。

我想做的，是一套会随着使用逐步理解我工作方式的个人 Agent：

- 它知道我在不同场景下如何推进工作
- 它区分上下文、判断、下一步和可执行事项
- 它知道哪些经验值得进入 skill 演化
- 它知道哪些过程最终值得被公开表达

如果这条路成立，那么以后的每一篇产品日记都不只是一次发布，而会成为下一轮产品迭代的起点。
