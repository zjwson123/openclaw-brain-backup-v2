# OpenClaw 能力全景指南

> 版本：2026-03-01 | 适用版本：OpenClaw v2026.x

---

## 一、什么是 OpenClaw？

OpenClaw 是一个**自托管的 AI 助手网关**，让你可以在自己控制的设备上运行 AI 助手，并通过你日常使用的聊天应用（WhatsApp、Telegram、Discord、iMessage、Signal、Slack 等）与之交互。

### 核心定位
- **自托管**：数据留在你自己的机器上，不依赖第三方云服务
- **多通道**：一个 Gateway 同时服务多个聊天应用
- **Agent 原生**：专为 AI 编码助手设计，支持工具调用、会话管理、多 Agent 路由
- **开源**：MIT 许可证，社区驱动

### 架构简览
```
聊天应用 (WhatsApp/Telegram/Discord/Signal/iMessage/Feishu)
         │
         ▼
    ┌─────────────┐
    │   Gateway   │  ← 控制平面 (WebSocket)
    │  (核心服务)  │
    └──────┬──────┘
           │
    ┌──────┴──────┐
    │             │
Pi Agent      CLI/Web UI
(编码助手)    (控制界面)
    │             │
iOS/Android   macOS 菜单栏
节点设备       应用
```

---

## 二、核心能力一览

### 2.1 消息通道支持

| 通道 | 状态 | 说明 |
|------|------|------|
| **WhatsApp** | ✅ 内置 | 基于 WhatsApp Web (Baileys) |
| **Telegram** | ✅ 内置 | 基于 grammY Bot API |
| **Discord** | ✅ 内置 | 基于 discord.js |
| **Signal** | ✅ 内置 | 基于 signal-cli |
| **iMessage** | ✅ 内置 | macOS 原生 (imsg CLI) |
| **Slack** | ✅ 内置 | 基于 Bolt |
| **Google Chat** | ✅ 内置 | Chat API |
| **Feishu/飞书** | ✅ 内置 | 企业级集成 |
| **BlueBubbles** | ✅ 内置 | iMessage 推荐方案 |
| **Microsoft Teams** | 🔌 扩展 | 插件形式 |
| **Matrix** | 🔌 扩展 | 插件形式 |
| **Zalo** | 🔌 扩展 | 越南市场 |
| **WebChat** | ✅ 内置 | 浏览器界面 |

### 2.2 Agent 运行时

- **Pi Agent (RPC 模式)**：官方支持的编码助手，支持工具流式传输
- **工具调用**：完整的工具生态（见下文）
- **会话管理**：多会话隔离，支持主会话和群组会话分离
- **模型配置**：支持多模型切换（Anthropic、OpenAI、Gemini 等）

### 2.3 工具生态

#### 文件与代码工具
- `read` / `write` / `edit`：文件操作
- `exec`：执行 shell 命令
- `apply_patch`：应用代码补丁
- `sessions_spawn`：生成子 Agent

#### 浏览器自动化
- `browser`：控制 Chrome/Chromium
  - 标签页管理、页面截图、快照
  - 点击、输入、滚动等交互操作
  - PDF 生成、Cookie 管理
  - 多配置文件支持（隔离环境）

#### 移动设备节点
- `nodes`：iOS/Android 设备控制
  - `camera_snap`：拍照（前后摄像头）
  - `camera_clip`：录制视频
  - `screen_record`：屏幕录制
  - `location_get`：获取位置
  - `system.run`：在节点执行命令

#### Canvas 可视化
- `canvas`：macOS 上的可视化工作区
  - 展示 HTML/CSS/JS 内容
  - A2UI 协议支持
  - 屏幕截图/快照

#### 会话与调度
- `sessions_list` / `sessions_send`：跨会话通信
- `cron`：定时任务调度
- `subagents`：子 Agent 管理

#### 第三方集成
- `message`：跨通道发送消息
- `web_search` / `web_fetch`：网络搜索
- `tts`：文本转语音
- `feishu_doc` / `feishu_wiki`：飞书集成

---

## 三、社区使用场景与案例

### 3.1 个人自动化助手

#### 🛒 购物自动化
> "Tesco Shop Autopilot" - 每周餐单 → 常购商品 → 预订配送 → 确认订单。全程无需 API，仅用浏览器控制。

