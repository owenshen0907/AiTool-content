---
title: 我不想再维护一套项目管理系统了：让 Codex 和 Claude Code 自己长出项目脉络
date: 2026-05-02
publishedAt: 2026-05-02T12:58:21+09:00
tags: [产品, AI, 工具, evomap-farmer, AiTool, architecture, devlog]
excerpt: 我最近越来越不想把开发过程重新抄进一个看板里，所以这次决定把项目进度做成一层 AI 驱动的“项目脉络”：从 Codex 和 Claude Code 的真实迭代里长出来，再经过人工确认，最后推到 AiTool-content 对外公开。
draft: false
---

这几天我有一个越来越强的厌烦感：**功能明明是在 Codex 和 Claude Code 里一点点被做出来的，最后却还要我再手工把过程抄进另一套项目管理工具。**

那套动作我不是不会做，只是越来越觉得它不诚实。

真正发生过的东西在：

- prompt
- agent 回答
- 改动过的文件
- 验证有没有通过
- 哪一步卡住了

结果我还要再回头补一层“人工翻译过的任务系统”，最后常常只剩下两个结局：

1. 要么我懒得补，于是项目进度失真。
2. 要么我硬着头皮补，于是我在维护第二套世界。

:::note{title="这次的核心判断"}
我不想再造一套传统项目管理模块了。更对的方向是：让项目进度直接从 Codex / Claude Code 的真实工作流里长出来，再经过我确认，最后沉淀成可公开的内容。
:::

## 我这次真正想解决的，不是“记任务”，而是“记脉络”

传统项目管理工具最擅长的是：

- 建卡片
- 拖状态
- 记截止时间
- 分配协作者

这些事本身没错，但它们不等于我现在最需要的东西。

我现在更在意的是另一类问题：

- 这个功能为什么突然值得做了？
- 我到底改过几轮判断？
- 哪些 prompt 只是试探，哪些已经变成稳定方向？
- 哪一次修改是真正把事情推过去了？
- 哪些过程值得以后公开写出来？

换句话说，我要的不是一个“任务列表”，而是一条**项目脉络**。

## 我最后决定把这件事拆成三层

我不准备再开一个新系统，而是直接复用我现在已经在用的三套东西：

- `EvoMap Farmer`：负责私有采集、AI 提炼、线程记忆
- `AiTool-content`：负责公开内容落盘
- `AiTool`：负责网站呈现

这三层一旦接起来，事情就顺了。

