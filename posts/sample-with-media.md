---
title: 媒体格式样板
date: 2026-04-25
tags: [工具, sample]
excerpt: 用来演示文章里图片/音频/视频/链接怎么写。
draft: false
---

这篇是用来给自己看渲染效果的样板。后面真正写作时复制这里的语法就行。

## 图片

普通图片直接 Markdown 语法:

```markdown
![日落](https://images.unsplash.com/photo-1506744038136-46273834b3fb?w=1200)
```

## 音频

用 HTML `<audio>`:

```html
<audio controls src="https://cdn.example.com/audio/sample.mp3"></audio>
```

## YouTube 嵌入

```html
<iframe
  width="100%"
  height="420"
  src="https://www.youtube.com/embed/dQw4w9WgXcQ"
  frameborder="0"
  allow="autoplay; encrypted-media; picture-in-picture"
  allowfullscreen
></iframe>
```

## B 站嵌入

```html
<iframe
  width="100%"
  height="420"
  src="//player.bilibili.com/player.html?bvid=BV1Xx411c7mQ&page=1"
  scrolling="no"
  border="0"
  frameborder="no"
  framespacing="0"
  allowfullscreen
></iframe>
```

## 代码块

支持高亮:

```ts
export function greet(name: string) {
  return `hi, ${name}`;
}
```

## 表格 / 任务列表 / 引用

| 项 | 完成度 |
|---|---|
| 列表页 | 100% |
| 详情页 | 100% |
| 标签云 | 80% |

- [x] Markdown 解析
- [x] iframe 视频
- [ ] 全文搜索

> 引用块也支持。配色、间距以站点为准。
