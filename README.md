# The Library of Babel (巴别图书馆)

An interactive 3D Library of Babel built with Three.js / WebGL.

🔗 **Live Demo**: [The Library of Babel](https://babellibrary.azad.asia/)

<img width="880" alt="image" src="https://github.com/user-attachments/assets/db054546-2d48-4f69-871b-907408cc03c8" />

## 📖 简介

此项目致敬博尔赫斯《巴别图书馆》。在无尽的六角形回廊中，所有的书都是由随机字母拼合而成的乱码（天书）。你可以通过鼠标拖拽环视、滚轮推拉，并点击漂浮的书籍进行翻阅。

**隐藏彩蛋**：在漫天乱码中，藏着一本用真实语言写成的书（博尔赫斯的原著英译本）。

## ✨ 特性

- 🏛️ **六角回廊**：实例化渲染（InstancedMesh）的无限书墙，随书架延伸的尘埃光柱与灯影呼吸
- 📚 **取卷翻阅**：点击任意浮动书籍即可展开双页阅读，支持前后翻页
- 🌐 **中英双语**：一键切换语言，自动按本地时区判定初始语言，偏好本地记忆
- 📊 **馆志**：内置项目缘起与阅读计数，向博尔赫斯致敬的题记
- 📱 **PWA**：可安装到主屏幕（manifest + Service Worker），全屏 App 体验
- 📴 **离线可用**：静态资源全量缓存，断网也能进馆
- ⚡ **自适应画质**：桌面端启用景深 + 泛光后期，帧率持续过低的设备自动回退原生渲染
- 🅰️ **康熙字体子集**：6.3 MB 全量字体裁剪至 105 KB（woff2），仅打包页面实际用到的字符

## 🛠️ 技术栈

- Three.js 0.167 / WebGL（EffectComposer 景深、UnrealBloom、FXAA 后期链）
- 原生 HTML / CSS / JavaScript（ES Module，零框架、零构建依赖）
- 3D 实例化渲染 (InstancedMesh)
- fonttools 字体子集化
- Service Worker / Web App Manifest

## 🚀 本地运行

直接双击打开 `index.html` 即可，或者使用本地服务器：

```bash
npx serve
```

> 离线缓存与"添加到主屏幕"需要 `https://` 或 `localhost` 环境才会生效。

## 📦 部署

静态单页，任意静态托管均可（本项目部署于腾讯云 EdgeOne Pages，由 GitHub 仓库自动构建）：

1. Fork 或克隆本仓库
2. 在 EdgeOne Pages（或 Vercel / Cloudflare Pages 等）导入仓库
3. 无需构建命令，直接以仓库根目录作为发布目录

## 🗂️ 目录结构

```
├── index.html            # 页面本体（内联样式与脚本）
├── three-bundle.js       # three.js + 后期插件的 esbuild 单文件打包
├── Kangxi-subset.woff2   # 康熙字典体子集（简体码位 → 繁体字形）
├── sw.js                 # Service Worker（缓存版本号 babel-v2）
├── manifest.webmanifest  # PWA 安装清单
├── favicon.ico / favicon-96.png / icon-*.png / apple-touch-icon.png
└── og-cover.png          # 社交分享卡片封面
```

## 📝 说明

- 页面不依赖任何外部 CDN，三维引擎与字体全部自包含，国内网络可直连访问
- 不采集任何数据，唯一的本地记录是阅读卷数（存于 `localStorage`）
- 更新 `three-bundle.js` 或字体后，请将 `sw.js` 中的缓存版本号 `babel-v2` 递增，用户端缓存才会刷新
