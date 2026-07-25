# 完全本地运行，开源免费！浏览器里的AI视频编辑器 Timeline Studio

Timeline Studio 是一个本地优先、直接运行在浏览器中的AI视频编辑器。它把接近剪映的多轨时间线剪辑，与浏览器AI配音、自动字幕、智能裁切、数字人结合在一起，所有AI推理都在本地完成，视频不需要上传到云端。支持 Claude Code / Codex AI Agent 自动化剪辑，MIT协议免费商用。

> **TL;DR**：Timeline Studio 适合在意隐私、不想交剪映会员费、需要简单AI剪辑的用户和AI Agent玩家；不适合需要专业复杂剪辑的专业用户。核心优势是完全本地运行、AI功能齐全免费开源，核心限制是浏览器渲染性能不如原生客户端。

## 项目简介

云端AI剪辑现在越来越流行，但始终有几个痛点绕不开：

1. 视频必须上传，隐私没法保证
2. 基本功能就要收月费，商业用途还得买高级授权
3. 客户端几个G，剪个1分钟短视频也要打开大软件

Timeline Studio 给出了完全不同的解决方案 —— 把整个AI视频编辑器搬到浏览器里，AI模型全部本地运行，你的视频永远不需要离开你的电脑。

![Timeline Studio 编辑器界面](editor-timeline.png)

## 核心功能

### AI 能力

| 功能 | 技术方案 | 特点 |
|------|----------|------|
| AI配音 | 中文 Piper/VITS ONNX，英文 Kokoro 82M | 本地运行，不按字数收费 |
| 自动字幕 | Whisper small q8 ONNX | 中文识别做了置信度修正 |
| 智能裁切 | YOLOS tiny 主体检测 | 自动保证主体不被裁切 |
| 人像抠图 | MODNet | 移除背景方便做合成 |
| 人声分离 | 浏览器端分离算法 | 提取伴奏放音乐轨 |
| 数字人 | JoyVASA + LivePortrait + WebGPU | 音频驱动表情动作 |

### 剪辑功能

- 主视频轨 + 字幕/配音/背景音乐独立时间轨
- 画布直接操作：移动、缩放、旋转、遮罩
- 关键帧动画、滤镜效果、调速
- 磁吸对齐、切分/复制/删除、撤销重做
- 导出：WebCodecs 生成 MP4，支持字幕、画中画、效果合成
- 支持PWA安装，离线可用

### AI Agent 自动化剪辑（特色功能）

最创新的地方是对 AI Agents 友好。提供官方 Skill，让 Claude Code / Codex 可以：

1. 读取现有的 `.timeline` 项目文件
2. 根据文字描述生成编辑计划
3. 验证编辑计划合法性
4. 执行编辑操作
5. 保存修改后的项目文件
6. 最终渲染导出MP4

示例命令：

```bash
# 安装 Skill
npx skills add MartinDelophy/ai-video-editor --skill edit-timeline-studio

# 检查项目信息
npm run agent -- project.inspect my-project.timeline

# 执行编辑计划
npm run agent -- project.run edit-plan.json

# 渲染输出
npm run agent -- project.render render-request.json
```

这种「人描述需求，AI执行剪辑，人最后验收」的工作流，对于批量短视频制作场景打开了很多想象空间。

## 优势对比

| 优势 | 劣势 |
|------|------|
| 完全本地运行，隐私有保障 | 浏览器渲染，大视频导出比原生客户端慢 |
| 所有AI功能免费，MIT协议商业可用 | 复杂剪辑功能不全，不如剪映丰富 |
| 不用安装客户端，打开浏览器就能用 | 第一次加载模型需要时间 |
| 支持PWA安装到本地，离线可用 | WebGPU 加速对浏览器版本有要求 |
| AI Agent 原生支持自动化 | 社区还小，中文资料不多 |

## 适合人群对照表

| 适合使用 | 不建议使用 |
|----------|------------|
| 在意隐私，不想把视频上传云端 | 需要专业复杂剪辑的影视从业者 |
| 不想交剪映会员费，偶尔剪短视频 | 完全不会代码，想要开箱即用成熟产品 |
| AI Agent 玩家，想试试自动化剪辑 | 需要处理十几分钟以上的长视频 |
| 开发者想二次开发定制自己的编辑器 | 电脑性能很差，没有WebGPU支持 |

## 快速开始

**在线体验：** [https://video-editor.ai-creator.top/](https://video-editor.ai-creator.top/)

**本地部署：**

```bash
git clone https://github.com/MartinDelophy/ai-video-editor.git
cd ai-video-editor
npm install
npm run dev
```

打开终端输出的本地地址即可使用。

## 实测总结

Timeline Studio 现在算不上能完全替代剪映，但它证明了一件事：**完整的AI视频编辑器完全可以跑在浏览器里，完全本地化，完全免费**。

这个方向本身就很值得关注。对于普通用户来说，多了一个免费隐私的选择；对于开发者来说，这是一个很好的基础可以二次定制；对于AI Agent领域来说，这是第一个真正把自动化剪辑落地的开源项目。

如果你最近也在找开源视频编辑方案，可以去试试：

**GitHub 地址：** [https://github.com/MartinDelophy/ai-video-editor](https://github.com/MartinDelophy/ai-video-editor)

---

如果你决定尝试，我建议按这个顺序：
1. 先打开在线版体验基本功能，看交互是否符合你的习惯
2. 如果好用，再克隆到本地部署
3. AI Agent 玩家可以直接装上 Skill 试试自动化剪辑
