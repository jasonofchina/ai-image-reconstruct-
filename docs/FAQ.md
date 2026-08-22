# 常见问题 / FAQ

> AI 图像智能重构 Skill 的常见问题，中英双语。
> Frequently asked questions for the AI Image Intelligent Reconstruction Skill, bilingual.

---

## 安装相关 / Installation

### Q1：`SKILL.md` 文件名必须大写吗？/ Must the filename be uppercase?

**必须大写。** 标准 Skills 平台（Claude 等）对文件名大小写敏感，写成 `skill.md` 或 `Skill.md` 会识别不到。
**Yes, it must be uppercase.** Standard Skills platforms (Claude, etc.) are case-sensitive; `skill.md` or `Skill.md` will not be detected.

---

### Q2：粘贴正文后没反应 / 不生效怎么办？/ Pasted the body but it doesn't work?

按顺序排查 / Check in this order：

1. 确认贴的是 `# Skill` **之后**的正文，不是 `---` 包着的 name/description 头信息
   Make sure you pasted the body **after** `# Skill`, not the name/description frontmatter
2. **重启会话**（很多平台要重开对话才会加载新指令）
   **Restart the session** (many platforms load new instructions only after a new conversation)
3. 检查是不是贴漏了（正文很长，容易复制不全）
   Check for truncation (the body is long; copying may be incomplete)

---

### Q3：frontmatter（`---` 那段）要保留吗？/ Do I keep the frontmatter (`---` block)?

- **导入文件时**：保留，平台靠它识别 name/description
  **When importing the file**: keep it — the platform uses it to detect name/description
- **粘贴到提示词框时**：可以删掉 `---` 那段，只留 `# Skill` 之后的正文即可
  **When pasting into a prompt box**: you can delete the `---` block and keep only the body after `# Skill`

---

### Q4：找不到「导入 Skill / Choose tag / 技能」入口？/ Can't find the "Import / Choose tag / Skill" entry?

不同平台入口叫法不同 / Entry names vary by platform：

- GitHub Release 的标签框显示为 **`Tag: Select tag`**（输入版本号后点「Create new tag」）
  GitHub Release shows **`Tag: Select tag`** (type the version then click "Create new tag")
- 桌面工作台（CatPaw / WorkBuddy）叫「技能 / Skill」
  Desktop workbenches (CatPaw / WorkBuddy) call it "技能 / Skill"
- 提示词平台（豆包/千问等）没有"导入"，只有「创建智能体 → 填 Prompt」
  Prompt platforms (Doubao/Qianwen etc.) have no "import", only "create agent → fill prompt"

详见 [install-guide.md](install-guide.md)。
See [install-guide.md](install-guide.md).

---

### Q5：中文版和英文版用哪个？/ Which version should I use, Chinese or English?

内容**完全一致**，按你或平台的习惯选即可：
Content is **identical**; choose by your or the platform's language:

- 中文平台 / 中文用户 → `SKILL.md`
- 英文平台 / 英文用户 → `SKILL-en.md`

---

## 使用相关 / Usage

### Q6：为什么我的平台不直接生成图片？/ Why doesn't my platform generate images directly?

**平台可能没有生图能力。** 本 Skill 内置「平台适配与能力自检」，会自动降级：
**The platform may lack image-generation capability.** The Skill has built-in capability self-check and auto-degrades:

- 有生图能力 → 直接出图 / Has generation → generates directly
- 无生图能力 → 返回一份**完整 Prompt**，你拿到能生图的工具里粘贴即可
  No generation → returns a **complete prompt** for you to paste into a generation tool

这**不是错误**，是预期的降级行为。详见 [examples/example_fallback.md](../examples/example_fallback.md)。
This is **not an error**, but expected fallback behavior. See [examples/example_fallback.md](../examples/example_fallback.md).

---

### Q7：API Key 怎么填？/ How do I fill in the API key?

仅在「方式二：外接 API」时需要 / Only needed for "Method 2: external API"：

1. 到对应供应商后台（如 DashScope、OpenAI、MiniMax）申请 key
   Apply for a key in the vendor's console (e.g. DashScope, OpenAI, MiniMax)
2. 按 Skill 正文的「密钥环境变量对照表」填入环境变量，不要硬编码在对话里
   Set it as an environment variable per the body's key-mapping table; do not hardcode it in chat
3. **用完即焚**：任务结束后 key 会被删除，不落盘、不回显
   **Burn after use**: the key is deleted after the task; no persistence, no echo

安全规范见 [SECURITY.md](../SECURITY.md)。
See [SECURITY.md](../SECURITY.md) for security rules.

---

### Q8：生成结果变脸 / 画质糊怎么办？/ The result changed the face / looks blurry — what do I do?

按优先级排查 / Check in this order：

1. **降级到「保守强度」**——强度越高越容易偏离原图
   **Downgrade to "conservative" intensity** — higher intensity drifts more from the original
2. 确认你用的模型**支持参考图垫图**（如 DashScope wan2.7、GPT Image，见正文第 9.2.1 节）
   Confirm the model **supports reference images** (e.g. DashScope wan2.7, GPT Image; see body Section 9.2.1)
3. 检查强化了「保真约束」（禁止新增/删除元素、禁止锐化/模糊/降噪）
   Check that fidelity constraints are reinforced (no add/remove, no sharpening/blur/denoise)

---

## 其他 / Miscellaneous

### Q9：这个 Skill 收费吗？能商用吗？/ Is this Skill free? Can I use it commercially?

**完全免费，可商用。** 本项目采用 MIT 许可证。
**Completely free and commercial-use allowed.** This project uses the MIT License.

---

### Q10：我遇到了文档里没写的 bug，怎么反馈？/ I found a bug not covered in the docs — how do I report it?

通过 GitHub Issues 提交，安全相关问题标题标注 `[Security]`。
Open a GitHub Issue; for security-related issues, prefix the title with `[Security]`.

贡献指南见 [CONTRIBUTING.md](../CONTRIBUTING.md)。
See [CONTRIBUTING.md](../CONTRIBUTING.md) for contribution guidelines.
