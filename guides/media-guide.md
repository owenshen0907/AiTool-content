# 媒体嵌入写法

这份文档只讲一件事：在内容仓里怎么写图、音频、视频。

原则：

- 内容仓只放 Markdown
- 媒体本体不提交进来
- 正文里只放可访问的 URL

## 1. 图片

普通图片直接写：

```md
![图注](https://cdn.example.com/image.jpg)
```

如果要更像编辑文档，建议写成 `figure`：

```html
<figure>
  <img src="https://cdn.example.com/image.jpg" alt="工作台主图" />
  <figcaption>这张图负责交代这篇内容的空间和情绪。</figcaption>
</figure>
```

## 2. 音频

推荐写法：

```html
<figure>
  <audio controls src="https://cdn.example.com/audio.mp3"></audio>
  <figcaption>15 到 30 秒的短配音，适合补一句最重要的判断。</figcaption>
</figure>
```

## 3. 原生视频

推荐写法：

```html
<figure>
  <video controls playsinline poster="https://cdn.example.com/poster.jpg" src="https://cdn.example.com/video.mp4"></video>
  <figcaption>一个短视频，用来补完整节奏。</figcaption>
</figure>
```

## 4. YouTube

推荐使用站点支持的指令写法：

```md
::youtube[这是一段演示视频]{#VIDEO_ID}
```

如果你更想手写 HTML，也可以：

```html
<iframe
  width="100%"
  height="420"
  src="https://www.youtube.com/embed/VIDEO_ID"
  allowfullscreen
></iframe>
```

## 5. Bilibili

推荐指令写法：

```md
::bilibili[B站版本]{#BV1xx411c7mD}
```

也支持 HTML：

```html
<iframe
  width="100%"
  height="420"
  src="https://player.bilibili.com/player.html?bvid=BV1xx411c7mD&page=1"
  allowfullscreen
></iframe>
```

## 6. Callout 强调块

站点支持这几种：

```md
:::note{title="结论"}
这一节适合放总判断。
:::

:::tip{title="建议"}
这一节适合放操作建议。
:::

:::warn{title="注意"}
这一节适合放风险或限制。
:::

:::quote{title="原话"}
这一节适合放一句值得单独引用的话。
:::
```

## 7. 最佳实践

- 一篇文章最多放 1 段音频
- 一篇文章最多放 1 到 2 段视频
- 主图负责开场，细节图负责落地
- 媒体前后最好各有一两句解释

不要：

- 纯堆媒体，不写解释
- 一篇文章连续塞 4 个视频
- 把本地路径直接写进 Markdown