<figure>
  <svg viewBox="0 0 1200 700" role="img" aria-label="项目脉络的三层结构图" style="width:100%;height:auto;border-radius:24px;border:1px solid #e2e8f0;background:linear-gradient(180deg,#f8fbff 0%,#ffffff 100%);">
    <defs>
      <linearGradient id="flowA" x1="0" y1="0" x2="1" y2="1">
        <stop offset="0%" stop-color="#dbeafe"></stop>
        <stop offset="100%" stop-color="#eff6ff"></stop>
      </linearGradient>
      <linearGradient id="flowB" x1="0" y1="0" x2="1" y2="1">
        <stop offset="0%" stop-color="#dcfce7"></stop>
        <stop offset="100%" stop-color="#f0fdf4"></stop>
      </linearGradient>
      <linearGradient id="flowC" x1="0" y1="0" x2="1" y2="1">
        <stop offset="0%" stop-color="#fef3c7"></stop>
        <stop offset="100%" stop-color="#fff7ed"></stop>
      </linearGradient>
      <marker id="arrow" markerWidth="12" markerHeight="12" refX="10" refY="6" orient="auto">
        <path d="M0,0 L12,6 L0,12 z" fill="#64748b"></path>
      </marker>
    </defs>

    <text x="70" y="80" font-size="34" font-weight="700" fill="#0f172a">我想要的不是“再记一遍”，而是“顺着真实工作流把脉络长出来”</text>
    <text x="70" y="118" font-size="18" fill="#475569">输入、提炼、公开，各做各的事，不再让一个系统硬扛全部职责。</text>

    <rect x="70" y="170" width="300" height="380" rx="28" fill="url(#flowA)" stroke="#bfdbfe"></rect>
    <text x="100" y="220" font-size="18" font-weight="700" fill="#1d4ed8">01 / 私有工作流</text>
    <text x="100" y="265" font-size="34" font-weight="700" fill="#0f172a">EvoMap Farmer</text>
    <text x="100" y="305" font-size="18" fill="#334155">把真实发生过的工作证据接住。</text>
    <text x="100" y="355" font-size="16" fill="#334155">• Codex / Claude Code prompt</text>
    <text x="100" y="388" font-size="16" fill="#334155">• agent summary / file changes / validation</text>
    <text x="100" y="421" font-size="16" fill="#334155">• 今日工作收件箱 + AI 提炼</text>
    <text x="100" y="454" font-size="16" fill="#334155">• project_thread 私有长期记忆</text>
    <text x="100" y="507" font-size="15" fill="#475569">它负责“记全”，但不直接对外说。</text>

    <rect x="450" y="170" width="300" height="380" rx="28" fill="url(#flowB)" stroke="#bbf7d0"></rect>
    <text x="480" y="220" font-size="18" font-weight="700" fill="#15803d">02 / 内容草稿层</text>
    <text x="480" y="265" font-size="34" font-weight="700" fill="#0f172a">AiTool-content</text>
    <text x="480" y="305" font-size="18" fill="#334155">把值得公开的阶段结果写成稿件。</text>
    <text x="480" y="355" font-size="16" fill="#334155">• public_note_draft</text>
    <text x="480" y="388" font-size="16" fill="#334155">• Markdown + frontmatter</text>
    <text x="480" y="421" font-size="16" fill="#334155">• draft / publish 分离</text>
    <text x="480" y="454" font-size="16" fill="#334155">• 模板、标签、写作节奏统一</text>
    <text x="480" y="507" font-size="15" fill="#475569">它负责“说清”，但不负责采集原始证据。</text>

    <rect x="830" y="170" width="300" height="380" rx="28" fill="url(#flowC)" stroke="#fed7aa"></rect>
    <text x="860" y="220" font-size="18" font-weight="700" fill="#c2410c">03 / 对外呈现层</text>
    <text x="860" y="265" font-size="34" font-weight="700" fill="#0f172a">AiTool /notes</text>
    <text x="860" y="305" font-size="18" fill="#334155">把稿件真正变成对外可读页面。</text>
    <text x="860" y="355" font-size="16" fill="#334155">• tags 过滤</text>
    <text x="860" y="388" font-size="16" fill="#334155">• 公开时间线</text>
    <text x="860" y="421" font-size="16" fill="#334155">• 图文音视频呈现</text>
    <text x="860" y="454" font-size="16" fill="#334155">• 以后再做项目页 / series 页</text>
    <text x="860" y="507" font-size="15" fill="#475569">它负责“让别人看懂”，不负责内部判断。</text>

    <line x1="370" y1="360" x2="450" y2="360" stroke="#64748b" stroke-width="4" marker-end="url(#arrow)"></line>
    <line x1="750" y1="360" x2="830" y2="360" stroke="#64748b" stroke-width="4" marker-end="url(#arrow)"></line>
    <text x="386" y="338" font-size="14" fill="#475569">人工确认后</text>
    <text x="767" y="338" font-size="14" fill="#475569">落到公开稿件</text>
  </svg>
  <figcaption>我最后决定不再让一个系统把“采集、判断、公开”全做了，而是明确拆成三层。</figcaption>
</figure>

## 为什么“今日工作收件箱”很重要，但它不能单独扛完整件事

我现在的 `今日工作收件箱` 已经很接近这个方向了。

它擅长做三件事：

1. 导入当天的 Codex / Claude Code 工作痕迹
2. 用 AI 把这些内容提炼成“候选”
3. 让我在真正写出外部内容之前，先做一次人工确认

所以它天然适合做**入口**。

但它还不适合单独做“长期项目进度管理”，原因也很直接：

- 它偏当天
- 它偏候选
- 它偏审阅

而项目脉络需要的是：

- 跨天
- 跨轮
- 跨 agent
- 能持续追踪同一个功能主题

所以收件箱可以是门口，但不能是整栋楼。

## 我准备新增的核心对象，其实只有两个

老实说，我最怕的是把这件事一想大，就又开始长出一堆概念。

所以我这次强行收住，只加两个对象。

### 1. `project_thread`

这不是任务卡，而是一条功能线程。

它记录的不是“要做什么”，而是“这件事现在推进到了哪、为什么这么推进”。

