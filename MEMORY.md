# 🧠 长期记忆库（常青记忆）

*这是核心知识库，永久保存重要信息。*

---

## 📌 核心档案

### 关于我（AI 助手）
- **名称**: 待定义
- **身份**: OpenClaw AI Agent
- **性格**: 真诚、高效、有主见
- **签名 Emoji**: 待选择

### 关于我的用户（zjw）
- **姓名**: zjw
- **职业**: 自动驾驶系统开发工程师
- **工作习惯**: 深夜工作，AI 工具重度用户（Cursor, Claude Code, ChatGPT, Gemini）
- **现状**: 工作 + 研究 AI 挤占锻炼时间，经常感到疲乏，习惯性熬夜
- **时区**: Asia/Shanghai (GMT+8)

---

## 📊 记忆系统架构说明

本记忆系统采用**双层记忆结构**：

| 层级 | 位置 | 内容类型 | 保留策略 |
|------|------|----------|----------|
| **长期记忆** | `MEMORY.md` + `memory/*.md` | 核心知识、联系人、决策、偏好、项目、模式 | 永久保存 |
| **短期记忆** | `memory/YYYY-MM-DD.md` | 每日会话日志、临时信息 | 30天衰减 |

### 专题记忆文件
- 📇 [contacts.md](./memory/contacts.md) - 联系人信息
- 🎯 [decisions.md](./memory/decisions.md) - 重要决策记录
- ⚙️ [preferences.md](./memory/preferences.md) - 用户偏好设置
- 📁 [projects.md](./memory/projects.md) - 项目信息
- 🧩 [patterns.md](./memory/patterns.md) - 模式和最佳实践
- 💬 [feedback.md](./memory/feedback.md) - 反馈记录

---

## 🔄 记忆写入规则

根据重要性自动分级：

| 评分 | 处理方式 | 说明 |
|------|----------|------|
| **≥4分** | 追加到 MEMORY.md 或对应专题文件 | 非常重要，永久保存 |
| **2-3分** | 记录到当日日志 | 有一定价值，短期保留 |
| **<2分** | 不记录 | 临时信息，无需保留 |

### 手动触发词
当用户说以下词语时，自动提升重要性：
- "记下来" / "记住这个"
- "别忘了"
- "永久保存"
- "这是一个重点"
- "很重要"

---

## 📝 重要记忆索引

### 最近更新
<!-- 按时间倒序记录重要更新 -->
- 2026-04-06: **系统维护与崩溃排查**
  - 完成周一专题文件同步检查与超期日志清理 (30天以上)
  - 记录持续的 ByteRover Context 报错及因 Kimi API 超时导致的 agent 崩溃 (code=1)
  - 日记提醒时间调整待用户反馈确认
- 2026-04-03: **Gemma 4 + OpenAI 1220亿融资 + ClawAegis**
  - Google DeepMind 发布 Gemma 4（开源推理模型，31B 全球第三，Apache 2.0）
  - OpenAI 完成 1220亿美元融资（科技史最大私募，估值8520亿）
  - 蚂蚁+清华开源 ClawAegis（首个 OpenClaw 智能体安全插件）
  - ByteRover 问题恶化持续，详见下方
- 2026-04-04: **ByteRover 报错根因已确认 - Kimi API 账户失效**
  - ByteRover `LLM request rejected` 实际是 Kimi API 402 错误导致
  - Kimi API key `sk-kimi-XroRG19nNFxx...` 返回 401+402 (账户问题)
  - 已修复: 从 fallback 列表移除 kimi/k2p5，重启 Gateway
  - 待办: 用户需检查 Kimi API 账户状态
- 2026-04-02: **重要更新**
  - PUA skill 安装完成（高压推进技能，用于穷尽方案不放弃）
  - exec 配置修复：`execApprovals.mode allow-always` + Gateway 重启
  - ByteRover 根因确认：hook-based 扩展调用 brv CLI 失败，不影响核心功能
  - brv CLI v2.3.2 工作正常
- 2026-04-01: **系统事件** - ByteRover Context 再次报错 "Agent process exited before ready (code=1)"
  - 可能是 ByteRover 上下文获取时机问题，需持续观察
- 2026-04-01: **每周专题文件同步检查** - 全部正常，无需更新
- 2026-03-31: **系统模式归档** - ByteRover 知识挖掘结果归档至 patterns.md
  - OpenClaw agent 崩溃 (code=1): 版本升级 2026.3.28 解决
  - ByteRover Context 报错: 已知 cron 时机相关模式
  - Gateway 健康检查: `openclaw gateway status`
- 2026-03-27: **重要指令** - 用户要求AI必须主动承担自身任务，不依赖提醒
  - 创建 `memory/tasks.md` 作为每日任务清单
  - 更新 HEARTBEAT.md 增加主动任务追踪
- 2026-03-15: **重要教训** - 时效性查询必须先确认当前时间（已记录到 patterns.md）
- 2026-03-15: 记录用户AI工具使用情况（Cursor为主，计划探索Claude Code、Codex）
- 2026-03-12: 搭建完成双层记忆系统，配置 Ollama 向量搜索（下载中）
- 2026-03-12: 记录用户偏好 - 喜欢先测试再使用新系统 

### 待办/跟进
<!-- 需要后续处理的事项 -->
- 

### 关键决策
<!-- 重要决策的引用链接 -->
- 

---

*最后整理: 2026-04-06*
