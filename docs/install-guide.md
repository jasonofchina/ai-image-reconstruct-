# AI 图像智能重构 Skill · 多平台安装指南 / Multi-Platform Install Guide

> 一份文档，搞定主流 AI 平台的 Skill 安装方法。
> One document to cover Skill installation on all mainstream AI platforms.
> 适用项目 / Project：`jasonofchina/ai-image-reconstruct`（AI 图像智能重构 Skill）
> 当前版本 / Version：v1.4.0（内置「平台适配与能力自检」，任何平台都能自动降级适配）

---

## 先搞清楚：你的 Skill 属于哪种形态 / First: What Kind of Skill Is Yours?

不同平台的"安装"方式完全不同，关键看平台吃不吃 **Agent Skills 标准**（即 `SKILL.md` 文件 + `name`/`description` 头信息）。
Installation methods differ by platform. The key is whether a platform supports the **Agent Skills standard** (a `SKILL.md` file with `name`/`description` frontmatter).

| 形态 / Type | 平台 / Platforms | 安装方式 / Install Method |
|------|------|---------|
| ✅ 标准 Skills / Standard Skills | Claude、ChatGPT、Gemini、Coze | 直接导入 `SKILL.md` 文件 / Import `SKILL.md` directly |
| 📋 提示词型智能体 / Prompt-based agent | 千问、豆包、文心、星火、Kimi、MiniMax、元宝、DeepSeek、ima、智谱清言 | 把正文粘贴到「系统提示词」/ Paste body into system prompt |
| 🖥️ 桌面 Agent 工作台 / Desktop agent workbench | CatPaw、WorkBuddy | 客户端里「技能」区创建/导入 / Create in the client's skills area |
| 🔌 MCP 插件玩法 / MCP plugin | 通义百炼、Coze、Dify 等支持 MCP 的平台 | 封装成 MCP 工具接入 / Wrap as an MCP tool |

> 一句话判断：平台有没有"导入 Skill 文件"的入口？有 → 标准法；只有"创建智能体/填 Prompt" → 粘贴法。
> Quick rule: does the platform have an "import Skill file" entry? Yes → standard method; only "create agent / fill prompt" → paste method.
>
> **好消息 / Good news**：v1.4.0 起，skill 正文开头有「平台适配与能力自检」章节，无论装到哪个平台，Agent 都会先自检能力、自动降级适配，不会因为平台不同而报错或乱来。
> Since v1.4.0, the Skill body begins with a "Platform Adaptation & Capability Self-Check" section. On any platform, the Agent self-checks capabilities and auto-degrades, so it won't error or misbehave due to platform differences.

---

## 一、标准 Skills 平台（导入文件）/ 1. Standard Skills Platforms (Import the File)

### 1. Claude（Anthropic）—— Skills 标准制定者 / The Originator of Agent Skills

**定位 / Positioning**：Agent Skills 的"原生家庭"，支持最完整。/ The "native home" of Agent Skills, with the most complete support.

**安装步骤 / Steps：**
1. 把 `SKILL.md` 放到目录：`~/.claude/skills/image-reconstruct/SKILL.md` / Put `SKILL.md` in `~/.claude/skills/image-reconstruct/SKILL.md`
2. 项目级也行：`.claude/skills/image-reconstruct/SKILL.md` / Or project-level: `.claude/skills/image-reconstruct/SKILL.md`
3. 重启会话，Agent 自动识别 / Restart the session; the Agent auto-detects it

**关键点 / Key points：**
- 文件名必须大写 `SKILL.md`（大小写敏感）/ Filename must be uppercase `SKILL.md` (case-sensitive)
- frontmatter 必须有 `name` + `description` 两个字段 / Frontmatter must have `name` + `description`

---

### 2. ChatGPT（OpenAI）

**定位 / Positioning**：已支持 Skills 标准。/ Already supports the Skills standard.

**安装步骤 / Steps：**
1. 打开 ChatGPT 的 Skills 功能入口，添加技能 / Open ChatGPT's Skills entry and add a skill
2. 上传/粘贴 `SKILL.md` / Upload or paste `SKILL.md`
3. 或在自定义 GPT / Project 的 Instructions 里粘贴正文 / Or paste the body into a custom GPT / Project's Instructions

