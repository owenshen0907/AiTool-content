# AiTool-content

AiTool 2.0 站点 (`https://owenshen.top/notes`) 的内容仓库。本仓库与 [AiTool](../AiTool) 是平级、独立的两个 git 仓库:

- **AiTool**: 网站代码,负责渲染
- **AiTool-content**(本仓库): 所有 Markdown 文章 + 本地暂存的素材

## 目录结构

```
AiTool-content/
├─ posts/                # 公开文章,文件名即 slug
│  ├─ 2026-05-01-x-day-one.md
│  └─ ai-claude-vs-codex.md
├─ assets-local/         # 本地暂存的图/音频,push 前由脚本上传到 OSS,不进站点构建
└─ README.md
```

文件名约定:

- 文件名直接就是 URL slug,例如 `posts/x-day-one.md` → `/notes/x-day-one`
- 推荐前缀加日期方便排序(可选): `2026-05-01-x-day-one.md`,但日期由 frontmatter 的 `date` 决定,文件名可不带

## Frontmatter 规范

每篇文章顶部必须有 frontmatter:

```yaml
---
title: 开始运营 X 的第一天      # 必填
date: 2026-05-01              # 必填,YYYY-MM-DD,网站按它倒序
tags: [产品, X运营, 自进化]    # 推荐,自由打,展示层会聚合
cover: https://cdn.xxx.com/x.jpg  # 可选,列表卡片封面
excerpt: 今天把对外表达正式拉起来  # 可选,列表摘要,缺省取正文首段
draft: false                  # 可选,默认 false。true 时网站不展示
---
```

## 快捷视图(网站侧 tag 过滤)

`/notes` 顶部固定 5 个快捷入口,本质就是 tag 过滤:

| 视图 | 命中标签(任意一个) |
|---|---|
| 产品 | `产品` / `product` |
| 生活 | `生活` / `life` / `daily` |
| AI | `ai` / `AI` |
| 工具 | `工具` / `tools` / `software` |
| 全部 | 不过滤 |

也就是说:**你 frontmatter 里只要带这些 tag 之一,就会出现在对应快捷视图**。tag 不限于这五个,任意自由打,展示页会同时显示完整标签云。

## 正文怎么写

普通 Markdown,默认开了 GFM(表格、任务列表、删除线)、代码高亮、原始 HTML。

- 图片:`![alt](https://cdn.../foo.png)` — URL 是上传到 OSS/服务器后的 CDN 地址
- 音频:`<audio controls src="https://cdn.../foo.mp3"></audio>`
- YouTube 视频:`<iframe width="100%" height="420" src="https://www.youtube.com/embed/VIDEO_ID" frameborder="0" allowfullscreen></iframe>`
- B 站视频:`<iframe width="100%" height="420" src="//player.bilibili.com/player.html?bvid=BVxxx&page=1" allowfullscreen></iframe>`
- 内部链接:`[去工具站](/tools)`

## 写作流程

```bash
# 1. 在本地写
cd ~/WebstormProjects/AiTool-content
$EDITOR posts/2026-05-02-new-thoughts.md

# 2. 在 AiTool 项目里本地预览(默认会读 ../AiTool-content)
cd ../AiTool
npm run dev   # 浏览器开 http://localhost:3002/notes

# 3. 满意了再提交并推到远端
cd ../AiTool-content
git add posts/2026-05-02-new-thoughts.md
git commit -m "post: 新文章主题"
git push
```

部署侧:网站构建/启动时会读取本地 `../AiTool-content` 或 `CONTENT_REPO_PATH` 指定的路径。生产部署时把内容仓 clone 到镜像的对应位置即可(细节由 AiTool 仓库 Dockerfile 处理)。

## 媒体存储

- **当前**:图/音频先放 `assets-local/`,你手动上传到对象存储后,把 Markdown 里的链接换成 CDN URL
- **以后**:会有一个 `scripts/publish.mjs` 自动扫 → 上传 → 改写链接 → commit
- **视频**:不存,只用 YouTube/B 站 iframe 嵌入

## 草稿

`draft: true` 的文章网站不展示,可以放心 commit 半成品。
