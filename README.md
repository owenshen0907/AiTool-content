# AiTool-content

`AiTool-content` 是 `AiTool` 站点 `/notes` 的独立内容仓。

这个仓库以后就只做一件事：

- 写内容
- 管内容
- 存模板
- 存规则说明

**不放网站代码，不放数据库，不放脚本，不放本地二进制素材。**

网站侧的渲染、样式和路由都在 `AiTool` 仓库里维护；这个仓库只负责 Markdown 内容本身。

## 目录结构

```text
AiTool-content/
├─ posts/                    # 真正会发布到 /notes 的文章
├─ templates/                # 可直接复制的写作模板
├─ guides/                   # 规则、标签、媒体写法、工作流说明
└─ README.md
```

## 怎么用

### 1. 写新内容

在 `templates/` 里挑一个模板，复制到 `posts/`：

```bash
cd ~/WebstormProjects/AiTool-content
cp templates/product-update-template.md posts/2026-05-02-my-update.md
```

然后改：

- frontmatter
- 标题
- 正文
- 媒体 URL

### 2. 本地预览

```bash
cd ../AiTool
npm run dev
```

浏览器打开：

- `http://localhost:3002/notes`
- `http://localhost:3002/notes/<你的 slug>`

### 3. 提交内容

```bash
cd ../AiTool-content
git add posts/2026-05-02-my-update.md
git commit -m "post: add my update"
git push
```

## 先看哪几份文档

第一次使用，先看这几份：

1. [内容规则](./guides/content-rules.md)
2. [标签规则](./guides/tag-guide.md)
3. [媒体嵌入写法](./guides/media-guide.md)
4. [工作流说明](./guides/workflow.md)

## 模板入口

当前可直接复制的模板：

1. [每日记录模板](./templates/daily-note-template.md)
2. [产品更新模板](./templates/product-update-template.md)
3. [实验记录模板](./templates/experiment-log-template.md)
4. [图文音视频模板](./templates/rich-media-note-template.md)

## 当前样板文章

如果你想先看最终效果，再回头写：

- [图文音视频样板](./posts/sample-with-media.md)

## 原则

- 内容仓只放 Markdown
- 模板和规则也放在内容仓里
- 所有图片、音频、视频都通过 URL 引用，不把二进制素材提交进来
- `posts/` 里的文件才会被站点读取
- `templates/` 和 `guides/` 只是给你写作时使用，不会直接发布到 `/notes`
