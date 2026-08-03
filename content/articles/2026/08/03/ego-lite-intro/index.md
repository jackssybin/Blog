---
date: 2026-08-03
title: "ego-lite：专为 AI Agents 设计的浏览器，让自动化速度提升 2.5 倍"
slug: ego-lite-ai-browser-intro
description: "深入介绍 ego-lite —— 一款专为 AI Agents 设计的浏览器，解决了传统自动化方案中"你和 AI 抢标签页"的痛点，支持多任务并行，复杂任务速度提升最高 2.5 倍，token 消耗大幅减少。"
cover: /images/ego-lite-intro/banner.png
categories: ["开源项目", "AI工具"]
layout: article
contenttype: article
---

# ego-lite：专为 AI Agents 设计的浏览器，让自动化速度提升 2.5 倍

上周我在给 Claude Code 配置浏览器自动化的时候，又遇到了那个老问题：我刚点开一个网页，agent 就把我标签页抢了，我只能眼睁睁看着它操作，自己啥也干不了。而且每次都要重新登录，cookie 带不过去，折腾半天才能开始真正的任务。

直到我发现了 **ego-lite** —— 它从设计之初就解决了这个问题：**同一个浏览器，你用你的标签页，AI 跑它自己的隔离空间，互不干扰，速度还比原来快了 2.5 倍**。

这篇文章我会详细介绍它解决了什么问题，核心优势是什么，怎么在 5 分钟内安装上手，以及对比现有方案该怎么选。

## 现有方案的痛点

目前主流的 AI 浏览器自动化方案主要分两类：

1. **自动化框架类**：比如 browser-use、Vercel agent-browser。它们只是一个库，需要你自己提供浏览器，AI 跑的时候占用整个浏览器，你没法同时用，而且登录态很难复用。

2. **AI 原生浏览器类**：比如 ChatGPT Atlas、Perplexity Comet。它们自带浏览器，但只能给自己的 AI 用，你没法把它接到你正在用的 Claude Code / Codex / Cursor 上。

不管哪类，都绕不开这几个问题：

- ❌ **你和 AI 抢浏览器** — AI 跑任务的时候你只能等着
- ❌ **登录态无法复用** — AI 要访问你已经登录的网站，得重新输密码
- ❌ **不支持多任务并行** — 一次只能跑一个任务，效率低
- ❌ **循环调用多，token 消耗大** — 每次操作都要"截图标注 → 调用模型 → 下一步"，复杂任务要很多轮

## ego-lite 是怎么解决的？

ego-lite 的思路很简单：做一个**你和 AI 都能用的浏览器**，给 AI 分配独立的"Spaces"（任务空间），所有任务都在隔离空间里跑，不影响你正常上网，还能复用你已经有的 Chrome 数据。

核心特性对比：

| 特性 | ego-lite | browser-use | agent-browser | ChatGPT Atlas | Perplexity Comet |
|---|:---:|:---:|:---:|:---:|:---:|
| 多任务并行 | ✅ | — | — | — | — |
| 可复用 Chrome 登录数据 | ✅ | — | — | ✅ | ✅ |
| 同一浏览器，隔离工作区 | ✅ | — | — | — | — |
| 压缩语义输入，token 更少 | ✅ | — | ✅ | — | — |
| 支持外部 AI Agent 控制 | ✅ | ✅ | ✅ | — | — |
| 数据本地存储 | ✅ | ✅ | ✅ | — | — |
| 无登录摩擦 | ✅ | — | — | ✅ | ✅ |
| 可日常使用 | ✅ | — | — | ✅ | ✅ |
| 免费 | ✅ | ✅ | ✅ | — | — |

核心设计优势：

### 1. 代码而非 CLI 驱动，速度提升 2.5 倍

传统方案是"模型输出指令 → CLI 执行 → 返回结果 → 模型再输出指令"这样的循环，复杂任务要很多轮。

ego-lite 把浏览器能力直接暴露为 JavaScript 函数，AI 可以一次性写出完整的多步骤任务代码，一口气执行完，减少了来回交互。官方测试显示，在复杂任务上，比 Vercel agent-browser 快最高 **2.5 倍**，token 消耗也少很多。

### 2. 每个 AI 一个独立 Space，你照样上网

你可以继续在当前标签页浏览，AI 在它自己的 Space 里跑任务，互不打扰。你随时可以看进度，也可以随时接手。多个 AI 可以同时开多个 Space，**并行跑多个任务** — 比如 Claude Code  enrich 10 条线索，Codex 同时爬 5 个竞争网站，都没问题。

