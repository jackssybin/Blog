---
date: 2026-08-03
title: "Felo AI CLI：给 Claude Code 一键增加 12 个实用技能"
slug: felo-ai-cli-claude-code-12-skills
description: "Felo AI CLI 是一个开源工具集，一键安装就能给 Claude Code/Gemini CLI/Codex 增加实时搜索、PPT生成、思维导图、推文写作、知识库管理等 12 个实用技能，开箱即用，不用自己攒脚本。"
cover: /images/felo-ai-cli-intro/icon.svg
categories: ["开源项目", "AI工具"]
layout: article
contenttype: article
---

# Felo AI CLI：给 Claude Code 一键增加 12 个实用技能

上周我想让 Claude Code 帮我搜索一点最新信息，结果发现它本身没有联网能力，得自己装插件或者写脚本折腾。折腾到一半发现了 **Felo-skills** —— 它已经把常用的 12 个技能都做好了，npm 一键安装就能用，支持 Claude Code/Gemini CLI/Codex 等主流 AI 客户端。

这篇文章详细介绍它能干什么，怎么安装，哪些技能真的好用，哪些可以先等等。

## 它解决了什么问题？

你肯定也遇到过：Claude Code 很强，但缺很多实用能力：

- 没法联网搜最新信息
- 想生成个 PPT 还要自己找工具导
- 让它写推文，不知道你的风格
- 爬网页、拿 YouTube 字幕还要自己装依赖

Felo AI CLI 把这些常用能力都做成了开箱即用的技能，装一次到处用。

## 12 个技能一览

Felo 提供了 12 个技能，覆盖搜索、内容生成、网页抓取、社交媒体、知识库等场景：

| 技能 | 功能 | 推荐指数 |
|---|---|:---:|
| **felo-search** | 实时网络搜索，AI 总结答案 | ⭐⭐⭐⭐⭐ |
| **felo-slides** | 一句话生成 PPT，直接返回链接 | ⭐⭐⭐⭐⭐ |
| **felo-mindmap** | 一句话生成思维导图，多种布局 | ⭐⭐⭐⭐⭐ |
| **felo-landingpage** | 一句话生成落地页并托管 | ⭐⭐⭐⭐ |
| **felo-web-fetch** | 提取网页正文，支持 markdown | ⭐⭐⭐⭐ |
| **felo-youtube-subtitling** | 获取 YouTube 视频字幕 | ⭐⭐⭐ |
| **felo-x-search** | 搜索 X (Twitter) 推文/用户 | ⭐⭐⭐ |
| **felo-livedoc** | 管理个人知识库，支持语义搜索 | ⭐⭐⭐⭐ |
| **apple-buy-advisor** | 买苹果产品前帮你调研对比 | ⭐⭐⭐ |
| **felo-twitter-writer** | 分析推文风格，按你的风格写推文 | ⭐⭐⭐⭐⭐ |
| **felo-superAgent** | 带实时搜索的流式对话 | ⭐⭐⭐⭐ |
| **doc-snapshot-agent** | 自动给 Markdown 文档配截图和 AI 图 | ⭐⭐⭐ |

下面挑几个最常用的说说体验。

### 1. felo-search：实时联网搜索

这个应该是最常用的。Claude 本身训练数据有截止日期，碰到最新信息、天气、价格、新闻就瞎编。用 `felo-search` 一句话就能搜到最新结果，AI 直接总结答案。

```bash
felo search "React 19 新特性"
felo search "今天东京天气"
```

在 Claude Code 里直接触发，不用跳出去浏览器搜，再粘回来，省很多时间。

### 2. felo-slides：一句话生成 PPT

这个真的香。你只需要给个主题，它直接生成好在线 PPT，返回链接你就能看、编辑、导出。

```bash
felo slides "Q4 2024 业务回顾，10 页"
```

开会要个应急 PPT，几分钟就能出来，不用自己打开 Keynote 慢慢调。

### 3. felo-mindmap：一句话生成思维导图

整理思路、梳理项目结构、做读书笔记的时候特别好用。支持多种布局：

- 标准结构图
- 时间线
- 鱼骨图

```bash
felo mindmap "2024 AI 技术趋势" --layout TIMELINE
felo mindmap "项目问题分析" --layout FISHBONE
```

生成完直接给你在线链接，打开就能看。

### 4. felo-twitter-writer：按你的风格写推文

这个功能做得非常细腻。它能：

