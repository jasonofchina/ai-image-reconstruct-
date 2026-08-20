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

### 参考图身份保持 / Reference-Image Identity Preservation
- 精选 2–4 张参考图，防止主体被"认错/换脸"  
  Curated 2–4 reference images to prevent the subject from being misidentified or face-swapped
- 身份声明 + 禁止冗长面部描述，避免合成"相似但不同"的新面孔  
  Identity declaration + no verbose facial descriptions, to avoid synthesizing a new, similar-looking face
- 反过度美化：拒绝网红脸、过度磨皮、商业旅拍感  
  Anti-beautification: reject influencer face, over-smoothing, commercial travel-shoot feel

### 双重合规审核 / Dual Compliance Review
- 前置文本审核 + 后置视觉审核  
  Pre-text review + post-visual review
- 主动规避版权、肖像、商标侵权风险  
  Proactively avoids copyright, portrait, and trademark infringement risks

### 生图执行方式三选一 / Three Generation Execution Methods
- **方式一 · Agent 内置生图**：直接调用平台内置生图接口，最省心  
  **Method 1 · Agent built-in generation**: directly calls the platform's built-in generation API, most hassle-free
- **方式二 · 外接 API**：用户提供 Key，Agent 调用外接生图接口（单次授权、用完即焚、多供应商适配）  
  **Method 2 · External API**: user provides a key, Agent calls an external generation API (single-use authorization, burn after use, multi-provider adaptation)
- **方式三 · 返回完整 Prompt**：六要素结构化 + 按目标工具适配语法（Midjourney / DALL·E / SD / 即梦等）  
  **Method 3 · Return a complete prompt**: six-element structure + tool-specific syntax (Midjourney / DALL·E / SD / Jimeng, etc.)

## 安装方法 / Installation

### 方法一：直接导入 Skill 文件  
Method 1: Directly import the Skill file
将本仓库中的 `skill.md` 文件导入你的 AI Agent/平台即可运行。

Import the `skill.md` file from this repository into your AI Agent/platform to run it.

### 方法二：克隆仓库  
Method 2: Clone the repository
```bash
git clone https://github.com/jasonofchina/ai-image-reconstruct-.git
```

## 使用方法 / How to Use

### 触发条件 / Trigger Conditions
上传图片后，输入以下关键词之一即可触发：  
After uploading an image, enter any of the following keywords to trigger:
`重构`、`重绘`、`风格化`、`重新生成`、`reconstruct`、`style transfer`

### 示例指令 / Example Commands
```
重构，电影感青橙色调，改为1:1画幅，视线上移，中等强度
Reconstruct, cinematic teal-orange tone, change to 1:1 aspect ratio, elevate sight line, medium strength
```

### 生图方式选择 / Choosing a Generation Method
每次任务开始前，Agent 会询问本次采用哪种生图方式：  
Before each task, the Agent will ask which generation method to use:

> 1. Agent 直接调用内置生图接口（推荐）
> 2. 我提供 API Key，由 Agent 调用外接生图接口（仅本次有效）
> 3. 返回完整 Prompt，我自己拿去生图工具里用（需告知目标工具）

## 输入规范 / Input Specifications

| 项目 / Item         | 要求 / Requirement                              |
|---------------------|--------------------------------------------------|
| 图片格式 / Format   | JPG、JPEG、PNG                                   |
| RAW 格式            | 不支持直传，需先转换为 JPG/PNG                    |
| 建议分辨率 / Resolution | 长边 1024px ~ 4096px                          |
| 文件大小 / Size     | 单张 ≤ 20MB                                      |

## ⚙️ 依赖能力 / Required Capabilities

本 Skill 正常运行依赖以下能力：  
This Skill requires the following capabilities to run normally:

- `image_input`：接收用户上传图片 / Receive user-uploaded images
- `image_generation`：执行图像重构（方式一/方式二需要；方式三不需要）/ Perform image reconstruction (needed for Method 1/2; not needed for Method 3)
- `vision_analysis`：原图理解、保真校验、元素推理 / Original image understanding, fidelity validation, element inference
- `web_search`：联网核实合规与侵权风险 / Verify compliance and infringement risks online

## 测试用例 / Test Cases

详见 examples/example_reconstruct.md  
See examples/example_reconstruct.md

## 合规与安全 / Compliance & Safety

- 所有处理必须以原图为基础，禁止无中生有  
  All processing must be based on the original image; nothing can be generated from scratch
- 严格锁定核心元素，避免 AI 幻觉  
  Core elements are strictly locked; AI hallucinations are prevented
- 画幅/视角调整必须经用户确认  
  Aspect ratio/angle adjustments must be confirmed by the user
- 双重审核机制确保输出合法合规  
  Dual review mechanisms ensure legal and compliant output
- 拦截、降级或跳过调整时均会向用户说明原因  
  Reasons for interception, downgrade, or skipping adjustments are explained to the user
- **密钥安全**：外接 API Key 仅单次授权使用，用完立即删除，绝不存储、记录或二次复用  
  **Key security**: external API keys are authorized for single use only, deleted immediately after use, never stored, logged, or reused

## 参考与致谢 / References & Attribution

本 Skill 在以下方面借鉴了开源项目的设计理念（均经重新表达，符合其 MIT 许可）：  
This Skill adapts design concepts from the following open-source projects (re-expressed in our own words, under their MIT licenses):

- **多供应商 API 适配、参考图身份保持、密钥环境变量管理** / Multi-provider API adaptation, reference-image identity preservation, key env-var management：参考 [JimLiu/baoyu-skills](https://github.com/JimLiu/baoyu-skills)（MIT License）
- **Prompt 六要素结构化、多工具语法差异、负面提示词与陷阱规避** / Six-element prompt structure, multi-tool syntax, negative prompts, pitfall avoidance：参考 `image-prompt`（gokulb20/Crewm8，MIT License）

## 版本记录 / Version History

见 CHANGELOG.md  
See CHANGELOG.md

## 许可证 / License

本项目采用 MIT License 开源。  
This project is open-sourced under the MIT License.