**关键点 / Key points：**
- 用自定义 GPT 时，把 `# Skill` 之后的正文贴进 Instructions / For custom GPTs, paste the body after `# Skill` into Instructions

---

### 3. Gemini（Google）—— 御三家之一（三种玩法）/ One of the Big Three (Three Ways)

**定位 / Positioning**：Google 全家桶，三条路径都能跑。/ Google's full suite; all three paths work.

**玩法 A · Gemini App / 网页版 / Method A · Gemini App / Web**
1. 打开 Gemini（gemini.google.com）/ Open Gemini (gemini.google.com)
2. 创建 Gems（自定义助手）/ Create a Gem (custom assistant)
3. 把 `SKILL.md` 正文粘贴到「Instructions（指令）」框，保存 / Paste the `SKILL.md` body into the "Instructions" box and save

**玩法 B · Google AI Studio / Method B · Google AI Studio**
1. 打开 aistudio.google.com / Open aistudio.google.com
2. 新建 Prompt / 应用，把正文粘贴到「System Instructions」/ Create a new prompt/app, paste the body into "System Instructions"
3. 可配合「图片输入」能力测试重构效果 / Can pair with image input to test reconstruction

**玩法 C · Gemini CLI（开发者）/ Method C · Gemini CLI (Developer)**
1. 安装 Gemini CLI 后，把 `SKILL.md` 挂到 skills 目录 / After installing Gemini CLI, mount `SKILL.md` in the skills directory
2. CLI 会自动加载 name/description 并触发 / The CLI auto-loads name/description and triggers

**关键点 / Key points：**
- Gemini 偏"指令 + 工具"，正文可直接当系统指令用 / Gemini leans "instructions + tools"; the body works directly as a system instruction
- 图片理解是 Gemini 强项，重构效果较好 / Image understanding is Gemini's strength, so reconstruction works well

---

### 4. Coze（扣子，字节）/ Coze (ByteDance)

**定位 / Positioning**：字节的智能体搭建平台，插件/技能生态强。/ ByteDance's agent-building platform with a strong plugin/skill ecosystem.

**安装步骤 / Steps：**
1. 创建智能体（Bot）/ Create a bot
2. 把 `SKILL.md` 正文粘贴到「人设与回复逻辑」/ Paste the `SKILL.md` body into "Persona & Reply Logic"
3. 或封装成「技能 / 插件」供复用 / Or wrap it as a reusable skill / plugin

**关键点 / Key points：**
- Coze 兼容 Skills 导入，也支持手动粘贴，两种都行 / Coze supports Skills import and manual paste; both work
- 支持 MCP，可把生图接口封装成 MCP 工具接入（见下文 MCP 玩法）/ Supports MCP; you can wrap the generation API as an MCP tool (see MCP section below)

---

## 二、提示词型智能体（粘贴法）/ 2. Prompt-Based Agents (Paste Method)

> 通用三步 / Three universal steps：① 进平台"创建智能体" → ② 复制 `SKILL.md` 里 `# Skill` 之后的全部正文 → ③ 粘贴到「系统提示词/Prompt/人设」框，保存。
> ① Enter "create agent" → ② copy everything after `# Skill` in `SKILL.md` → ③ paste into the "system prompt / Prompt / persona" box and save.

### 5. 千问（通义千问）/ Qianwen (Tongyi)
- **入口 / Entry**：通义 App / 阿里云百炼平台 → 创建应用 / Tongyi App / Alibaba Cloud Bailian → create app
- **粘贴位置 / Paste into**：Prompt 模板 / 系统指令 / Prompt template / system instruction

### 6. 豆包 / Doubao
- **入口 / Entry**：豆包 App / 豆包智能体中心 / Doubao App / Doubao agent center
- **粘贴位置 / Paste into**：人设与回复逻辑 / Persona & reply logic

### 7. 文心一言 / Wenxin (ERNIE)
- **入口 / Entry**：文心智能体平台（AgentBuilder）/ Wenxin agent platform (AgentBuilder)
- **粘贴位置 / Paste into**：角色设定 / Prompt / Character setting / Prompt

### 8. 星火（讯飞）/ Xinghuo (iFlytek)
- **入口 / Entry**：星火 App / 讯飞开放平台 / Xinghuo App / iFlytek open platform
- **粘贴位置 / Paste into**：角色设定 / Prompt / Character setting / Prompt

