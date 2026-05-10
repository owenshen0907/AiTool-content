---
title: Google 登录本地调试：别先怀疑测试环境，先看回调地址
date: 2026-05-10
publishedAt: 2026-05-10T04:15:00+09:00
series: 产品日记
tags: [产品, 开发, OAuth, Google, 登录, devlog]
excerpt: 这次给本地项目接 Google 登录时，我又一次被 redirect_uri_mismatch 卡住。最后发现问题不在测试环境，而在于前端来源、后端回调地址和 Google OAuth Client 配置没有对齐。
draft: false
---

今天给本地开发环境接 Google 登录，又踩了一次很典型的坑。

页面一直报：

```text
redirect_uri_mismatch
```

第一反应很容易是：是不是测试环境不行？是不是 Google 登录不能在本地跑？是不是 Codex 自带浏览器有什么限制？

但这次排下来，我更愿意把它当成一个提醒：**OAuth 出错时，不要先怀疑“环境玄学”，先把浏览器真正发给 Google 的地址找出来。**

:::note{title="这次的核心判断"}
`redirect_uri_mismatch` 不是测试环境问题，而是 Google OAuth Client 里登记的“已获授权的重定向 URI”，没有和应用实际提交的 `redirect_uri` 完全一致。
:::

## 这次发生了什么

我本地有一个前端页面跑在：

```text
http://127.0.0.1:5174
```

后端服务跑在：

```text
http://localhost:8788
```

前端点击 Google 登录以后，不再直接用 Google Identity Services 的按钮流程，而是改成后端发起 OAuth code flow：

1. 前端跳到后端 `/v1/auth/google/start`
2. 后端生成 Google 授权地址
3. Google 登录完成后，把授权码回调到后端
4. 后端换 token、验证身份，再把登录态带回前端

这个流程本身是对的。它比在前端处理一堆 Google 脚本、FedCM、弹窗限制要稳定，也更适合以后区分本地开发、测试环境和生产环境。

问题出在第三步。

后端生成的回调地址是：

```text
http://localhost:8788/v1/auth/google/callback
```

但 Google OAuth Client 里没有登记这个精确地址，于是 Google 直接拒绝。

## 最容易混的两个配置

Google Cloud 的 OAuth Web Client 页面里，最容易混的是这两块：

| 配置项 | 它解决什么问题 |
| --- | --- |
| 已获授权的 JavaScript 来源 | 允许哪些浏览器页面发起前端请求，比如 `http://localhost:5174` |
| 已获授权的重定向 URI | 登录完成后，Google 可以把用户带回哪里，比如 `http://localhost:8788/v1/auth/google/callback` |

这次我一开始已经配了 JavaScript 来源：

```text
http://localhost:5174
http://127.0.0.1:5174
```

但这只能说明“前端来源”被允许了。

真正出错的是后端 code flow 的回调地址。也就是说，Google 不是在拒绝前端页面，而是在拒绝这个地址：

```text
http://localhost:8788/v1/auth/google/callback
```

这两个配置看起来都在同一个页面里，但用途完全不同。

## 为什么 `localhost` 和 `127.0.0.1` 也要分清

这次还有一个细节：本地开发时，我的页面有时从 `127.0.0.1` 打开，有时后端配置又用了 `localhost`。

对人来说，它们都指向本机。

但对 OAuth 来说，它们是两个不同的字符串。

Google 官方文档里也写得很明确：`redirect_uri` 必须和 OAuth Client 中登记的授权重定向 URI 精确匹配，scheme、domain、大小写、尾部斜杠都要一致。不匹配就会得到 `redirect_uri_mismatch`。

所以本地开发时，最省心的做法是把两条都配上：

```text
http://localhost:8788/v1/auth/google/callback
http://127.0.0.1:8788/v1/auth/google/callback
```

前端来源也同理：

```text
http://localhost:5174
http://127.0.0.1:5174
```

这样以后不管浏览器地址栏用哪一个，都不容易因为字符串不一致而卡住。

## 我这次学到的排错顺序

以后再遇到 Google 登录失败，我会按这个顺序查：

1. 先展开 Google 错误页里的“错误详情”
2. 找到它实际提交的 `redirect_uri`
3. 去 Google Cloud OAuth Client 里检查“已获授权的重定向 URI”
4. 确认协议、域名、端口、路径、尾部斜杠完全一致
5. 再看后端 token exchange、client secret、用户测试名单这些更后面的事

这里顺序很重要。

如果第一步就没过，后面的 client secret、测试用户、数据库用户绑定，都还没轮到。

`redirect_uri_mismatch` 发生在 Google 把用户带回应用之前。它不是后端数据库问题，也不是用户体系问题，更不是“测试环境不能用”。

## 对我自己的系统设计有什么提醒

这次顺手也让我更确定一件事：后面统一后台最好把这些 OAuth 配置抽成环境配置，而不是散在前端代码里。

比较稳的形态应该是：

- 前端只知道“我要登录”
- 后端负责选择 OAuth provider、生成授权地址、处理回调
- 本地、测试、生产只改环境变量
- Google OAuth Client 里按环境登记对应回调地址

这样以后接 Apple、GitHub、微信、飞书登录，模式都能复用。

真正要避免的是：前端一份配置、后端一份配置、Google Console 又一份配置，三边各说各话。最后报错时，看起来像平台问题，其实只是地址没有对齐。

## 当前结论

这次不是 Google 登录不能在本地跑，也不是测试环境不行。

它只是一个很普通、但很容易误判的问题：

> OAuth 里最重要的不是“看起来访问的是同一个本机服务”，而是“实际提交给 Google 的回调字符串，必须和控制台登记的一字不差”。

把这个原则记住，后面本地开发、测试环境、生产环境就都能按同一套方式处理。

## 参考资料

- [Google OAuth 2.0 for Web Server Applications](https://developers.google.com/identity/protocols/oauth2/web-server)
- [Google OAuth redirect_uri_mismatch 说明](https://developers.google.com/youtube/reporting/guides/authorization/client-side-web-apps#redirect_uri_mismatch)
