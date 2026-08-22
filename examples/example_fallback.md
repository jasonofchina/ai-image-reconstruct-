# 平台降级适配示例 / Platform Fallback Examples

> 本文件演示 v1.4.0 起内置的「平台适配与能力自检」在不同能力缺失场景下的实际降级行为。
> This file demonstrates how the built-in "Platform Adaptation & Capability Self-Check" (since v1.4.0) actually degrades under different missing-capability scenarios.

---

## 场景一：平台无 image_generation（只能返回 Prompt）/ Scenario 1: No image_generation (Prompt Only)

**环境 / Environment**：提示词型智能体，能收图（有 `image_input`+`vision_analysis`），但无内置生图能力。

**用户输入 / User**：上传一张人像图，输入「重构，日系清新色调，中等强度」

**Agent 正确响应 / Correct Response**：

> 我看到你想把这张人像重构为日系清新风格。需要说明：**我当前平台无法直接生成图像**，但我可以为你生成一份完整、可直接粘贴使用的 Prompt，你拿到支持生图的工具（如即梦、Midjourney、ChatGPT 生图）里就能一键生成。
>
> 【完整 Prompt】
> 主体：保持原图人物不变，年轻女性，齐肩短发，白色衬衫；构图 3:4 竖版，人物居中留白；视角平视不变；光影柔和的自然光，明暗比 1:2，面部高光柔和；色调偏日系清新，色相轻微偏青，饱和度 -10%，白平衡略冷，肤色保护；景深浅，背景虚化过渡自然，轻微柔光；重构强度：中等（允许色调/光影/氛围调整，禁止改变人物五官、发型、服装、背景主体结构）；保真约束：禁止新增/删除/替换元素，文字与标识保持原样，禁止锐化/模糊/降噪，无伪影/锯齿/紫边；负面提示词：畸形、多手多指、文字乱码、伪影、低清晰度、面部变形。

**验证点 / Checkpoints**：
- ✅ Agent 明确告知"无法生图"而非假装生成
- ✅ 主动降级到方式三，并询问目标工具
- ✅ Prompt 完整包含六要素 + 保真约束 + 负面提示词

---

## 场景二：平台无 image_input（转纯文本出图）/ Scenario 2: No image_input (Text-Only)

**环境 / Environment**：纯对话模型，无图片相关能力。

**用户输入 / User**：直接发一张图（平台无法接收），说「帮我重构这张图」

**Agent 正确响应 / Correct Response**：

> 抱歉，**我当前平台无法接收图片**，所以无法基于你上传的原图做重构。不过如果你告诉我画面内容（主体是什么、什么风格），我可以帮你生成一份出图 Prompt，你拿去做图；或者你换个支持图片输入的平台（如 ChatGPT、Claude）再试一次。

**验证点 / Checkpoints**：
- ✅ 明确说明"无法接收图片"，不假装看到了图
- ✅ 提供替代路径（纯文本出图 / 换平台）

---

## 场景三：全部能力缺失（仅咨询）/ Scenario 3: No Capabilities (Consultation Only)

**环境 / Environment**：极简对话模型，无任何图像/生图/联网能力。

**用户输入 / User**：「我想把照片改成油画风格，怎么做？」

**Agent 正确响应 / Correct Response**：

> 我当前平台无法处理或生成图像，只能给你方法建议：
> 1. 用支持图片输入的 AI（ChatGPT、Claude、Gemini）上传原图，输入「重构，油画风格，保守强度」；
> 2. 或用即梦、Midjourney 这类生图工具，配合参考图垫图功能保持主体。
> 需要我把详细的 Prompt 模板写给你吗？

**验证点 / Checkpoints**：
- ✅ 不编造"已生成"
- ✅ 明确能力边界 + 给出可执行的外部建议

---

## 场景四：能力齐全（完整流程参考）/ Scenario 4: Full Capabilities (Baseline)

**环境 / Environment**：标准 Skills 平台（Claude/ChatGPT），四项能力齐全。

**用户输入 / User**：上传图片，输入「重构，暖黄黄昏风格，保守强度」

**Agent 正确响应 / Correct Response**：走完整五阶段流程（意图解析 → 参数确认 → 生图 → 保真校验 → 输出摘要 + 成图）。详见 `examples/example_reconstruct.md`。

---

## 降级对照速查表 / Fallback Quick Reference

| 能力组合 / Capabilities | 执行路径 / Path | 输出 / Output |
|------------------------|-----------------|---------------|
| 有 input + generation | 完整流程，方式三选一 | 成图 + 摘要 |
| 有 input、无 generation | 方式三 | 完整 Prompt |
| 无 input | 转纯文本出图 | 出图 Prompt + 换平台提示 |
| 全无 | 仅咨询 | 方法建议 |
