# 工作流说明

以后你更新内容，就只在 `AiTool-content` 仓里处理。

## 1. 新建文章

在 `templates/` 里选一个模板：

- `daily-note-template.md`
- `product-update-template.md`
- `experiment-log-template.md`
- `rich-media-note-template.md`

复制到 `posts/`：

```bash
cd ~/WebstormProjects/AiTool-content
cp templates/daily-note-template.md posts/2026-05-02-my-note.md
```

## 2. 改内容

修改：

- frontmatter
- 标题
- 正文
- 标签
- 媒体 URL

## 3. 在站点里预览

```bash
cd ../AiTool
npm run dev
```

然后打开：

```text
http://localhost:3002/notes
http://localhost:3002/notes/<slug>
```

## 4. 自查

发布前建议检查：

- 日期是不是对的
- 标签是不是合理
- 图片 / 音频 / 视频是不是能正常打开
- 开头有没有一句清晰判断
- 结尾有没有结论或下一步

## 5. 提交

```bash
cd ../AiTool-content
git add posts/2026-05-02-my-note.md
git commit -m "post: add my note"
git push
```

## 6. 长期维护建议

- 模板长期放在 `templates/`
- 规则长期放在 `guides/`
- 真正要发的内容只放 `posts/`
- 不要把“暂时想法草稿”一直堆在根目录

最稳妥的习惯就是：

- 想发的：进 `posts/`
- 想复用的结构：进 `templates/`
- 想沉淀的方法：进 `guides/`