我现在想让它至少有这些字段：

| 字段 | 含义 |
| --- | --- |
| `thread_id` | 稳定线程 ID |
| `project` | 属于哪个项目 |
| `topic` | 这条线程在讲哪个功能/方向 |
| `current_goal` | 当前这轮真正想完成什么 |
| `status` | 当前状态 |
| `latest_summary` | 最近一次推进的阶段总结 |
| `key_decisions` | 关键判断，不是流水账 |
| `open_questions` | 还没解决的问题 |
| `next_prompt` | 下一条最合理的 agent 提示词 |
| `publish_ready` | 是否值得转成公开内容 |

这里最关键的一点是：**线程不是按仓库建，也不是按 prompt 建，而是按“一个稳定主题”建。**

比如：

- 统一工作台简化
- 积分实时刷新修复
- 项目脉络 AI 化

这样才真的有回看价值。

### 2. `public_note_draft`

这个对象的职责就单纯很多：

- 从 `project_thread` 里抽一段可公开的阶段结果
- 填成一篇 Markdown 草稿
- 放进 `AiTool-content`

它不是原始记录，也不是内部 thread，只是**准备拿出去说的话**。

## 它跟传统项目管理最大的区别是什么

我专门把这件事想了一遍，差别其实很大。

| 传统 PM | 我这次想做的 |
| --- | --- |
| 人先建卡 | 工作先真实发生 |
| 人再更新状态 | AI 先识别阶段，再由人确认 |
| 目标是协作排期 | 目标是保留真实迭代脉络 |
| 内容偏“任务” | 内容偏“判断、变化、阻塞、下一步” |
| 很容易空转 | 必须绑定真实 prompt / 文件改动 / 验证结果 |

说白了，我不是想把 AI 塞进项目管理，而是想让项目进度直接从 AI 工作流里生出来。

## 我最在意的一条边界：私有证据，不等于公开内容

这一层边界如果不提前想清楚，后面一定会翻车。

因为真实工作流里会有很多不适合直接公开的东西：

- 原始 prompt
- 私有路径
- 暂时错误的判断
- 凭证、配置、环境信息
- 还没整理过的碎片推演

所以我现在把边界划成三层：

1. `activity`：私有证据，只在本地保存
2. `project_thread`：内部结构化脉络，可复用但不直接外发
3. `AiTool-content`：真正对外的成品

<figure>
  <svg viewBox="0 0 1200 720" role="img" aria-label="一条项目线程从私有证据到公开稿件的演进图" style="width:100%;height:auto;border-radius:24px;border:1px solid #e2e8f0;background:#ffffff;">
    <defs>
      <marker id="arrowB" markerWidth="12" markerHeight="12" refX="10" refY="6" orient="auto">
        <path d="M0,0 L12,6 L0,12 z" fill="#64748b"></path>
      </marker>
    </defs>
    <text x="72" y="86" font-size="34" font-weight="700" fill="#0f172a">一条线程真正的演进方式</text>
    <text x="72" y="124" font-size="18" fill="#475569">不是从“待办卡片”开始，而是从真实工作证据开始，经过提炼，再长成对外记录。</text>

    <rect x="72" y="180" width="1056" height="120" rx="28" fill="#f8fafc" stroke="#e2e8f0"></rect>
    <text x="108" y="224" font-size="18" font-weight="700" fill="#0f172a">第一层：私有证据</text>
    <text x="108" y="262" font-size="16" fill="#334155">Codex prompt / Claude Code prompt / agent summary / files changed / validation</text>
    <text x="108" y="292" font-size="15" fill="#64748b">这里尽量记全，但不直接公开。</text>

    <line x1="600" y1="300" x2="600" y2="356" stroke="#94a3b8" stroke-width="4" marker-end="url(#arrowB)"></line>

    <rect x="72" y="360" width="1056" height="160" rx="28" fill="#eff6ff" stroke="#bfdbfe"></rect>
    <text x="108" y="406" font-size="18" font-weight="700" fill="#1d4ed8">第二层：项目脉络 thread</text>
    <text x="108" y="445" font-size="16" fill="#334155">主题：统一工作台简化</text>
    <text x="108" y="475" font-size="16" fill="#334155">当前状态：implementing</text>
    <text x="108" y="505" font-size="16" fill="#334155">阶段总结：不再切模式，统一到一页；积分刷新逻辑走强制实时链路；页面层级继续做减法。</text>
    <text x="760" y="445" font-size="16" fill="#334155">阻塞：还缺“项目脉络”对象</text>
    <text x="760" y="475" font-size="16" fill="#334155">下一条 prompt：从今日工作收件箱里抽 project_progress</text>
    <text x="760" y="505" font-size="16" fill="#334155">可公开：是</text>

    <line x1="600" y1="520" x2="600" y2="576" stroke="#94a3b8" stroke-width="4" marker-end="url(#arrowB)"></line>

    <rect x="72" y="580" width="1056" height="100" rx="28" fill="#f0fdf4" stroke="#bbf7d0"></rect>
    <text x="108" y="624" font-size="18" font-weight="700" fill="#15803d">第三层：公开稿件</text>
    <text x="108" y="662" font-size="16" fill="#334155">一篇真的能发到 AiTool-content 的文章，讲清“为什么这么做、怎么拆、下一步怎么长”。</text>
  </svg>
  <figcaption>我很想保留过程，但我不想把过程原样倒出去。中间必须有一层 thread，帮我把碎片整理成能复用的脉络。</figcaption>
