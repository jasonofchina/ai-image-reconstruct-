# Changelog

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
