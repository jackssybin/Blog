---
date: $(date +%Y-%m-%d)
title: "AI Agent 技能商店：收录 244+ 可直接用的 Claude Code 技能，每日自动更新"
slug: ai-agent-skill-store
cover: /images/ai-agent-skill-store/cover-wechat.jpg
description: 收录最全、更新最快的 AI Agent 技能库，涵盖文档处理、内容创作、编程开发、机器学习、自动化工作流等多个领域的精选技能包。开箱即用，直接导入 Claude Code / Cursor 就能用。
categories: ["开源项目", "AI工具"]
layout: article
contenttype: article
---

# AI Agent 技能商店：收录 244+ 可直接用的 Claude Code 技能，每日自动更新

> 收录最全、更新最快的 AI Agent 技能库，涵盖文档处理、内容创作、编程开发、机器学习、自动化工作流等多个领域的精选技能包。开箱即用，直接导入 Claude Code / Cursor 就能用。


> 收录最全、更新最快的 AI Agent 技能库，涵盖文档处理、内容创作、编程开发、机器学习、自动化工作流等多个领域的精选技能包。开箱即用，直接导入 Claude Code / Cursor 就能用。

## TL;DR

- **项目地址**：https://github.com/anbeime/skill
- **在线预览**：https://skill.vercel.app
- **技能总数**：244 个（官方 182 + 本地 62）
- **更新频率**：每 24 小时自动爬取最新技能
- **适合人群**：Claude Code / Cursor / Codex 用户，想要用现成技能提升效率，不想自己从零写提示词

## 为什么需要这个项目？

用 Claude Code 有一段时间的朋友应该都有这个感受：

1. **技能分散**：好用的技能散落在 GitHub 各个仓库，想要找的时候搜半天找不到
2. **更新不及时**：很多汇总帖几个月就不更了，新出的技能找不到
3. **分类混乱**：同一个技能不同版本分叉，不知道哪个是维护的
4. **本地备份缺失**：作者删库就找不到了，没有完整备份

这个项目就是来解决这些问题的：

- **自动每日同步**：从 `VoltAgent/awesome-agent-skills` 自动爬取，保证始终最新
- **完整备份覆盖**：100% 覆盖率，所有本地技能都有压缩包备份
- **智能分类**：按功能领域分类，好找
- **支持二次开发**：支持 JSON / CSV 导出，方便做自己的工具

## 核心特性

### 🤖 自动更新

