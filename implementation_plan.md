# 执行计划: Hollywood Cut (Jazz & Western Edition) v2.0

基于您提供的 PRD 2.0 规范，我制定了以下分阶段的执行计划。该计划旨在以**零构建工具 (ESM/CDN)** 为基础，通过递进式开发，实现一个高鲁棒性、高还原度的单页应用。

## 阶段一：基础骨架与设计系统设定 (Foundation & Design)
本阶段目标为搭建项目外壳，并注入 PRD 要求的视觉规范。

*   **1.1 核心依赖引入**:
    *   在 `index.html` 中引入 Tailwind CSS, React 19, DOM, Babel, Framer Motion, Lucide 及 Google GenAI SDK。
*   **1.2 字体加载**:
    *   引入 Google Fonts: `Inter`, `Playfair Display`, `Rye`。
*   **1.3 配置 Tailwind 主题**:
    *   定义颜色变量：`klein-blue` (#002FA7), `sunset-orange` (#FF4500), `warm-paper` (#FAF9F6), `saddle-brown` (#8B4513)。
    *   定义字体变量家族 (`cinematic`, `western`, `ui`, `mono`)。
*   **1.4 基础样式与动画**:
    *   实现 CSS `folded-paper` (信纸折角) 效果。
    *   编写背景装饰层 (`#atmosphere`) 漂浮元素的动画帧。

## 阶段二：应用状态与认证模块 (State & Auth)
本阶段目标为实现会话管理和欢迎页。

*   **2.1 React 根组件搭建**:
    *   初始化状态: `apiKey`, `isAuth` (读取 localStorage)。
*   **2.2 欢迎页 (Auth Screen) 构建**:
    *   居中对齐卡片布局 (`border-4 border-klein`)。
    *   电影质感斜体标题 (Playfair Display)。
    *   场记板 (Clapperboard) 图标。
    *   "进入电影片场" 按钮逻辑实现，校验并保存 Key。

## 阶段三：主界面响应式布局 (Main UI Shell)
本阶段目标为构建双栏主操作区。

*   **3.1 头部与页脚 (Header & Footer)**:
    *   "Hollywood Cut" 标题排版及 Reset 按钮。
    *   页脚固定底部及相关装饰文案。
*   **3.2 左侧：导演控制台 (Director Controls)**:
    *   **文件上传**: 虚线交互框及 `FileReader` 预览支持。
    *   **场景参数**: 电影名称输入框及 1.2s 防抖触发预留；长宽比 (Ratio) 和景深 (DOF) 的单选状态按钮组 (`grid-cols-2` & `grid-cols-3`)。
    *   **Prompt 监视域**: 带有折角效果的文本框，监听状态自动拼接。
*   **3.3 右侧：监视器 (Monitor)**:
    *   主显示框构建 (`aspect-[16/10]`)。
    *   空状态 "NO SIGNAL" (`Rye` 字体) 排版。

## 阶段四：AI 服务集成 (Service Layer)
本阶段是项目的核心，对接 Gemini API 逻辑。

*   **4.1 Prompt 工程装载**:
    *   实现 `PROMPT_TEMPLATE` 核心文本。
*   **4.2 背景海报联想 (Atmosphere Effect)**:
    *   实现防抖逻辑：当电影名输入停止 1.2 秒后，调用 `gemini-2.5-flash` 根据片名生成印象图片，作为页面底层背景 (`Mix-blend: multiply`)。
*   **4.3 图像生成 (generateSetPhoto)**:
    *   构建 Base64 传递逻辑，调用 `gemini-3-pro-image-preview`。
    *   处理加载状态 (自定义脉冲动画) 与错误回退。
*   **4.4 修图模块与画廊 (Gallery & Magic Edit)**:
    *   (仅在有生成结果后呈现)
    *   缩略图展示逻辑。
    *   实现 "APPLY CUT" 修图调用 (`gemini-2.5-flash-image`)。

## 阶段五：联调测试与修饰 (Polish & Delivery)
*   **5.1 鲁棒性测试**: 测试 API Key 无效或模型不可用时的全屏容错反馈。
*   **5.2 动画优化**: 利用 `framer-motion` 为页面切换 (认证页 -> 主页) 和状态转变添加微动效。
*   **5.3 发布交付**: 确保单一文件 `index.html` 能够自包含所有的逻辑与样式。