**能力展示**：
- 浏览器登录电商网站
- 自动化购物车操作
- 定时任务（cron）触发

#### 🏠 智能家居控制
- **Winix 空气净化器**：Claude Code 发现控制协议 → OpenClaw 接管管理室内空气质量
- **Roborock 扫地机器人**：自然语言控制机器人清扫、查看状态
- **Home Assistant 集成**：通过技能控制全屋智能设备

#### 💰 财务自动化
- **月度记账**：收集邮件中的 PDF 票据，整理成税务顾问需要的格式
- **ParentPay 学校餐费**：自动化英国学校餐费预订

### 3.2 开发与工作流

#### 📱 完整 App 开发
> 通过 Telegram 聊天完成 iOS App 开发（地图、录音功能），直接部署到 TestFlight —— 全程未打开笔记本。

**涉及能力**：
- 代码生成与编辑
- Xcode 项目构建
- TestFlight 部署

#### 🔍 PR 代码审查
> OpenCode 完成改动 → 创建 PR → OpenClaw 审查 diff → 在 Telegram 回复审查意见 + 合并建议

**工作流**：
1. 子 Agent 生成代码变更
2. GitHub 集成创建 PR
3. OpenClaw 读取 diff 并提供反馈

#### 📊 3D 打印控制
- **Bambu 打印机技能**：状态查询、任务管理、摄像头预览、AMS 控制、校准

#### 📝 项目管理
- **Linear CLI**：从终端管理 Linear 问题和项目
- **Jira 技能**：自然语言创建、查询 Jira 任务
- **Todoist 集成**：通过 Telegram 管理待办事项

### 3.3 知识管理与学习

#### 🍷 私人酒窖管理
> 用户要求建立本地酒窖技能 → OpenClaw 请求 CSV 样本 → 构建并测试技能（案例中管理了 962 瓶酒）

#### 📚 中文学习助手 (xuezh)
- 发音反馈
- 学习流程管理
- 语音交互

#### 🔖 书签语义搜索
- Karakeep 书签集成
- Qdrant 向量数据库
- OpenAI/Ollama 嵌入

### 3.4 创意与内容

#### 🎨 视觉早报生成
> 定时提示生成每日"场景"图片（天气、任务、日期、喜欢的帖子/引用）

#### 📸 天空摄影
- 屋顶摄像头触发
- OpenClaw 判断"天空好看"时自动拍照

#### ✂️ SNAG 截图工具
- 快捷键截取屏幕区域
- Gemini Vision 识别
- 自动生成 Markdown 到剪贴板

### 3.5 多 Agent 编排

#### 🤖 Kev's Dream Team
> 14+ Agent 在一个 Gateway 下运行，Opus 4.5 作为编排器，委派给 Codex 工作器。

**架构亮点**：
- 技术架构完整记录
- 模型选择策略
- 沙盒隔离
- Webhook + Heartbeat 协调

---

## 四、最佳实践指南

### 4.1 部署模式选择

| 场景 | 推荐方案 | 说明 |
|------|----------|------|
| **个人使用** | macOS / Linux 本机 | 最简单，直接控制本机资源 |
| **家庭共享** | Linux 服务器 + Tailscale | 多用户隔离，安全访问 |
| **远程工作** | VPS + SSH 隧道 | 云端运行，多地访问 |
| **智能家居** | Home Assistant OS + 插件 | 与智能家居生态集成 |

### 4.2 安全配置清单

```json5
// 基础安全配置示例
{
  gateway: {
    bind: "loopback",  // 仅本地访问
    auth: {
      mode: "token",   // Token 认证
      token: "your-secure-token"
    }
  },
  channels: {
    whatsapp: {
      dmPolicy: "pairing",  // 需要配对才能 DM
      allowFrom: ["+86138xxxxxxxx"]  // 白名单
    }
  },
  agents: {
    defaults: {
      sandbox: {
        mode: "non-main"  // 非主会话使用沙盒
      }
    }
  }
}
```