每 24 小时自动爬取 [awesome-agent-skills](https://github.com/VoltAgent/awesome-agent-skills) 仓库，确保技能库始终保持最新状态。

### 📦 双重技能库

- **官方技能**：182 个来自 Anthropic、Vercel、Cloudflare、Google Labs、Hugging Face 等顶级团队
- **本地技能**：62 个精选中文技能，涵盖内容创作、视频制作、电商营销等垂直领域

### 🏷️ 智能分类

按照功能、来源、Star 数量等多维度标签进行分类整理。

### 📊 数据导出

支持 JSON 和 CSV 格式导出，方便数据分析和二次开发。

## 本地技能分类速览

### 📝 内容创作与发布（10个）

- `content-creation-publisher` ⭐⭐⭐⭐⭐ - 内容创作与发布全流程
- `intelligent-content-system` ⭐⭐⭐⭐⭐ - 智能内容系统
- `article-illustrator` ⭐⭐⭐⭐ - 文章智能配图
- `baoyu-url-to-markdown` ⭐⭐⭐⭐ - 网页转 Markdown
- `baoyu-format-markdown` ⭐⭐⭐⭐ - Markdown 格式化
- `baoyu-post-to-wechat` ⭐⭐⭐⭐ - 微信公众号发布
- `baoyu-post-to-x` ⭐⭐⭐ - X/Twitter 发布
- `baoyu-xhs-images` ⭐⭐⭐⭐ - 小红书图文生成
- `wechat-hotspot-publisher` ⭐⭐⭐ - 微信热点文章生成

### 🎬 视频创作（9个）

- `video-creation-suite` ⭐⭐⭐⭐⭐ - 完整视频创作套件
- `video-creation-collaborator` ⭐⭐⭐⭐ - 多智能体协同视频创作
- `video-creation-pro` ⭐⭐⭐ - 商品视频创作系统
- `video-recreation` ⭐⭐⭐⭐ - 视频二创工具
- `video-frame-extractor` ⭐⭐⭐ - 视频反推工具
- `viral-video-copywriting` ⭐⭐⭐⭐ - 爆款短视频文案
- `historical-science-video-prod` ⭐⭐ - 历史科学类视频
- `historical-interview-scripts` ⭐⭐ - 历史访谈文案
- `three-body-video-creator` ⭐⭐ - 《三体》视频创作

### 🛒 电商与营销（7个）

- `ecommerce-full-pipeline` ⭐⭐⭐⭐⭐ - 跨境电商全链路自动化（1688 采集/清洗/上架/推广/视频/代发/爆品挖掘/闲鱼选品捡漏）
- `pet-commerce-creator` ⭐⭐⭐ - 萌宠带货短视频
- `ecommerce-copywriter` ⭐⭐⭐ - 电商图片文案
- `ecommerce-video-marketing` ⭐⭐⭐ - 电商视频营销
- `product-marketing-copywriter` ⭐⭐⭐ - 产品营销文案
- `product-video-creator` ⭐⭐⭐⭐ - 商品视频创作
- `xiaohongshu-makeup` ⭐⭐⭐ - 小红书美妆内容

### 📊 PPT 与演示（6个）

- `NanoBanana-PPT-Skills` ⭐⭐⭐⭐⭐ - AI 生成 PPT 图片和视频
- `ppt-generator` ⭐⭐⭐⭐ - 智能 PPT 生成
- `pptx-generator` ⭐⭐⭐ - JSON 转 PPTX
- `nanobanana-ppt-visualizer` ⭐⭐⭐ - PPT 视觉增强
- `ppt-roadshow-generator` ⭐⭐ - PPT 路演视频
- `remotion-video-enhancer` ⭐⭐ - 视频转场动画

### 🎙️ 语音与音频（3个）

- `tts-voice-synthesis` ⭐⭐⭐⭐⭐ - 智能语音合成
- `qwen3-tts-local` ⭐⭐⭐⭐ - 本地语音合成（Edge-TTS）
- `qwen3-asr-assistant` ⭐⭐⭐⭐ - 语音转文字

### 🤖 数字人与视频配音（5个）

- `infinitetalk` ⭐⭐⭐⭐⭐ - 音频驱动视频配音
- `infinitetalk-shopping-avatar` ⭐⭐ - 小省导购员提示词
- `digital-avatar-shopping-video` ⭐⭐ - 数字人口播带货
- `dream-video-prompt-generator` ⭐⭐ - 即梦视频提示词
- `agentkit-multimedia-shopping` ⭐⭐ - 多媒体带货视频

### 📄 文档与分析（4个）

- `paper-analysis-assistant` ⭐⭐⭐⭐ - arXiv 论文分析
- `contract-review` ⭐⭐⭐ - 合同审核
- `law-to-markdown` ⭐⭐ - 法律文档转换
- `stock-analysis` ⭐⭐⭐ - 股票个股分析

### 🤝 智能体协作（3个）

- `agent-team` ⭐⭐⭐ - 智能体团队协作
- `multi-agent-meeting` ⭐⭐ - 多智能体会议
- `peers-advisory-group` ⭐⭐ - 同行顾问团

### 💼 产品与项目管理（2个）

- `product-manager-toolkit` ⭐⭐⭐ - 产品经理工具包
- `sales-ai-assistant` ⭐⭐ - 销售 AI 助手

### 🎨 设计与可视化（4个）

- `frontend-design` ⭐⭐⭐ - 前端界面设计
- `ai-drawio` ⭐⭐⭐⭐ - 流程图绘制
- `pop-up-book-illustration` ⭐⭐ - 3D 纸艺插画
- `web-to-app` ⭐⭐ - 网页转桌面应用

### 📑 文档处理（4个 - 系统内置）

- `pptx` ⭐⭐⭐⭐⭐ - PPT 文件处理
- `xlsx` ⭐⭐⭐⭐⭐ - Excel 文件处理
- `pdf` ⭐⭐⭐⭐⭐ - PDF 文件处理
- `docx` ⭐⭐⭐⭐⭐ - Word 文件处理

### 🔧 技能管理（2个 - 系统内置）

- `find-skill` ⭐⭐⭐ - 技能发现工具
- `skill-creator` ⭐⭐⭐ - 技能创建工具

### 💰 财务分析（2个）

- `creating-financial-models` ⭐⭐⭐⭐ - 财务建模套件
- `market-research-reports` ⭐⭐⭐⭐ - 市场研究报告

### 🎭 文化创作（1个）

- `poetry-music-visual` ⭐⭐ - 古诗词配图配乐

## 五星推荐技能

| 技能名 | 评分 | 说明 |
|--------|------|------|
| content-creation-publisher | ⭐⭐⭐⭐⭐ | 内容创作与发布全流程 |
| intelligent-content-system | ⭐⭐⭐⭐⭐ | 智能内容系统 |
| video-creation-suite | ⭐⭐⭐⭐⭐ | 完整视频创作套件 |
| ecommerce-full-pipeline | ⭐⭐⭐⭐⭐ | 跨境电商全链路自动化 |
| NanoBanana-PPT-Skills | ⭐⭐⭐⭐⭐ | AI 生成 PPT |
| tts-voice-synthesis | ⭐⭐⭐⭐⭐ | 智能语音合成 |
| infinitetalk | ⭐⭐⭐⭐⭐ | 音频驱动视频配音 |
| pptx | ⭐⭐⭐⭐⭐ | PPT 文件处理（系统内置） |
| xlsx | ⭐⭐⭐⭐⭐ | Excel 文件处理（系统内置） |
| pdf | ⭐⭐⭐⭐⭐ | PDF 文件处理（系统内置） |
| docx | ⭐⭐⭐⭐⭐ | Word 文件处理（系统内置） |

## 快速开始

### 1. 克隆仓库

```bash
git clone https://github.com/anbeime/skill.git
cd skill
```

### 2. 安装依赖

```bash
pip install -r requirements.txt
```

### 3. 运行更新

```bash
# 立即执行一次更新
python main.py --once

# 启动定时更新守护进程
python main.py --daemon

# 显示数据统计
python main.py --stats

# 导出为 CSV 格式
python main.py --export skills.csv

# 详细日志模式
python main.py --once -v
```

### 4. 浏览技能

访问 [在线技能商店](https://skill.vercel.app) 或查看本地文件：

```bash
# 查看官方技能列表
cat data/skills.json

# 查看本地技能列表
cat data/local_skills.json

# 查看技能文档
ls docs/
```

## 技能验证工具

内置技能验证工具，用于检查 `SKILL.md` 是否符合规范：

```bash
# 验证所有技能
python tools/skill_validator.py validate

# 验证单个技能
python tools/skill_validator.py validate skills/agent-team

# 读取技能属性
python tools/skill_validator.py read-properties skills/agent-team --json

# 生成 XML prompt（用于 AI 调用）
python tools/skill_validator.py to-prompt skills/agent-team
```

## 谁适合用这个项目？

| 使用场景 | 适合度 |
|----------|--------|
| Claude Code 日常开发，想找现成技能提升效率 | ✅ 非常适合 |
| Cursor / Cline / Codex 用户，导入外部技能 | ✅ 适合 |
| 想要搭建自己的技能库，需要一个模板 | ✅ 适合 |
| AI Agent 研究者，统计分析技能生态 | ✅ 适合 |
| 完全不懂技能是什么，想要从零了解 | ✅ 适合（文档齐全） |
| 只需要一两个特定技能，不想折腾 | ⚠️ 可以直接去 GitHub 找单个技能 |

## 我的使用体验

用了一段时间感觉最爽的几点：

1. **不用到处找了**：打开在线预览就能搜，关键词一搜就出来，比 GitHub 搜索好用
2. **更新及时**：每天自动同步，新出的技能很快就能收录进来
3. **中文技能分类清晰**：国内创作者做的垂直领域技能（电商、内容创作、小红书）都分类整理好了，不用自己翻
4. **有完整备份**：不怕作者删库，这里都有压缩包备份

## 常见问题

### Q: 这个项目和 awesome-agent-skills 是什么关系？

A: `awesome-agent-skills` 是上游源仓库，这个项目每天自动爬取同步，并额外添加了 62 个中文本地技能，做了分类整理和完整备份。

### Q: 可以直接用这些技能吗？

A: 大部分技能都有 `SKILL.md` 格式，Claude Code 可以直接加载使用。具体每个技能的使用方法看技能目录里的说明。

### Q: 怎么贡献自己的技能？

A: 欢迎提交 Issue 或者 PR。详见 [贡献指南](https://github.com/anbeime/skill/blob/main/CONTRIBUTING.md)。

- 快速提交：[创建 Issue 提交技能](https://github.com/anbeime/skill/issues/new?template=submit-skill.yml)
- PR 直接提交：fork 仓库后复制 `skills/_template/` 创建技能，验证后提 PR

### Q: 技能是免费的吗？

A: 绝大多数技能都是 MIT 或类似开源协议，具体看各个技能仓库的说明。这个项目只是做索引和备份，不改变原项目协议。

## 链接

- [GitHub 仓库](https://github.com/anbeime/skill)
- [在线演示](https://skill.vercel.app)
- [技能管理数据库](https://github.com/anbeime/skill/blob/main/docs/技能管理数据库.md)
- [Awesome Agent Skills（源仓库）](https://github.com/VoltAgent/awesome-agent-skills)

## 总结

如果你是 Claude Code / Cursor 重度用户，又懒得到处找技能，这个项目值得星标。244+ 技能，每日自动更新，分类清晰，还有完整备份，要用的时候搜一下就能直接拿走，确实能省不少时间。

> 项目地址：https://github.com/anbeime/skill
