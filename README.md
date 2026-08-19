# AI 图像智能重构 Skill（专业摄影版） / AI Image Intelligent Reconstruction Skill (Pro Photography Edition)

一个可直接安装运行的图像处理 Skill，以顶级摄影师审美为基准，专注于基于原图的 AI 智能风格重构。严格保留原图核心元素与像素级清晰度，避免 AI 幻觉与画质劣化。

A directly installable and runnable image processing Skill, benchmarked against top commercial photography aesthetics, focusing on AI-powered intelligent style reconstruction based on the original image. Strictly preserves key elements and pixel-level sharpness, avoiding AI hallucinations and quality degradation.

## ✨ 功能特性 / ✨ Features

### 专业摄影级智能重构 / Professional Photography-Grade Intelligent Reconstruction
- 基于原图主体、构图、光影、色调、景深、视角进行风格化重构  
  Style reconstruction based on subject, composition, lighting, tones, DoF, and perspective
- 三档重构强度可调：**保守 / 中等 / 激进**  
  3 intensity levels: Conservative / Medium / Aggressive
- 元素锁定机制，防止 AI 幻觉（不新增/删除关键元素）  
  Element locking to prevent AI hallucination (no addition/deletion of key elements)
- 支持用户自定义风格意向描述  
  Custom style description supported

### 画幅与视角调整（需确认） / Aspect Ratio & Angle Adjustment (Requires Confirmation)
- 支持画幅比例互转（3:4↔1:1、16:9↔4:3 等），基于元素分布推理最佳裁切/扩展区域  
  Supports conversion between aspect ratios (3:4↔1:1, 16:9↔4:3, etc.), inferring optimal crop/expand areas based on element distribution
- 支持拍摄视角位置调整（仰俯角、视线位移、机位平移），基于透视关系推理合理空间布局  
  Supports adjustment of shooting angle (tilt/pitch, sight-line shift, camera pan), inferring logical spatial layout from perspective
- **调整必确认**：AI 提供具体调整方案预览，用户确认后才执行，拒绝则跳过  
  **Confirmation required**: AI provides a preview of the adjustment plan, and proceeds only after user confirmation; skipped if rejected

### 像素级保真约束 / Pixel-Level Fidelity Constraints
- 清晰度以原图为唯一基准，禁止锐化/模糊/降噪/纹理增强  
  Sharpness uses the original image as the sole benchmark; sharpening/blurring/denoising/texture enhancement prohibited
- 文字/标识区域锁定原始像素，禁止重绘失真  
  Text/logo areas have original pixels locked; redrawing causing distortion is forbidden
- 输出无锯齿、无伪影、无重影、无杂色、无紫边、无晕影  
  Output is free of aliasing, artifacts, ghosting, color noise, purple fringing, and vignetting
- 保真优先级高于风格化，冲突时自动降级  
  Fidelity takes priority over stylization; auto-downgrades when in conflict

### 双重合规审核 / Dual Compliance Review
- 前置文本审核 + 后置视觉审核  
  Pre-text review + post-visual review
- 主动规避版权、肖像、商标侵权风险  
  Proactively avoids copyright, portrait, and trademark infringement risks

## 安装方法 / Installation

### 方法一：直接导入 Skill 文件  
Method 1: Directly import the Skill file
将本仓库中的 `skill.md` 文件导入你的 AI Agent/平台即可运行。

Import the `skill.md` file from this repository into your AI Agent/platform to run it.

### 方法二：克隆仓库  
Method 2: Clone the repository
```bash
git clone https://github.com/jasonofchina/ai-image-reconstruct.git
