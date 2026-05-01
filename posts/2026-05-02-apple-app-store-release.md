---
title: 苹果 App 上架流程：从 Xcode 打包到 App Store Connect 提审
date: 2026-05-02
tags: [工具, iOS, Xcode, App Store, 开发]
cover: https://owenshen-aitool-assets.oss-cn-shanghai.aliyuncs.com/notes/2026/05/2026-05-02-apple-app-store-release/app-store-release-1-1332259a.png
excerpt: 记录一次 iOS App 上架的最小完整流程：先在 Xcode 归档上传，再到 App Store Connect 填资料、选构建版本并提交审核。
---

苹果 App 上架这件事，不要一开始就把它想成一个复杂发布系统。最小流程其实很清楚：**先把 App 开发和测试好，在 Xcode 里归档上传，然后去 App Store Connect 填资料、选择构建版本、提交审核。**

这篇先记录一条适合自己以后复用的上架路径。

## 上架前先准备什么

真正点 `Archive` 之前，最好先把下面这些东西确认完：

- 已经加入 Apple Developer Program，并且能登录 [App Store Connect](https://appstoreconnect.apple.com/)
- Xcode 项目里的 `Bundle Identifier` 已经确定，后面要和 App Store Connect 里的 Bundle ID 对上
- `Version` 和 `Build` 已经设置好，例如 `Version = 1.0.0`，`Build = 1`
- App 图标、启动页、基础权限说明都已经处理好
- 真机测试过核心流程，不要只在 Simulator 里跑通
- 如果 App 要登录，准备好给审核人员使用的测试账号
- 准备隐私政策 URL、支持页面 URL、App 截图、简介、关键词等上架资料

这里最容易漏的是隐私和审核信息。即使 App 很简单，只要要上架 App Store，也需要在 App Store Connect 里说明隐私处理方式，并提供必要的支持和隐私相关信息。

## 在 Xcode 里打包上传

开发完成后，先回到 Xcode。

第一步，选择正确的运行目标。一般不要选模拟器，而是选择类似 `Any iOS Device` / `Any iOS Device (arm64)` 这样的 iOS 设备目标。这样做的目的不是为了运行，而是为了生成适合发布的归档包。

<figure>
  <img src="https://owenshen-aitool-assets.oss-cn-shanghai.aliyuncs.com/notes/2026/05/2026-05-02-apple-app-store-release/app-store-release-1-1332259a.png" alt="Xcode 选择 Any iOS Device 后执行 Product > Archive" />
  <figcaption>打包前先选择 <code>Any iOS Device (arm64)</code>，再从菜单进入 <code>Product &gt; Archive</code>。</figcaption>
</figure>

然后从菜单栏进入：

```text
Product > Archive
```

注意这里是 `Product > Archive`。点下去之后，Xcode 会开始构建归档包。构建成功后，会自动打开 Organizer 里的 Archives 界面。

<figure>
  <img src="https://owenshen-aitool-assets.oss-cn-shanghai.aliyuncs.com/notes/2026/05/2026-05-02-apple-app-store-release/app-store-release-2-8b356be2.png" alt="Xcode Organizer Archives 界面中的 Validate App 和 Distribute App" />
  <figcaption>Archive 成功后会进入 Archives 界面，右侧可以先 <code>Validate App</code>，再点击 <code>Distribute App</code> 上传。</figcaption>
</figure>

在 Archives 里选中刚刚生成的归档包，可以先点 `Validate App` 做一次基础校验。如果没有明显问题，再点：

```text
Distribute App
```

后面的分发方式一般选择面向 `TestFlight & App Store` 或 `App Store Connect` 的上传路径。继续往后走时，通常保持自动签名，让 Xcode 管理证书和 provisioning profile。确认无误后开始上传。

上传成功不代表马上能提交审核。App Store Connect 还需要处理这个 build，处理完成后才会出现在对应 App 的构建版本列表里。

## 到 App Store Connect 创建应用

上传完成后，打开：

[https://appstoreconnect.apple.com/](https://appstoreconnect.apple.com/)

进入 `Apps`。如果这是第一次上架这个 App，需要先创建一个新的 App 记录。创建时重点填写：

- 平台：iOS
- App 名称
- 主语言
- Bundle ID
- SKU
- 用户访问权限

这里的 Bundle ID 要和 Xcode 项目里的 Bundle Identifier 一致。否则 Xcode 上传的 build 不会正确挂到这个 App 下面。

创建完成后，这个 App 会进入准备提交的状态。接下来要补齐产品页和审核资料。

## 填写上架信息

App Store Connect 里需要填写的信息比较多，但可以按几类来处理。

### 产品页信息

这部分决定用户在 App Store 里看到什么：

- App 名称
- 副标题
- 描述
- 关键词
- 分类
- App 截图
- App 预览视频，可选
- 支持 URL
- 营销 URL，可选

截图是必须认真准备的。它不是简单证明 App 能打开，而是用户判断要不要下载的第一屏材料。最好用真实核心页面，不要只放空白首页。

### App 信息

这部分更偏平台配置：

- 年龄分级
- 内容版权声明
- 价格与销售范围
- 是否包含第三方内容
- 是否面向儿童
- 隐私政策 URL

如果 App 是免费工具，也要检查价格和可用地区。不要默认一路点过去，最后发现没有在目标地区开放。

### 隐私信息

隐私信息要按实际情况填写：

- App 是否收集用户数据
- 收集哪些类型的数据
- 数据是否和用户身份关联
- 数据是否用于追踪
- 第三方 SDK 是否会收集数据

如果用了统计、广告、登录、支付、崩溃分析 SDK，都要把这些第三方行为算进去。这里不要凭感觉填，最好回到代码和 SDK 文档确认。

### 审核信息

审核信息是给 Apple 审核人员看的：

- 联系人姓名、电话、邮箱
- 测试账号和密码，如果 App 需要登录
- 审核备注，例如特殊入口、测试步骤、需要打开的功能开关

如果 App 的核心功能藏得比较深，建议在备注里写清楚审核路径。审核人员找不到功能，也可能导致延迟或被拒。

## 选择构建版本并提交审核

当 Xcode 上传的 build 处理完成后，在 App Store Connect 的 App 版本页面里找到 `Build` 区域，选择刚刚上传的构建版本。

确认所有必填信息都通过后，页面右上角会出现类似 `Add for Review` 的操作。点进去后，把这个 App 版本加入审核提交项。

最后到 App Review / Draft Submission 里点击：

```text
Submit for Review
```

提交后状态会进入等待审核或审核中。后面就可以等 Apple 审核结果了。

## 审核之后会发生什么

提交之后常见状态大概是：

- `Waiting for Review`：已经提交，等待 Apple 开始审核
- `In Review`：Apple 正在审核
- `Rejected`：被拒，需要根据原因修改代码或资料后重新提交
- `Metadata Rejected`：通常是资料、截图、描述、隐私说明等元信息有问题
- `Pending Developer Release`：审核通过，但需要开发者手动发布
- `Ready for Distribution`：已经可在 App Store 分发

如果被拒，不要只看标题，要读完整的 Resolution Center 信息。Apple 通常会说明问题出在哪里，有些是代码问题，有些只是资料没有写清楚。

## 常见卡点

### build 上传成功但 App Store Connect 里看不到

先等一会儿。build 需要处理时间，处理完成通常会有邮件提醒。如果很久都没有出现，再检查 Bundle ID、版本号和上传账号是不是对应同一个 App。

### build 号重复

同一个版本下，`Build` 不能重复。重新上传前，把 Xcode 里的 build number 加一，例如从 `1` 改成 `2`。

### 签名失败

优先确认 Xcode 里登录的是正确的 Apple Developer 账号，Team 选择正确，并且 Bundle ID、Capabilities、证书权限都一致。个人开发时可以先用 `Automatically manage signing` 降低出错概率。

### 审核人员无法登录

如果 App 需要账号才能使用，必须提供可用的测试账号。测试账号不要绑定短信验证码、地区限制或短期过期策略。

### 隐私信息填错

隐私信息要覆盖 App 自己和第三方 SDK 的数据行为。只要实际收集了数据，就不要为了省事填写“不收集”。

## 我的固定上架顺序

以后就按这个顺序走：

1. 开发并真机测试 App
2. 确认 Bundle ID、Version、Build、签名和权限
3. Xcode 选择 iOS Device 目标
4. 执行 `Product > Archive`
5. 在 Organizer 里 `Validate App`
6. 点击 `Distribute App` 上传到 App Store Connect
7. 打开 App Store Connect 创建或进入对应 App
8. 填写产品页、隐私、价格、年龄分级和审核信息
9. 选择上传好的 build
10. `Add for Review`，然后 `Submit for Review`
11. 等审核，通过后按自动发布或手动发布策略上架

核心判断是：**Xcode 负责生成和上传可审核的构建版本，App Store Connect 负责产品页、合规信息和审核提交。** 把这两部分分开看，上架流程就不会乱。

## 参考

- [Apple Developer Documentation: Distributing your app for beta testing and releases](https://developer.apple.com/documentation/xcode/distributing-your-app-for-beta-testing-and-releases)
- [App Store Connect Help: Upload builds](https://developer.apple.com/help/app-store-connect/manage-builds/upload-builds/)
- [App Store Connect Help: Add a new app](https://developer.apple.com/help/app-store-connect/create-an-app-record/add-a-new-app)
- [App Store Connect Help: Submit an app](https://developer.apple.com/help/app-store-connect/manage-submissions-to-app-review/submit-an-app)
- [App Store Connect Help: Manage app privacy](https://developer.apple.com/help/app-store-connect/manage-app-information/manage-app-privacy)
