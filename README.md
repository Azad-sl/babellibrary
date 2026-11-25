# The Library of Babel (巴别图书馆)

An interactive 3D Library of Babel built with Three.js / WebGL.

**中文** | [English](#english)

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

---

<a id="english"></a>

# The Library of Babel

An interactive 3D Library of Babel built with Three.js / WebGL.

[中文](#the-library-of-babel-巴别图书馆) | **English**

🔗 **Live Demo**: [The Library of Babel](https://babellibrary.azad.asia/)

## 📖 About

A tribute to Jorge Luis Borges' *The Library of Babel*. In the endless hexagonal galleries, every book is gibberish — random strings of letters and punctuation. Drag to look around, scroll to move closer, and click any floating volume to open and leaf through it.

**Hidden easter egg**: among the sea of gibberish, one book is written in real language — an English translation of Borges' original story.

## ✨ Features

- 🏛️ **Hexagonal galleries**: an infinite book wall rendered with InstancedMesh, with drifting dust, light shafts and breathing lamps
- 📚 **Take a volume**: click any floating book to open the two-page reader, with page turning
- 🌐 **Bilingual UI**: switch between Chinese and English in one click; initial language is detected from the local time zone and remembered locally
- 📊 **About panel**: an in-app preface with a reading counter, honoring Borges
- 📱 **PWA**: installable to the home screen (manifest + Service Worker) with a full-screen app experience
- 📴 **Offline-ready**: all static assets are cached — the library works without a network
- ⚡ **Adaptive quality**: desktop gets depth-of-field + bloom post-processing; devices that keep failing the frame-rate check automatically fall back to native rendering
- 🅰️ **Kangxi font subsetting**: the full 6.3 MB dictionary font trimmed to 105 KB (woff2), bundling only the glyphs the page actually uses

## 🛠️ Tech Stack

- Three.js 0.167 / WebGL (EffectComposer with Bokeh DoF, UnrealBloom, FXAA)
- Vanilla HTML / CSS / JavaScript (ES Module — no framework, no build step)
- Instanced 3D rendering (InstancedMesh)
- fonttools font subsetting
- Service Worker / Web App Manifest

## 🚀 Run Locally

Open `index.html` directly in a browser, or serve it locally:

```bash
npx serve
```

> Offline caching and "Add to Home Screen" require an `https://` or `localhost` environment.

## 📦 Deployment

A single static page — any static host works (this project runs on Tencent Cloud EdgeOne Pages, auto-deployed from the GitHub repo):

1. Fork or clone this repository
2. Import the repo into EdgeOne Pages (or Vercel / Cloudflare Pages, etc.)
3. No build command needed — use the repo root as the publish directory

## 🗂️ Project Structure

```
├── index.html            # The page itself (inline styles & scripts)
├── three-bundle.js       # three.js + post-processing addons bundled by esbuild
├── Kangxi-subset.woff2   # Kangxi dictionary font subset (simplified codepoints → traditional glyphs)
├── sw.js                 # Service Worker (cache version: babel-v2)
├── manifest.webmanifest  # PWA install manifest
├── favicon.ico / favicon-96.png / icon-*.png / apple-touch-icon.png
└── og-cover.png          # Social sharing cover image
```

## 📝 Notes

- No external CDN dependencies — the 3D engine and fonts are fully self-contained, accessible from mainland China without a proxy
- No data collection; the only stored state is the reading counter (in `localStorage`)
- After updating `three-bundle.js` or the font, bump the cache version in `sw.js` (`babel-v2`) so client caches refresh