### 9. Kimi（月之暗面）/ Kimi (Moonshot)
- **入口 / Entry**：Kimi+ / Kimi 开放平台 / Kimi+ / Kimi open platform
- **粘贴位置 / Paste into**：Prompt / 系统提示词 / Prompt / system prompt

### 10. MiniMax（海螺）/ MiniMax (Hailuo)
- **入口 / Entry**：海螺 AI / MiniMax 开放平台 / Hailuo AI / MiniMax open platform
- **粘贴位置 / Paste into**：Agent 的 Prompt / Agent's Prompt

### 11. 腾讯元宝 / Tencent Yuanbao
- **入口 / Entry**：元宝 App → 智能体 / Yuanbao App → agent
- **粘贴位置 / Paste into**：系统提示词 / System prompt

### 12. DeepSeek
- **说明 / Note**：官方以对话为主，无独立智能体平台 / Officially chat-focused, no standalone agent platform
- **做法 / Method**：用 API 接入第三方（Coze / Dify / 扣子）创建智能体，粘贴正文 / Use its API in a third party (Coze / Dify) to create an agent and paste the body

### 13. ima（腾讯）/ ima (Tencent)
- **入口 / Entry**：ima 知识库 App / ima knowledge-base App
- **粘贴位置 / Paste into**：自定义指令 / 提示词设置 / Custom instruction / prompt settings

### 14. 智谱清言（GLM）/ Zhipu Qingyan (GLM)
- **入口 / Entry**：智谱清言 App / 开放平台（open.bigmodel.cn）/ Qingyan App / open platform (open.bigmodel.cn)
- **做法 / Method**：创建智能体，把正文粘贴到「提示词 / Prompt」框 / Create an agent and paste the body into the prompt box
- **关键点 / Key points**：智谱的 GLM 系列对中文理解好，粘贴正文即可正常执行 / Zhipu's GLM handles Chinese well; pasting the body works correctly

---

## 三、桌面 Agent 工作台 / 3. Desktop Agent Workbenches

### 15. CatPaw（美团）/ CatPaw (Meituan)
- **定位 / Positioning**：美团全场景 AI Agent 平台（2026 年 7 月上线）/ Meituan's full-scenario AI Agent platform (launched July 2026)
- **安装步骤 / Steps**：
  1. 官网下载 App / PC 客户端，美团 App 或微信扫码登录 / Download the App / PC client and log in via Meituan App or WeChat QR
  2. 进入「技能」区，创建新技能 / Go to the "Skills" area and create a new skill
  3. 把 skill 正文粘贴进去，或用对话方式封装为专属技能 / Paste the body in, or wrap it into a dedicated skill via conversation

### 16. WorkBuddy（腾讯）/ WorkBuddy (Tencent)
- **定位 / Positioning**：腾讯 AI 办公工作台（桌面智能体，2026 年 3 月推出）/ Tencent's AI office workbench (desktop agent, launched March 2026)
- **安装步骤 / Steps**：
  1. 官网下载桌面客户端（Windows / macOS），微信扫码登录 / Download the desktop client (Windows / macOS) and log in via WeChat QR
  2. 在「技能（Skill）」区导入 / 创建技能 / In the "Skill" area, import / create a skill
  3. 粘贴正文，或关联 MCP 连接器 / Paste the body, or link an MCP connector

---

## 四、MCP 插件玩法（进阶）/ 4. MCP Plugin (Advanced)

> 适用 / Applies to：通义百炼、Coze、Dify、Cursor 等支持 MCP（Model Context Protocol）的平台。
> 核心思路 / Core idea：把"生图能力"封装成 MCP 工具，让 skill 的 Agent 通过 MCP 调用，而不是靠平台自带能力。
> Wrap the "generation capability" as an MCP tool so the Agent calls it via MCP instead of relying on platform built-ins.

### 17. 通义百炼（阿里云）—— MCP 玩法 / Tongyi Bailian (Alibaba Cloud) — MCP

**定位 / Positioning**：阿里云百炼是官方 Agent 平台，天然支持 MCP，且自带 DashScope 图像生成 API。/ Bailian is Alibaba's official agent platform, natively supports MCP, and ships with the DashScope image-generation API.

