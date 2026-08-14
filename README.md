# ai-image-reconstruct-
Comprehensively focus on intelligent reconfiguration of a single core capability, reconfigure the entire processing flow based on professional photographer aesthetic standards, support capabilities such as frame/angle adjustment, and confirm the mechanism and pixel-level fidelity constraints.全面聚焦智能重构单一核心能力，以专业摄影师审美重构处理流程，支持画幅/视角调整等能力，并确认机制与像素级保真约束。

AI 图像智能重构 Skill（专业摄影版）
一个可直接安装运行的图像处理 Skill，以顶级摄影师审美为基准，专注于基于原图的 AI 智能风格重构。严格保留原图核心元素与像素级清晰度，避免 AI 幻觉与画质劣化。

##功能特性：

### 专业摄影级智能重构
  基于原图主体、构图、光影、色调、景深、视角进行风格化重构
  三档重构强度可调：保守 / 中等 / 激进
  元素锁定机制，防止 AI 幻觉（不新增/删除关键元素）
  支持用户自定义风格意向描述

### 画幅与视角调整（需确认）
  支持画幅比例互转（3:4↔1:1、16:9↔4:3 等），基于元素分布推理最佳裁切/扩展区域
  支持拍摄视角位置调整（仰俯角、视线位移、机位平移），基于透视关系推理合理空间布局
  调整必确认：AI 提供具体调整方案预览，用户确认后才执行，拒绝则跳过

##像素级保真约束
  清晰度以原图为唯一基准，禁止锐化/模糊/降噪/纹理增强
  文字/标识区域锁定原始像素，禁止重绘失真
  输出无锯齿、无伪影、无重影、无杂色、无紫边、无晕影
  保真优先级高于风格化，冲突时自动降级

### 双重合规审核
  前置文本审核 + 后置视觉审核
  主动规避版权、肖像、商标侵权风险

## 安装方法:
方法一：直接导入 Skill 文件
将本仓库中的 'skill.md' 文件导入你的 AI Agent/平台即可运行。
方法二：克隆仓库