- 分析任意 X 用户的推文风格，提取"风格 DNA"
- 让你选风格，然后按这个风格写推文/线程
- 保存你自己的风格，每次写都保持一致

在 Claude Code 里用：

```
/felo-twitter-writer Write a thread about why most startups fail in the style of paulg
```

如果你经常写 X 推文，这个技能真的能省很多事。

### 5. felo-livedoc：个人知识库

你可以创建自己的知识库，上传 PDF、添加网页、添加文档，然后语义搜索里面的内容。相当于把 Felo 当成你的个人 RAG 引擎。

```bash
felo livedoc create --name "我的项目文档"
felo livedoc add-urls <id> --urls "https://example.com/docs"
felo livedoc retrieve <id> --query "怎么配置 API"
```

## 5 分钟安装上手

### 第一步：安装 CLI

```bash
npm install -g felo-ai
```

### 第二步：配置 API Key

去 [Felo AI](https://felo.ai) 注册拿 API Key（设置 → API Keys），然后：

```bash
felo config set FELO_API_KEY your-api-key-here
```

就好了。Key 存在 `~/.felo/config.json`。

### 第三步：安装 Claude Code 技能

如果你用 Claude Code，一条命令就能装完所有技能（通过 ClawHub）：

```bash
clawhub install felo-search
clawhub install felo-slides
clawhub install felo-mindmap
# ... 或者装你需要的单个技能

# 如果装 twitter-writer 需要依赖：
clawhub install felo-twitter-writer  # 会自动装依赖 felo-superAgent + felo-livedoc
```

手动安装也很简单：

```bash
git clone https://github.com/Felo-Inc/felo-skills
cd felo-skills
cp -r felo-search ~/.claude/skills/
cp -r felo-slides ~/.claude/skills/
# ... 复制你需要的技能
```

支持不止 Claude Code：

| AI 客户端 | 安装方式 |
|---|---|
| Claude Code | 上面的方法 |
| Gemini CLI | `cp -r * ~/.gemini/skills/` |
| OpenAI Codex | `cp -r * ~/.codex/skills/` |
| Hermes Agent | `bash <(curl -s https://raw.githubusercontent.com/Felo-Inc/felo-skills/main/scripts/install-hermes.sh)` |

## 实际使用体验

我用了几天，感觉几个高频技能真的能提升效率：

- **搜索**：不用切浏览器，Claude 里直接问直接拿结果，上下文不乱跳
- **PPT 生成**：应急、初稿真的太快了，比自己做省一小时
- **推文写作**：风格分析这点做得很好，能学到大V的写作感觉，自己写也能保持风格一致
- **思维导图**：梳理复杂问题的时候，帮你结构化，比你自己在 markdown 里写清单清晰多了

当然也有一些限制：

- 需要 Felo API Key，虽然免费额度应该够用了，但还是要注册
- 生成 PPT/思维导图都是在线托管，没法下载源码本地改（当然可以导出）
- 一些高级功能比如推文风格库依赖 LiveDoc，需要多一步配置

## 谁该装，谁可以再等等？

✅ **推荐立刻安装：**
- 你天天用 Claude Code/Gemini CLI 做开发
- 你需要经常搜最新信息，厌倦了切浏览器
- 你需要快速产出 PPT/思维导图，不想开重量级软件
- 你经常写 X 推文，想要保持风格一致

⏳ **可以再等等：**
- 你很少用 AI 终端客户端，都是在网页上用
- 你只需要基础对话，不需要这些扩展能力
- 你不想注册额外的账号拿 API Key

## 总结

Felo-skills 找准了当前 AI 终端客户端的一个痛点：**能力很多，但开箱即用的实用技能太少**，大多数时候你得自己写脚本攒能力。

它把 12 个高频场景都做成了一键安装的技能，质量都还不错，常用的几个搜索/PPT/思维导图/推文写作真的能省很多时间。如果你是 Claude Code 重度用户，值得花 5 分钟装上试试。

**项目地址：** https://github.com/Felo-Inc/felo-skills
**官方网站：** https://felo.ai
**文档：** https://openapi.felo.ai/docs/

## 安装命令速查（可收藏）

```bash
# 安装 CLI
npm install -g felo-ai

# 配置 API Key
felo config set FELO_API_KEY your-key

# Claude Code  via ClawHub
clawhub install felo-search
clawhub install felo-slides
clawhub install felo-mindmap
clawhub install felo-twitter-writer  # 需要 felo-superAgent + felo-livedoc
```
