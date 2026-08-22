# Changelog

## [1.4.2] - 2026-08-22

### Added
- 新增 `docs/FAQ.md`：常见问题（安装/使用/其他，中英双语）
  - Added `docs/FAQ.md`: FAQ (installation / usage / miscellaneous, bilingual)
- README 新增「常见问题」章节与目录入口
  - README added an FAQ section and table-of-contents entry

## [1.4.1] - 2026-08-22

### Added
- 新增 `examples/example_fallback.md`：平台降级适配示例（4 个场景 + 降级速查表）
  - Added `examples/example_fallback.md`: platform fallback examples (4 scenarios + quick reference table)
- 新增 `SECURITY.md`：密钥处理强制规范、能力边界、漏洞报告方式
  - Added `SECURITY.md`: mandatory API key handling, known limitations, vulnerability reporting
- README 新增「🚀 快速开始」与「📑 目录」章节
  - README added "Quick Start" and "Table of Contents" sections

### Changed
- README 测试用例章节补充降级示例链接，合规章节补充 SECURITY 链接
  - README added fallback-example link in test cases and SECURITY link in compliance section

## [1.4.0] - 2026-08-21

### Added
- 新增「平台适配与能力自检」章节：平台类型识别、四项能力自检与降级、执行路径决策树、通用铁律
  - Added "Platform Adaptation & Capability Self-Check": platform type identification, four-capability self-check & fallback, execution path decision tree, universal iron rules
- 新增 `docs/install-guide.md`：17+ 平台安装指南（标准 Skills / 提示词型 / 桌面工作台 / MCP 玩法）
  - Added `docs/install-guide.md`: install guide for 17+ platforms (standard Skills / prompt-based / desktop workbench / MCP)
- 新增 `THIRD_PARTY_NOTICES.md`（第三方许可声明，含 MIT 原文）
  - Added `THIRD_PARTY_NOTICES.md` (third-party notices with full MIT license texts)

### Changed
- frontmatter 版本号升级至 1.4.0
  - frontmatter version bumped to 1.4.0
- README 新增平台适配说明、THIRD_PARTY_NOTICES 链接、docs 安装指南链接
  - README added platform-adaptation note, THIRD_PARTY_NOTICES link, and docs install-guide link

## [1.3.0] - 2026-08-20

### Added
- 新增参考图身份保持机制（精选参考图、身份声明、反过度美化、反换脸）
  - Added reference-image identity preservation (curated references, identity declaration, anti-beautification, anti-face-swap)
- 方式二新增供应商参考图支持矩阵（哪些支持/不支持垫图）
  - Method 2 added provider reference-image support matrix (which support / do not support image-to-image)
- 方式二新增供应商自动选择优先级
  - Method 2 added provider auto-selection priority
- 方式二新增密钥环境变量对照表（9 家供应商）
  - Method 2 added key environment variable mapping (9 providers)
- 方式三新增 Prompt 六要素结构化（Subject/Style/Composition/Lighting/Mood/Color）
  - Method 3 added six-element prompt structure (Subject/Style/Composition/Lighting/Mood/Color)
- 方式三新增多工具语法差异表（Midjourney / DALL·E / SD / 即梦）
  - Method 3 added multi-tool syntax difference table (Midjourney / DALL·E / SD / Jimeng)
- 方式三新增 SD/SDXL 提示词模板
  - Method 3 added SD/SDXL prompt template
- 方式三新增 5 条常见陷阱规避 + 2–3 变体生成
  - Method 3 added 5 common pitfall avoidance rules + 2–3 variant generation
- 新增「参考与致谢」章节，标注借鉴来源与许可
  - Added "References & Attribution" section, noting adapted sources and licenses

### Changed
- 异常处理表新增「主体身份漂移」「供应商不支持参考图」两条
  - Exception table added "subject identity drift" and "provider does not support reference images"
- 处理摘要模板「保真状态」新增「身份一致」字段
  - Processing summary "fidelity status" added "identity consistent" field

## [1.2.0] - 2026-08-20

### Added
- 新增生图执行方式三选一机制：Agent 内置生图接口 / 外接 API / 返回完整 Prompt
  - Added a three-way generation execution mechanism: Agent built-in generation API / external API / return a complete prompt
- 新增完整 Prompt 编写规范（11 项必填字段，防幻觉、防漏项、防歧义）
  - Added complete prompt writing rules (11 mandatory fields to prevent hallucination, omission, and ambiguity)
- 新增多工具 Prompt 语法适配（Midjourney / ChatGPT·DALL·E / 即梦 / Stable Diffusion 等）
  - Added multi-tool prompt syntax adaptation (Midjourney / ChatGPT·DALL·E / Jimeng / Stable Diffusion, etc.)
- 新增外接 API Key 单次授权安全规范（用完即焚、不落盘、脱敏展示）
  - Added external API key single-use authorization security rules (burn after use, no persistence, masked display)
- 新增异常处理：API Key 失效、用户未授权外接 API 的回退策略
  - Added exception handling: fallback strategies for invalid API keys and unauthorized external API usage

### Changed
- 处理摘要模板新增「执行方式」字段
  - Added an "Execution method" field to the processing summary template
- 依赖能力声明更新：`image_generation` 仅在方式一/方式二需要，方式三不需要
  - Updated dependency declarations: `image_generation` is needed only for Method 1/2, not for Method 3

## [1.1.0] - 2026-08-14

### Removed
- Removed the 'Miniature Effect (Tilt-Shift)' feature module
- Deleted `examples/example_tiltshift.md`
- Removed all tilt-shift related logic, triggers, and adaptations

### Added
- New professional photography aesthetics: lighting reshaping, color grading, depth optimization, atmosphere enhancement
- New aspect ratio adjustment (3:4↔1:1, 16:9↔4:3, etc.)
- New camera angle adjustment (pitch/roll, sightline shift, camera pan)
- New mandatory confirmation mechanism for adjustments
- New pixel-level fidelity constraints
- New fidelity auto-downgrade and validation checkpoints
- New related test cases

### Changed
- Repository renamed to `ai-image-reconstruct`
- Skill name updated to 'AI Image Intelligent Reconstruction (Professional Photography Edition)'
- Simplified processing flow with a new adjustment confirmation stage
- Output summary now includes adjustment and fidelity status

### Fixed
- Fixed multi-mode instruction parsing issues
- Fixed style-induced text/logo distortion
- Fixed improper perspective after angle adjustments

## [1.0.0] - 2026-08-13

### Added
- Initial release
- Supported reconstruct and tilt-shift modes (tilt-shift removed in v1.1.0)
- Dual compliance checks
- Full test cases
