---
title: "让 AI Agent 自动做电影解说：Narrator AI CLI Skill 实测"
date: 2026-08-21
slug: "narrator-ai-cli-skill-automate-movie-narration"
cover: "/images/narrator-ai-cli-skill-automate-movie-narration/cover-wechat.jpg"
categories: ["开源项目", "AI工具"]
tags: ["AI Agent", "自动化", "短视频", "开源"]
draft: false
contenttype: article
---

# 让 AI Agent 自动做电影解说：Narrator AI CLI Skill 实测

你有没有过这种经历：想做一条电影解说短视频，光是找素材、写文案、配音、剪辑就要花掉大半天，辛辛苦苦做出来播放量还不如人意？

我最近发现了一个非常棒的开源项目，可以让你的 AI Agent 一句话自动完成电影解说视频全流程——**Narrator AI CLI Skill**。

今天这篇文章，我把完整的安装配置步骤、使用方法、踩坑经验都整理好了，看完你就能自己动手试试。

---

## 这到底是什么？

简单来说，这是一套给 AI Agent 用的技能包，配合 `narrator-ai-cli` 命令行工具，可以实现：

你说一句话：**"帮我做一个喜剧风格的《飞驰人生》电影解说视频"**

AI 自动执行全流程：
1. 搜索内置电影素材库
2. 选择对应风格模板
3. 挑选适配的BGM
4. 选择配音角色
5. 生成解说文案
6. 合成完整视频
7. 返回下载链接

整个过程不需要你手动干预，5-10分钟就能得到一条可以直接发布的成品视频。

CLI 和 Skill 的配合关系非常清晰：

| | CLI（命令行工具） | Skill（技能描述文件） |
|---|---|---|
| 是什么 | 可执行命令集合 | 教 AI 怎么用这些命令的说明书 |
| 类比 | 一套厨具 | 一本菜谱 |
| 单独能用吗 | 可以手动在终端用 | 不能，必须配合 CLI |

一句话总结：**CLI 是手脚，Skill 是大脑，两者配合，AI Agent 就能全自动做视频**。

---

## 核心能力

这个项目内置了非常丰富的资源，开箱即用：

- **两条工作流**：支持二创文案（爆款学习）和原创文案（快速模式）
- **三种创作模式**：热门影视、原声混剪、冷门新剧
- **内置资源**：约 100 部电影、146 首 BGM、63 个配音角色、90+ 解说风格模板
- **完整流水线**：从文案生成到视频合成一站式完成
- **独立任务**：还支持声音克隆、文本转语音单独使用
- **错误处理**：全部 18 个 API 错误码都有对应解决方案
- **成本预估**：创建任务前会帮你预估积分消耗，避免超预算

---

## 安装步骤

完整安装只需要四步：

### 第一步：安装 CLI 工具

```bash
pip install "narrator-ai-cli @ git+https://github.com/NarratorAI-Studio/narrator-ai-cli.git"
```

### 第二步：配置 API Key

```bash
narrator-ai-cli config set app_key <你的API_Key>
```

> 没有 API Key？发送邮件至 `merlinyang@gridloud.com` 或扫描项目 README 底部二维码添加微信获取。

### 第三步：安装 Skill 到你的 AI Agent

Skill 由 `SKILL.md` 和 `references/` 目录共同组成，两者缺一不可。根据你的 AI Agent 平台选择对应安装方式：

**OpenClaw（小龙虾）：**
```bash
mkdir -p ~/.openclaw/skills
git clone https://github.com/NarratorAI-Studio/narrator-ai-cli-skill.git \
  ~/.openclaw/skills/narrator-ai-cli
```

**Windsurf / Claude Code：**
```bash
mkdir -p /path/to/your/project/.skills
git clone https://github.com/NarratorAI-Studio/narrator-ai-cli-skill.git \
  /path/to/your/project/.skills/narrator-ai-cli
```

**Cursor：**
```bash
mkdir -p /path/to/your/project/.cursor/rules
git clone https://github.com/NarratorAI-Studio/narrator-ai-cli-skill.git \
  /path/to/your/project/.cursor/rules/narrator-ai-cli
```

**WorkBuddy / QClaw（腾讯系）：**
在技能管理界面上传 `SKILL.md` 以及完整 `references/` 目录，**必须保持目录结构**，`references/` 需要作为子目录和 `SKILL.md` 并列，不能平铺文件。

> 后续升级只需在 clone 目录执行 `git pull` 即可。

### 第四步：开始对话

安装完成后，直接用自然语言和 AI 交流就行：

- 帮我做一个喜剧风格的《飞驰人生》电影解说视频
- 查看有哪些内置电影素材
- 用热血动作风格生成一条解说
- 帮我做5条不同电影的解说视频批量产出

---

## 已验证兼容平台

这个项目已经在多个主流 AI Agent 平台验证过：

| 平台 | 安装方式 | 状态 |
|---|---|---|
| 小龙虾 OpenClaw | `git clone` 到技能目录 | ✅ 已验证 |
| WorkBuddy（腾讯） | 上传 SKILL.md + references | ✅ 已验证 |
| QClaw（腾讯） | 上传 SKILL.md + references | ✅ 已验证 |
| Windsurf | `git clone` 到 .skills 目录 | ✅ 已验证 |
| 有道龙虾 | `git clone` 到技能目录 | ✅ 已验证 |
| 元气 AI | `git clone` 到技能目录 | ✅ 已验证 |
| Claude Code | `git clone` 到项目 .skills 目录 | ✅ 已验证 |
| Cursor | `git clone` 到 .cursor/rules 目录 | ✅ 已验证 |
| 其他支持 Markdown Skill 的 Agent | `git clone` 后指向 SKILL.md | ✅ 兼容 |

---

## 系统要求

- **CLI 版本**: narrator-ai-cli v1.0.0+
- **Python**: 3.10+
- **依赖库**: typer, httpx[socks], httpx-sse, pyyaml, rich
- **API Key**: 需要联系作者获取

---

## 使用场景与适合人群

这个工具非常适合：

1. **内容创业者**：批量生成电影解说短视频，做号矩阵
2. **AI Agent 开发者**：学习如何给 AI 编写可执行技能
3. **短视频创作者**：降低剪辑门槛， focus 在内容创意而不是重复劳动
4. **AI 爱好者**：体验全自动 AI 工作流到底能做什么

如果你已经在使用 Claude Code / Cursor / Windsurf 等现代 AI 编程工具，安装这个技能只需要一分钟，马上就能体验 AI 全自动生成视频的快感。

---

## 总结

Narrator AI CLI Skill 解决了一个非常具体的痛点：**把手动制作电影解说的几小时工作，压缩成一句话指令，AI 帮你搞定一切**。

对于需要批量产出短视频的内容创作者来说，这绝对是效率神器。对于 AI Agent 爱好者来说，这也是一个非常好的案例，展示了如何通过 "CLI + Skill" 的方式，让 AI 真正落地完成实际生产任务。

项目地址：https://github.com/NarratorAI-Studio/narrator-ai-cli-skill

感兴趣的话不妨 clone 下来试试，有任何问题可以在 GitHub Issues 留言，或者联系项目作者获取帮助。

---

**如果你觉得这个项目有用，别忘了去 GitHub 点个 Star 支持开发者 😉**