### 3. 一键迁移 Chrome 数据，登录直接用

第一次启动的时候，ego-lite 会问你要不要迁移 Chrome 数据。同意之后，你的所有 cookies、登录态、书签、扩展都会带过来，AI 可以直接访问你已经登录的网站，不用再重新登录。

### 4. 最强页面快照，能处理嵌套 iframe

得益于内核级定制，ego-lite 能生成最高质量的页面快照，可靠处理深度嵌套 iframe 这种其他方案经常失败的场景。

### 5. 支持任何 Agent CLI，不用换工具

`ego-browser` 是连接层，支持 Claude Code、Codex、Cursor 或者你自己的自定义 Agent，不用换你正在用的 AI 工具。

## 5 分钟快速上手

目前 ego-lite 只支持 macOS，Windows 和 Linux 在 roadmap 上。

### 方式一：直接下载安装

1. 下载对应版本：
   - [Apple Silicon](https://cdn.ego.app/channel/github_github_referral/setup/macos/arm64/egolite.dmg)
   - [Intel](https://cdn.ego.app/channel/github_github_referral/setup/macos/x64/egolite.dmg)

2. 打开安装，它会自动把 `ego-browser` skill 添加到你机器上所有 agent 的技能目录。

3. 第一次启动，选择迁移 Chrome 数据（推荐）。

### 方式二：npx 添加 skill

如果你只需要安装技能，后续让 agent 引导你安装 app：

```bash
npx skills add citrolabs/ego-lite
```

### 运行第一个任务

安装好之后，在你的 agent CLI 里直接输入：

```
/ego-browser follow @ego_agent on x.com for me
```

Agent 就会自动打开 x.com，帮你完成关注操作，整个过程你该干嘛干嘛，不用管它。

## 实际体验感受

我用它跑了几个常见的自动化任务：

1. **爬取数据**：多个页面并行爬取，确实比 browser-use 快很多，因为不用每次都重启浏览器。
2.** 内容整理 **：让 AI 帮我整理一个网站的文章列表，它在自己的 Space 里慢慢跑，我继续写代码，互不影响。这个体验真的爽，之前用其他方案，我只能干等着。
3.** 需要登录的操作 **：因为复用了 Chrome 的 cookies，直接就能操作，不用重新扫码登录，省了好多时间。

当然也有局限性：

- 目前只支持 macOS，Windows/Linux 用户还要等。
- 它是一个完整的浏览器，需要下载安装，不是纯 npm 包就能搞定。
- 内核定制的功能只有 app 才有，开源仓库里是连接层代码。

## 适用人群和场景

**推荐使用：**

- 你正在用 Claude Code / Codex / Cursor，经常需要浏览器自动化
- 你受够了 AI 抢你的标签页，或者每次都要重新登录
- 你需要跑多个并行的浏览器任务，想要提高效率
- 你想要减少 token 消耗，让复杂任务跑得更快

**暂时不推荐：**

- 你用的是 Windows 或 Linux（等官方支持吧）
- 你只需要偶尔跑一次简单的自动化，现有方案已经够用
- 你不想安装新浏览器，只想要纯 Node.js 方案

## 总结

ego-lite 找到了 AI 浏览器自动化领域一个很精准的痛点：**你和 AI 真的不需要抢同一个浏览器窗口**。给 AI 隔离空间，复用现有数据，支持并行，这几个点戳得很准。

如果你正好在找这方面的工具，花 5 分钟装上试试，应该能让你的 AI 自动化效率提升不少。

**项目地址：** https://github.com/citrolabs/ego-lite
**官方文档：** https://lite.ego.app/document/

## 可收藏的快速参考

### 安装命令速查

```bash
# npx 安装 skill
npx skills add citrolabs/ego-lite

# 让 agent 帮你安装
Set up ego lite for me: https://github.com/citrolabs/ego-lite
Read `skills/ego-browser/references/install.md` and follow the steps to install ego lite.
```

### 基本使用格式

```
/ego-browser <你的任务描述>
```

### 关键优点总结

- ✅ 你用你的，AI 跑 AI 的，互不干扰
- ✅ 复用 Chrome 登录态，不用重新登录
- ✅ 多任务并行，同一个浏览器跑多个 AI 任务
- ✅ 代码驱动，复杂任务快 2.5 倍，token 更少
- ✅ 支持所有主流 Agent CLI，不用换工具
- ✅ 免费使用，数据本地存储
