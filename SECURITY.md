# 安全策略 / Security Policy

## 本项目的安全承诺 / Our Security Commitment

本 Skill 本身不接触、不存储任何用户数据；唯一涉及敏感信息的环节是**用户提供生图 API Key**（方式二：外接生图接口）。对此，本项目强制遵守以下安全规范。

This Skill itself does not touch or store any user data. The only sensitive-data scenario is when a user provides a generation API key (Method 2: external API). For this, the following security rules are mandatory.

---

## 密钥处理强制规范 / Mandatory API Key Handling

| 规范 / Rule | 说明 / Description |
|-------------|-------------------|
| **单次授权 / One-time** | Key 仅用于本次任务，任务完成后立即删除，不保留任何副本 / Key is used only for the current task; delete it immediately after, keep no copy |
| **不落盘 / No persistence** | Key 严禁写入文件、日志、记忆或任何持久化存储 / Never write the key to files, logs, memory, or any persistent storage |
| **不展示 / No echo** | 对话中不回显完整 Key，仅以脱敏形式确认（如 `sk-****abcd`）/ Never echo the full key; confirm only in masked form (e.g. `sk-****abcd`) |
| **用完即焚 / Burn after use** | 生成完成后，主动告知用户「授权密钥已删除」/ After generation, proactively tell the user "the key has been deleted" |
| **失效即停 / Stop on failure** | Key 无效/额度不足/网络异常时，立即停止重试、删除 Key、提示用户检查 / On invalid key / quota exceeded / network error, stop retrying, delete the key, and prompt the user to check |

---

## 已知能力边界 / Known Limitations

- 本 Skill 是纯 Markdown 文档，**不包含任何可执行代码**，无远程数据回传。/ This Skill is a pure Markdown document with **no executable code** and no remote data exfiltration.
- 生图能力依赖各平台/供应商自带接口，具体数据合规以对应平台政策为准。/ Image generation depends on each platform/vendor's own API; data compliance follows that platform's policy.

---

## 报告安全问题 / Reporting a Vulnerability

如发现安全相关问题，请通过 GitHub Issues 提交，并在标题标注 `[Security]`。

If you find a security issue, please open a GitHub Issue with `[Security]` in the title.