</figure>

## 为什么我最终决定把公开输出放到 AiTool-content

这件事我没有重新发明任何新轮子。

因为我已经有了一个非常合适的公开出口：

- 内容只写 Markdown
- 模板和规则已经有了
- 网站读取也已经通了
- `draft` 可以天然作为“公开前草稿状态”

这意味着我根本不需要再做一个“发布后台”。

更省力的方式是：

1. 先在 `EvoMap Farmer` 里确认一条 thread 值得公开
2. 生成一份 `public_note_draft`
3. 直接写到 `AiTool-content/posts/`
4. 如果我还想再润一下，就先留着
5. 改好之后再正式发出去

这一步最重要的价值是：**公开内容和内部过程终于不再脱节。**

## 这套东西落地时，我准备怎么分阶段

我不打算一口气把它做大。

### V1：先从“今日工作收件箱”长出来

第一步只做这些：

- 新增 `project_progress` 这种 insight 类型
- 在收件箱里增加“项目脉络候选”
- 人工确认后更新 `project_thread`
- 同时生成 `AiTool-content` 的 Markdown 草稿

这一步只解决一件事：

> 让项目进度不再靠我手抄，而是能从真实 agent 迭代里自己长出来。

### V2：再补一个轻量的“项目脉络”页

到第二步再做长期视图：

- 看到每个项目当前活跃线程
- 看到每条线程的最近推进
- 看到阻塞和下一条 prompt
- 看到哪些线程已经适合写公开内容

它不是看板，更像一面“当前脑内地图”。

### V3：最后再让网站前台形成系列感

等 `AiTool-content` 的文章积累到一定程度，再考虑：

- 给 `/notes` 增加项目聚合页
- 给同一个 thread 的文章形成 series
- 把“开发迭代”真正变成一个可长期阅读的公开入口

## 这件事对我来说，真正舒服的地方在哪里

不是因为它更“高级”，而是因为它终于比较顺手。

我现在越来越确定一件事：

> 如果一个系统要求我把已经发生过的思考再录入一遍，它迟早会烂掉。

我想要的是另一种感觉：

- 做事的时候，就已经在留下证据
- 证据会被收成 thread
- thread 会变成公开记录
- 公开记录反过来又成为我的长期资产

这样项目、内容、个人表达才会真正连起来。

不是今天为了写一篇文章，硬从工作里抽点东西出来；而是工作本身就带着可以被整理、被回看、被公开的结构。

## 我给自己留的下一步

接下来我会先把这件事收得很窄：

1. 先在 `EvoMap Farmer` 里补 `project_progress`
2. 让“今日工作收件箱”先长出“项目脉络候选”
3. 把第一批公开草稿直接写进 `AiTool-content`

我真正想看到的，不是多一个系统，而是一个更自然的闭环：

**我在 Codex 和 Claude Code 里推进项目，项目脉络自己被记住，最后再从这个口子安静地流到网站上。**

如果这条路走通了，我以后公开写出来的，就不只是结果，而是我这个人这些年是怎么一点点把自己的开发方法长出来的。