**玩法 A · 直接建应用（简单）/ Method A · Direct app (simple)**
1. 登录百炼控制台（bailian.console.aliyun.com）/ Log in to the Bailian console (bailian.console.aliyun.com)
2. 创建应用 → 选「通义千问」模型 / Create an app → choose the Tongyi Qianwen model
3. 把 `SKILL.md` 正文粘贴到「Prompt 模板」/ Paste the `SKILL.md` body into the "Prompt template"
4. 开通 DashScope 的「图像生成」能力，作为工具接入 / Enable DashScope's image-generation capability as a tool

**玩法 B · 封装 MCP Server（进阶）/ Method B · Wrap an MCP Server (advanced)**
1. 用 DashScope 的 `wan2.7-image` 模型写一个 MCP 图像生图服务 / Write an MCP image-generation service using DashScope's `wan2.7-image` model
2. 在百炼「MCP 管理」里添加该 MCP 服务 / Add the MCP service in Bailian's "MCP Management"
3. 创建智能体时勾选该 MCP 工具 / Select the MCP tool when creating the agent
4. 正文里"方式二：外接 API"的供应商选 DashScope，Key 用 `DASHSCOPE_API_KEY` / In the body, choose DashScope as the Method-2 provider and use `DASHSCOPE_API_KEY`

**关键点 / Key points：**
- 百炼/通义的 `wan2.7-image` 系列**支持参考图垫图**，能保持原图主体（对照 skill 第 9.2.1 节）/ Bailian/Tongyi's `wan2.7-image` family **supports reference images**, preserving the original subject (see Section 9.2.1)
- 其余非 wan2.7 系列不支持垫图，注意避坑 / Other non-wan2.7 families do not support reference images — watch out

### 通用 MCP 思路（适配任意支持 MCP 的平台）/ General MCP Approach (Any MCP Platform)

1. 选一个支持参考图的生图 API（OpenAI GPT Image / Gemini / MiniMax / Seedream / DashScope wan2.7）/ Pick a reference-capable generation API (OpenAI GPT Image / Gemini / MiniMax / Seedream / DashScope wan2.7)
2. 封装成 MCP 工具（一个 `generate_image` 工具，入参：prompt + 可选参考图）/ Wrap as an MCP tool (a `generate_image` tool with params: prompt + optional reference image)
3. 在平台里挂载该 MCP 工具 / Mount the MCP tool in the platform
4. 把 `SKILL.md` 正文当系统提示词，Agent 会自动走"方式二：外接 API"路径调用你的 MCP 工具 / Use the `SKILL.md` body as the system prompt; the Agent auto-routes to "Method 2: external API" and calls your MCP tool

---

## 五、一句话口诀 / 5. One-Line Cheat Sheet

- 🈶 有「导入 Skill 文件」入口 → 交 `SKILL.md` 文件 / Has an "import Skill file" entry → hand over `SKILL.md`
- 💬 只有「对话框 / 填 Prompt」→ 粘正文当"人设" / Only a chat box / prompt field → paste the body as the "persona"
- 🖥️ 桌面工作台 → 客户端里建「技能」/ Desktop workbench → create a "skill" in the client
- 🔌 支持 MCP → 封生图 API 成 MCP 工具，正文当系统提示词 / Supports MCP → wrap the generation API as an MCP tool, use the body as the system prompt

---

## 附：关于「御三家」/ Appendix: About the "Big Three"

- **海外御三家 / Overseas Big Three**：Claude / ChatGPT / Gemini（Agent 标准三巨头，均支持 Skills）/(the three Agent-standard giants, all supporting Skills)
- **国产三大厂 / Domestic Big Three**：豆包 / 千问 / 文心（提示词型，用粘贴法）/(prompt-based, use the paste method)

> 你手上的 `SKILL.md` 一份文件全平台通用——标准平台直接导文件，提示词平台粘正文，桌面工作台建技能，MCP 平台封工具。配合 v1.4.0 的「平台适配与能力自检」，一招吃遍所有平台。
> Your single `SKILL.md` works on every platform — import the file on standard platforms, paste the body on prompt platforms, create a skill on desktop workbenches, and wrap a tool on MCP platforms. Combined with v1.4.0's "Platform Adaptation & Capability Self-Check", one skill covers them all.
