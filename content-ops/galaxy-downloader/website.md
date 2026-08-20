# Galaxy Downloader：支持 25+ 平台的开源媒体下载器

上周我想保存小红书上一条收藏的穿搭视频，翻了好几个在线下载器，要么有水印，要么要关注公众号要钱，要么干脆解析失败。试了一圈下来发现，**最好用的方案其实是自己搭一个开源的**。

今天介绍的 [Galaxy Downloader](https://github.com/lxw15337674/galaxy-downloader) 就是这么一个项目：它支持 Bilibili、抖音、小红书、Instagram、TikTok、X、微博等 **25+ 主流平台** 的媒体内容下载，支持无水印视频、音频提取、图文打包，基于 Next.js + Cloudflare Vinext 开发，可以一键部署到 Cloudflare 的免费额度，完全自己掌控，不用担心服务跑路。

这篇文章讲清楚四件事：1）它支持哪些平台，解决了什么痛点；2）5 分钟一键部署到 Cloudflare 的完整步骤；3）我实测下来的体验和注意事项；4）二次开发的小技巧。

---

## 它解决了什么痛点？

你肯定遇到过：

- 看到好看的小红书视频/抖音短视频想保存，原平台没有下载按钮，第三方工具要么有水印要么收费
- 想把 B 站视频的音频提取出来当播客听，要转好几个工具太麻烦
- 在线下载器动不动就挂，今天能用明天就 404，想找个稳定的自己用
- 隐私顾虑：把别人分享的链接交给第三方下载站，不知道他们会拿数据做什么

Galaxy Downloader 给出的方案很简单：**全栈开源，自己部署到 Cloudflare，一分钱不用花，数据完全自己掌控**。

![Galaxy Downloader 首页界面](/images/galaxy-downloader/01-home-page.png)

## 支持哪些平台？

项目目前支持的平台列表相当全面，覆盖了大多数人常用的社交媒体：

| 平台 | 支持内容 | 说明 |
|------|----------|------|
| Bilibili | 视频、音频 | 支持分享口令解析 |
| 抖音 | 视频、图文 | **无水印**，支持分享口令 |
| 小红书 | 视频、图文 | 无水印原图/原视频下载 |
| Instagram | Reels、帖子、图文 | 支持多种链接格式 |
| TikTok | 视频 | 无水印下载 |
| X (Twitter) | 视频 | 支持推文视频下载 |
| 微信公众号 | 文章视频 | 支持多视频提取 |
| 微博 | 视频、图文 | 支持多视频提取 |
| Telegram | 视频 | 直接解析下载 |
| Threads | 视频、图文 | 支持解析 |
| Niconico | 视频 | 支持下载 |
| Vimeo/Dailymotion/Streamable/Reddit/Newgrounds/Tumblr/Pinterest/VK/OK.ru/Twitch/SoundCloud | 内容下载 | 基础支持 |

也就是说，**从国内的抖音、小红书，到国外的 Instagram、TikTok，几乎你能碰到的需要下载媒体的场景，它都覆盖到了**。

特色功能：

1. **浏览器端音频提取**：用 FFmpeg.wasm 在浏览器直接提取音频，不需要后端处理
2. **图文打包下载**：多图文章可以打包成 ZIP 一次性下载
3. **本地下载历史**：浏览器保存你的下载记录，刷新页面还在
4. **多语言支持**：简体中文、繁体中文、英文、日文开箱即用

## 5 分钟一键部署教程

项目基于 [vinext](https://github.com/cloudflare/vinext) 开发，可以一键部署到 Cloudflare Workers + Pages，完全免费额度就能跑。

### 前置准备

- 一个 Cloudflare 账号（免费注册就能用）
- Node.js 20+ 和 pnpm 包管理器

### 步骤 1：Fork 项目

先到 GitHub 项目页面点 Fork：

```
https://github.com/lxw15337674/galaxy-downloader
```

### 步骤 2：克隆到本地安装依赖

```bash
git clone https://github.com/你的用户名/galaxy-downloader.git
cd galaxy-downloader
pnpm install
```

### 步骤 3：本地测试运行

```bash
pnpm dev
```

打开浏览器访问 `http://localhost:3010` 就能看到界面了，可以先试解析一两个链接没问题再部署。

### 步骤 4：部署到 Cloudflare

项目作者已经配置好了一键部署命令：

```bash
# 先构建
pnpm build
# 再部署
pnpm deploy
```

按照提示登录 Cloudflare，等待几分钟就能完成部署。

如果你之前已经执行过 build，可以用：

```bash
pnpm deploy:ci
```

### 环境变量配置（可选但建议）

部署时建议配置几个环境变量，让 SEO 和链接跳转更正确：

| 变量名 | 说明 | 示例 |
|--------|------|------|
| `NEXT_PUBLIC_API_BASE_URL` | 公开 API 地址 | `https://your-worker-name.your-username.workers.dev` |
| `NEXT_PUBLIC_SITE_URL` | 你的站点地址 | `https://downloader.your-domain.com` |
| `SEO_INDEXABLE` | 是否允许搜索引擎索引 | `true` |

配置方式：在 Cloudflare Workers 控制台 → 设置 → 环境变量里添加即可。

## 实际使用体验

我实测了几个常用平台，说下实际感受：

### ✅ 体验不错的地方

1. **界面干净**：没有广告，没有弹窗，就是一个输入框加下载按钮，用着舒服
2. **解析速度快**：因为部署在 Cloudflare 边缘节点，国内访问速度也不错
3. **抖音无水印确实能用**：实测分享口令解析成功，下载出来的视频确实没有水印
4. **小红书图文都能下**：单图多图都能解析，原图保存，比在线工具清晰

### ⚠️ 需要注意的坑

1. **音频提取受浏览器性能限制**：项目用 FFmpeg.wasm 在浏览器端做音频提取，大文件会比较慢，太长的视频建议用桌面工具处理
2. **部分平台需要跨域处理**：因为浏览器直接请求目标站点，部分平台可能会有跨域限制，这时候需要后端 Worker 做反代，项目已经处理好了大多数情况
3. **Cloudflare 免费额度够用吗**：免费额度每天 10 万请求，个人完全够用，除非分享给几百人同时用才会超

## 适合谁自建？不适合谁？

**推荐自建：**

- 经常需要从各个平台保存媒体内容
- 讨厌第三方工具的广告、水印、关注公众号套路
- 在意隐私，不想把自己的下载记录交给第三方
- 有 Cloudflare 账号，会点简单的命令行操作

**不建议折腾：**

- 完全不会代码，连 git clone 都没听过
- 只下载一次，用完就走
- 需要下载非常大的视频文件，对速度要求极高

## 技术架构简析

这个项目的技术选型挺有意思的：

- **前端**：Next.js 16 + React 19 + TypeScript + Tailwind CSS + shadcn/ui，现代化栈，代码结构清晰
- **后端**：Cloudflare Workers，无服务器架构，免费额度够用
- **音频处理**：FFmpeg.wasm 完全浏览器端处理，不用后端算
- **打包**：JSZip 浏览器端打包图文，也不用后端参与

整个项目除了静态页面托管在 Cloudflare Pages，API 路由跑在 Workers 上，**全部运行在边缘节点，没有服务器费用**，这个架构对于个人工具类项目来说太合适了。

## 总结

Galaxy Downloader 是一个完成度很高的开源项目，解决了一个很多人都有的痛点：**各个平台媒体下载难**。比起各种在线工具，自建一个的好处是：

- 永久可用，不用担心服务跑路
- 完全免费，没有功能限制
- 隐私保护，你的下载记录只在你自己浏览器里
- 可以自己改代码，加功能，定制属于自己的下载器

如果你最近也被第三方下载器搞烦了，不妨花 5 分钟搭一个自己的：

**项目地址：** https://github.com/lxw15337674/galaxy-downloader

作者已经在 `galaxy-downloader.bhwa233.com` 部署了在线版本，可以先去试试好不好用再决定要不要自建。
