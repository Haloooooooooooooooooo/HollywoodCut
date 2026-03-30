# Hollywood Cut (Jazz & Western Edition) 🎬

一款高质感的**电影幕后片场照 (Behind-The-Scenes) 生成工具**。基于 Google Gemini Pro 多模态大语言模型打造，采用**单页零构建 (Zero-Build SPA)** 架构，主打即插即用的无服务器特性。

## ✨ 核心特性 / Features

- **Klein Blue Jazz Western (克莱因蓝爵士西部)** 独立视觉系统。
- **纯粹单页应用 (Single-File App)**: 无需 Webpack/Vite 等任何构建工具配置，极简接入。
- **原生依赖 (ES Modules / CDN)**: React 18 模块化支持，Tailwind CSS 极速渲染。
- **动态胶片感指令**: 针对人像摄影内置 100% 结构级重塑的导演级防崩溃 Prompt 逻辑库。

## 🔐 隐私与安全说明 / Privacy & Security

本应用严格坚守隐私协议：
* **无硬编码**: 前端源码中 **不会包含任何 API Keys**。
* **本地存储**: 所有的认证信息 (`gemini_api_key`) 仅存储于用户当前浏览器的 `localStorage`，不会以任何形式暴露或上传至其他第三方。
* 严禁将 `.env` 文件或包含 Key 的环境文档 Push 到云端（已通过 `.gitignore` 预防）。

## ⚙️ 工作流及配置说明 / Deployment Workflow

### 本地部署 (Local Setup)

由于采用绝对的 Zero-Build 架构，部署流程极为简单：

1. 克隆本项目：
   ```bash
   git clone https://github.com/Haloooooooooooooooooo/HollywoodCut.git
   cd HollywoodCut
   ```

2. 开启本地服务即可体验：
   (例如：在根目录开启基于 Python 的简单服务器)
   ```bash
   python -m http.server 8080
   ```
   随后在浏览器访问 `http://localhost:8080` 即可加载。

### 环境参数指引 (Environment Parameters)

请参考根目录的 `.env.example` 文件。当前的架构模式中并不直接解析 `.env` 文件。
当用户首次打开应用，会自动显示【导演控制台通行证】UI，在这个 UI 卡片中输入的：
*   **Gemini API Key** 必须由 `Google AI Studio` 正式提供 (包含对 `gemini-1.5-flash` 和 `gemini-3-pro-image-preview` 等多模态/生成模型的调用权限)。

## 🚀 项目规划进度 (Roadmap)

- [x] Phase 1: Foundation & Design - Tailwind/Framer Motion 接入与克莱因视觉底板。
- [x] Phase 2: State & Auth - `localStorage` API Key 权限控制与前端拦截器。
- [x] Phase 3: Main UI Shell - 双栏响应式导演控制台与多状态监视器搭建。
- [x] Phase 4: Core Service Layer - SiliconFlow SDXL 2.0 逻辑接通，打通图生图/海报抓取全链路。

---
*Built with React 18 & Google Gemini API. Created in 2026.*