**关键安全实践**：
1. **配对机制**：对未知发送者要求配对码验证
2. **白名单**：限制可访问的用户/群组
3. **沙盒隔离**：对非主会话启用 Docker 沙盒
4. **工具限制**：对特定 Agent 禁用危险工具（如 `write`、`exec`）
5. **Tailscale**：使用 Tailnet 替代公网暴露

### 4.3 多 Agent 设计模式

```json5
// 多 Agent 配置示例
{
  agents: {
    list: [
      {
        id: "personal",
        name: "个人助手",
        workspace: "~/.openclaw/workspace-personal",
        model: "anthropic/claude-sonnet-4-5",
        sandbox: { mode: "off" }  // 信任环境，无沙盒
      },
      {
        id: "coding",
        name: "编程助手",
        workspace: "~/.openclaw/workspace-coding",
        model: "anthropic/claude-opus-4-6",
        tools: {
          allow: ["exec", "read", "write", "edit"],
          deny: ["browser", "canvas", "nodes"]
        }
      },
      {
        id: "family",
        name: "家庭机器人",
        workspace: "~/.openclaw/workspace-family",
        sandbox: { mode: "all", scope: "agent" },
        tools: {
          allow: ["read", "sessions_list"],
          deny: ["write", "edit", "exec", "browser"]
        }
      }
    ]
  },
  bindings: [
    // 个人 WhatsApp → personal Agent
    { agentId: "personal", match: { channel: "whatsapp", accountId: "personal" } },
    
    // 工作 Telegram → coding Agent
    { agentId: "coding", match: { channel: "telegram" } },
    
    // 特定家庭群组 → family Agent
    { 
      agentId: "family", 
      match: { 
        channel: "whatsapp", 
        peer: { kind: "group", id: "1203630...@g.us" }
      }
    }
  ]
}
```

### 4.4 自动化工作流设计

#### Heartbeat vs Cron 选择指南

| 场景 | 推荐 | 原因 |
|------|------|------|
| 定期检查（邮件、日历） | Heartbeat | 可批量，有对话上下文 |
| 精确时间任务（每天早上 9 点） | Cron | 精确控制，独立执行 |
| 一次性提醒（20 分钟后） | Cron | 单次任务，无需持续 |
| 需要隔离的后台任务 | Cron (isolated) | 不污染主会话历史 |

#### Cron 任务示例

```bash
# 早报生成（每天早上 7 点）
openclaw cron add \
  --name "Morning Brief" \
  --cron "0 7 * * *" \
  --tz "Asia/Shanghai" \
  --session isolated \
  --message "生成今日早报：检查邮件、日历、天气，发送摘要" \
  --announce \
  --channel whatsapp \
  --to "+86138xxxxxxxx"

# 定时提醒（20 分钟后）
openclaw cron add \
  --name "Quick Reminder" \
  --at "20m" \
  --session main \
  --system-event "记得给团队发周报" \
  --wake now \
  --delete-after-run
```

### 4.5 技能开发最佳实践

#### Skill 结构
```
skills/
└── my-skill/
    ├── SKILL.md          # 技能定义（必需）
    ├── README.md         # 使用说明
    └── scripts/          # 辅助脚本（可选）
```

#### SKILL.md 模板
```markdown
---
name: my-awesome-skill
description: 一句话描述技能功能
metadata:
  {
    "openclaw":
      {
        "emoji": "🚀",
        "requires": { 
          "bins": ["docker"],           # 需要的可执行文件
          "env": ["API_KEY"],            # 需要的环境变量
          "config": ["browser.enabled"]  # 需要的配置项
        },
        "primaryEnv": "API_KEY"
      }
  }
---

# 使用说明

当用户要求 XXX 时，执行以下步骤：
1. ...
2. ...

## 示例

用户："帮我做 XXX"
→ 你应该 ...
```

### 4.6 节点（Nodes）使用技巧

#### iOS/Android 设备配对
```bash
# 1. 在手机上安装 OpenClaw Companion App
# 2. 配对设备
openclaw nodes pending
openclaw nodes approve <requestId>

# 3. 使用设备能力
openclaw nodes camera snap --node iPhone --facing back
openclaw nodes screen record --node iPhone --duration 10s
openclaw nodes location get --node iPhone
```

#### 远程执行工作流
```bash
# Gateway 在服务器，在本机执行命令
openclaw config set tools.exec.host node
openclaw config set tools.exec.node "my-macbook"

# 之后所有 exec 调用都会在 macbook 上执行
```

