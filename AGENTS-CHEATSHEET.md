# 🎯 代理速查手册

## 快速选择指南

不知道用哪个代理？根据你的场景直接选：

### 🚗 自动驾驶/嵌入式开发
| 场景 | 代理 | 激活词 |
|------|------|--------|
| 嵌入式固件开发 | embedded-firmware-engineer | "激活嵌入式工程师" |
| 系统架构设计 | software-architect | "激活架构师" |
| 代码审查 | code-reviewer | "审查这段代码" |
| 安全审计 | security-engineer | "安全审查" |
| 系统可靠性 | sre-site-reliability-engineer | "激活SRE" |

### 💻 通用软件开发
| 场景 | 代理 | 激活词 |
|------|------|--------|
| 前端开发 | frontend-developer | "激活前端" |
| 后端架构 | backend-architect | "激活后端" |
| API设计 | backend-architect | "设计API" |
| 数据库优化 | database-optimizer | "优化数据库" |
| DevOps/CI | devops-automator | "激活DevOps" |
| AI功能集成 | ai-engineer | "激活AI工程师" |

### 🔍 查找代理命令

```bash
# 搜索包含关键字的代理
ls ~/.openclaw/agency-agents/ | grep -i "关键字"

# 查看所有代理分类
ls ~/.openclaw/agency-agents/ | head -20

# 查看工程类代理
ls ~/.openclaw/agency-agents/ | grep -E "(engineering|embedded|backend|frontend|security|code)"
```

### 🎮 自然语言激活（推荐）

不用记具体名称，用自然语言描述你的需求，我来帮你匹配：

**你可以直接说：**
- "帮我审查这段代码" → 自动激活 code-reviewer
- "设计系统架构" → 自动激活 software-architect
- "这段固件代码有问题" → 自动激活 embedded-firmware-engineer
- "检查安全性" → 自动激活 security-engineer
- "优化数据库查询" → 自动激活 database-optimizer

### 📋 常用代理 TOP 10

1. **code-reviewer** - 代码审查（最常用）
2. **embedded-firmware-engineer** - 嵌入式开发
3. **software-architect** - 架构设计
4. **security-engineer** - 安全审计
5. **backend-architect** - 后端/API设计
6. **database-optimizer** - 数据库优化
7. **devops-automator** - CI/CD自动化
8. **sre-site-reliability-engineer** - 系统可靠性
9. **ai-engineer** - AI模型集成
10. **technical-writer** - 技术文档

### 🔧 快速查看所有代理

```bash
# 列出所有代理
openclaw agents list

# 或者
ls ~/.openclaw/agency-agents/ | nl
```

---

**💡 提示**：下次使用时，直接描述你的需求，我会自动推荐合适的代理！
