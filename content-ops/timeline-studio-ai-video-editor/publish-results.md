# 发布结果记录

## Timeline Studio: 浏览器开源AI视频编辑器

创建时间：2026-07-25

---

### 1. Website / Blog

- **文章路径**: `content/articles/2026/07/25/timeline-studio-ai-video-editor.md`
- **静态图片**: `static/images/timeline-studio-ai-video-editor/` (7张截图)
- **Git commit**: `aa595d0`
- **状态**: ✓ 已提交到本地Git仓库

---

### 2. WeChat 公众号草稿

- **标题**: 用了半年剪映后，我发现这个开源项目能在浏览器里本地剪AI视频
- **封面**: `content-ops/timeline-studio-ai-video-editor/media/cover-wechat.jpg` (需要生成)
- **正文图片**: 7张，均为本地绝对路径
- **状态**: ⏳ 待上传（需要WeChat AppID/Secret配置后执行上传命令）

上传命令：
```bash
node /root/.hermes/skills/openclaw-imports/wechat-toolkit/scripts/publisher/publish.js /root/blog/content-ops/timeline-studio-ai-video-editor/wechat-upload.md newsroom github
```

---

### 3. Zhihu 专栏草稿

- **标题**: Timeline Studio 开源浏览器AI视频编辑器值得用吗？我的实测结论
- **上传模式**: Mode B (`--markdown-file --upload-images`)
- **正文图片**: 7张，均在本地 `content-ops/timeline-studio-ai-video-editor/media/`
- **紧凑HTML**: `content-ops/timeline-studio-ai-video-editor/zhihu-compact.html` (3741 字符)
- **状态**: ⏳ 待上传

上传命令：
```bash
python3 /root/.hermes/skills/social-media/zhihu-answer-workflow/scripts/zhihu_draft.py --cache-dir /tmp/zhihu-cache column \
  --title "Timeline Studio 开源浏览器AI视频编辑器值得用吗？我的实测结论" \
  --markdown-file /root/blog/content-ops/timeline-studio-ai-video-editor/zhihu.md \
  --upload-images
```

### 知乎封面（需手动关联，30 秒）
- 编辑链接：（上传后获取）
- 封面 CDN URL：（上传后获取）
- 本地封面：需要生成 `content-ops/timeline-studio-ai-video-editor/media/cover-zhihu.png`
- 操作：点"添加封面" → 粘贴 CDN URL 或上传本地文件 → 保存

---

## 包结构

```
/root/blog/
├── content/articles/2026/07/25/timeline-studio-ai-video-editor.md  # Website
├── content-ops/timeline-studio-ai-video-editor/
│   ├── titles.md                          # 候选标题
│   ├── website.md                         # Website 完整版本
│   ├── wechat.md                          # WeChat 版本
│   ├── wechat-upload.md                   # WeChat 上传版本
│   ├── zhihu.md                           # Zhihu Markdown 版本
│   ├── zhihu-compact.html                 # Zhihu 紧凑 HTML
│   ├── build_zhihu_html.py                # HTML 构建脚本
│   ├── publish-results.md                 # 此文件
│   └── media/                             # 截图
└── static/images/timeline-studio-ai-video-editor/  # Website 静态图
```

---

## 选题总结

- 项目亮点：完全本地浏览器运行、AI功能齐全、免费开源MIT协议、支持AI Agent自动化剪辑
- 差异化对比：对比剪映等云端闭源产品，隐私保护更好，完全免费，适合开发者和在意隐私的用户
- 适合三端推广，项目技术方向有创新性，AI+本地编辑是明确的用户痛点