---

## 五、进阶功能详解

### 5.1 Canvas 与 A2UI

Canvas 是 macOS 上的可视化工作区，Agent 可以在上面渲染 UI：

```javascript
// A2UI v0.8 示例
{
  "surfaceUpdate": {
    "surfaceId": "main",
    "components": [
      {
        "id": "title",
        "component": {
          "Text": {
            "text": {"literalString": "Hello Canvas"},
            "usageHint": "h1"
          }
        }
      }
    ]
  }
}
```

**使用场景**：
- 实时数据仪表盘
- 交互式配置界面
- 图像/视频预览

### 5.2 浏览器自动化深度应用

```bash
# 多配置文件隔离
openclaw browser create-profile --name work --color "#0066CC"
openclaw browser create-profile --name personal --color "#FF4500"

# 自动化登录流程
openclaw browser open https://example.com
openclaw browser snapshot --interactive
openclaw browser type e12 "username" --submit
openclaw browser type e23 "password" --submit

# 截图与 PDF
openclaw browser screenshot --full-page
openclaw browser pdf --path report.pdf
```

### 5.3 子 Agent 编排

```bash
# 生成子 Agent 处理复杂任务
openclaw sessions_spawn \
  --task "分析这个代码库并找出潜在 bug" \
  --mode run \
  --runtime subagent \
  --label "code-review"

# 监控子 Agent
openclaw subagents list
openclaw subagents steer <target> --message "请重点关注安全问题"
```

### 5.4 远程访问方案

#### Tailscale 集成
```json5
{
  gateway: {
    tailscale: {
      mode: "serve",  // serve = 仅 tailnet，funnel = 公网
    }
  }
}
```

#### SSH 隧道
```bash
# 本地 → 远程 Gateway
ssh -N -L 18790:127.0.0.1:18789 user@gateway-host

# 然后连接本地端口
openclaw agent --message "Hello" --host 127.0.0.1 --port 18790
```

---

## 六、故障排查速查

### 6.1 快速诊断

```bash
# 全面健康检查
openclaw doctor

# Gateway 状态
openclaw gateway status
openclaw gateway logs --follow

# 通道状态
openclaw channels status --probe

# Agent 状态
openclaw agents list --bindings
```

### 6.2 常见问题

| 问题 | 排查步骤 |
|------|----------|
| 消息收不到 | 检查 `channels.<channel>.allowFrom` 和 `dmPolicy` |
| 工具调用失败 | 检查沙盒配置和 `tools.allow`/`tools.deny` |
| 浏览器无法启动 | 检查 Playwright 安装和可执行路径 |
| 节点命令失败 | 确认节点在线且应用在前台 |
| Cron 任务不执行 | 检查 `cron.enabled` 和 Gateway 持续运行 |

---

## 七、资源与社区

### 官方资源
- **官网**：https://openclaw.ai
- **文档**：https://docs.openclaw.ai
- **GitHub**：https://github.com/openclaw/openclaw
- **Discord**：https://discord.gg/clawd

### 技能市场
- **ClawHub**：https://clawhub.com — 发现和安装社区技能

### 推荐关注
- **Twitter/X**：@openclaw — 获取最新动态
- **Showcase**：https://docs.openclaw.ai/start/showcase — 社区项目展示

---

## 八、总结

OpenClaw 的核心价值在于：

1. **隐私优先**：自托管意味着你的对话和数据完全在自己控制之下
2. **无处不在**：通过日常使用的聊天应用随时访问 AI 助手
3. **能力强大**：从代码编写到浏览器自动化，从文件管理到设备控制
4. **灵活扩展**：技能系统让功能无限扩展
5. **多用户支持**：多 Agent 架构支持家庭或团队共享

**建议入门路径**：
1. 运行 `openclaw onboard --install-daemon` 完成初始化
2. 配置 1-2 个通道（推荐 WhatsApp 或 Telegram）
3. 从简单的文件操作和代码问答开始
4. 逐步探索浏览器自动化和定时任务
5. 根据需要添加更多技能和集成

---

*本文档基于 OpenClaw 官方文档和社区 Showcase 整理*
