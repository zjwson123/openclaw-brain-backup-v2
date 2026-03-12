# Prompt Engineering 最佳实践

从 Cursor Agent 2.0 和 Claude Code 2.0 系统提示词中提取的最佳实践

---

## 1. 结构规范

### 1.1 分层组织
```
系统上下文 → 工具定义 → 使用规范 → 输出格式 → 安全策略
```

### 1.2 使用 XML 标签进行语义分区
- `<tool_calling>` - 工具调用规范
- `<citing_code>` - 代码引用规范  
- `<system_reminder>` - 系统提醒（动态注入）
- `<env>` - 环境信息
- `<example>` / `<good-example>` / `<bad-example>` - 示例

### 1.3 动态内容占位
- 使用占位符如 `{{USER_QUERY}}`、`{{WORKSPACE}}`
- 在运行时注入上下文信息

---

## 2. 工具定义最佳实践

### 2.1 详细的参数说明
每个参数都应包含：
- `description` - 清晰描述用途
- `type` - 明确数据类型
- 必要时添加 `enum` 限制取值范围
- `required` 数组明确必填字段

### 2.2 工具选择指南（When to Use / When NOT to Use）
为每个工具提供明确的使用场景：
```
### When to Use This Tool
- 场景1: ...
- 场景2: ...

### When NOT to Use
- 场景1: ...
- 场景2: ...
```

### 2.3 提供具体示例
- 正面示例（Good）
- 反面示例（Bad）
- 解释为什么好/坏

---

## 3. 输出格式规范

### 3.1 代码引用格式（CODE REFERENCES）
**格式**: ```startLine:endLine:filepath
```
**要求**:
- 必须包含起始行号、结束行号、文件路径
- 不要添加语言标签
- 代码块前必须有空行

### 3.2 行号处理
- 代码块中收到的行号格式: `LINE_NUMBER|LINE_CONTENT`
- 将 `LINE_NUMBER|` 视为元数据，不视为代码内容

### 3.3 代码块规范
- 代码块开头不要缩进（即使出现在列表中）
- 代码块前必须有空行
- 代码块内不要包含行号

---

## 4. 任务管理规范

### 4.1 使用 Todo 列表
- 复杂任务（3+ 步骤）必须创建 todo
- 实时更新状态：pending → in_progress → completed
- 一次只能有一个 in_progress

### 4.2 任务完成标准
- 只有完全完成才能标记 completed
- 遇到错误保持 in_progress
- 及时标记完成，不要批量更新

---

## 5. 安全与边界

### 5.1 安全声明
```
IMPORTANT: Assist with defensive security tasks only.
Refuse to create, modify, or improve code that may be used maliciously.
```

### 5.2 破坏性操作确认
- 执行破坏性命令前必须确认
- 提供 `--yes` 等非交互式标志
- Git 操作安全协议（不强制推送、不修改配置等）

### 5.3 权限边界
- 不读取 ~/.ssh、~/.env 等敏感文件
- 不协助凭证发现或挖掘

---

## 6. 语气与风格

### 6.1 简洁优先
- 回复一般少于 4 行（不包括工具调用）
- 只在复杂任务时提供详细信息
- 避免不必要的前言和后缀

### 6.2 专业客观
- 技术准确性优先于迎合用户
- 必要时礼貌地纠正用户
- 不确定时先调查再回答

### 6.3 主动性平衡
- 用户要求时才主动
- 做正确的事，但不擅自行动
- 先回答问题，再采取行动

---

## 7. 代码编辑规范

### 7.1 编辑原则
- 优先编辑现有文件，而非创建新文件
- 阅读文件后再编辑（Read before Edit）
- 提供足够的上下文确保唯一性

### 7.2 代码完整性
- 生成的代码必须可立即运行
- 包含必要的导入语句
- 提供依赖管理文件（requirements.txt 等）

### 7.3 错误处理
- 引入错误时负责修复
- 同一文件最多修复 3 次
- 之后询问用户如何处理

---

## 8. 工具调用最佳实践

### 8.1 并行调用
- 独立任务可以并行调用
- 依赖任务使用 `&&` 串联

### 8.2 专用工具优先
- 文件搜索用 Glob，不用 find
- 内容搜索用 Grep，不用 grep/rg
- 读取文件用 Read，不用 cat/head/tail
- 编辑文件用 Edit，不用 sed/awk

### 8.3 命令执行规范
- 终端操作用 Bash
- 文件操作用专用工具
- 避免使用 echo/printf 与用户通信

---

## 9. 上下文管理

### 9.1 知识截断声明
```
Knowledge cutoff: 2024-06
```

### 9.2 环境信息注入
```
<env>
Working directory: {{WORK_DIR}}
Is directory a git repo: {{IS_GIT}}
Platform: {{PLATFORM}}
</env>
```

### 9.3 系统提醒（System Reminders）
- 自动附加但不直接响应
- 包含重要指令提醒
- 动态注入用户上下文

---

## 10. 可复用的 Prompt 模板

### 10.1 工具定义模板
```typescript
type tool_name = (_: {
  // 参数说明，用自然语言描述
  param1: string,
  // 可选参数
  param2?: boolean,
}) => any;
```

### 10.2 示例模板
```xml
<example>
user: 用户输入
assistant: 期望输出
</example>

<good-example>
正确做法 + 解释
</good-example>

<bad-example>
错误做法 + 解释
</bad-example>
```

### 10.3 系统提示模板
```markdown
# 版本信息
Version: X.X.X
Release Date: YYYY-MM-DD

# System Prompt
你是...，帮助用户...

## 安全声明
...

## 语气风格
...

## 工具使用
...

## 代码规范
...

<env>
环境信息...
</env>
```

---

## 11. 反模式（Anti-patterns）

### ❌ 避免
- 过长的系统提示（>50KB 可能影响性能）
- 模糊的工具描述
- 不明确的输出格式要求
- 缺乏安全边界的提示
- 过度主动或过度保守的行为模式

### ✅ 推荐
- 清晰的工具选择指南
- 具体的输入/输出示例
- 明确的边界和限制
- 平衡主动性和用户控制
- 可预测的行为模式

---

*提取自 Cursor Agent 2.0 和 Claude Code 2.0 系统提示词*
*日期: 2026-03-05*
