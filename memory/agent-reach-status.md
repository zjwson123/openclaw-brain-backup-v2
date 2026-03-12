# 🌐 Agent Reach 安装状态

*安装时间：2026-03-12*
*环境：macOS ARM64 (Apple Silicon)*
*最后更新：2026-03-13*

---

## ✅ 已安装完成（10/15 渠道）

### 立即可用

| 渠道 | 状态 | 说明 |
|------|------|------|
| **GitHub** | ✅ | 仓库、代码、搜索、Fork、Issue、PR |
| **YouTube** | ✅ | 视频下载、字幕提取 |
| **Twitter/X** | ✅ | 推文搜索、读取（含长文）|
| **RSS/Atom** | ✅ | 订阅源读取 |
| **全网语义搜索** | ✅ | Exa 搜索，免费无需 API Key |
| **任意网页** | ✅ | Jina Reader 读取 |
| **B站** | ✅ | 视频、字幕提取 |
| **微博** | ✅ | 热搜、搜索、用户动态、评论 |
| **抖音** | ✅ | 视频解析、无水印下载（服务运行在 :18070）|
| **微信公众号** | ✅ | 文章阅读、搜索工具已安装 |

### 待配置（需要额外设置）

| 渠道 | 状态 | 所需配置 |
|------|------|----------|
| **小红书** | ⏳ | Docker MCP 服务（ARM64需源码构建）|
| **小宇宙播客** | ⏳ | Groq API Key（免费）|
| **Reddit** | ⏳ | 代理配置（服务器 IP 可能被封锁）|
| **LinkedIn** | ⏳ | 需要浏览器登录（见下方说明）|
| **V2EX** | ⚠️ | 连接超时，可能需要代理 |

---

## 🔧 使用方式

### 基础命令

```bash
# 激活环境
source ~/.agent-reach-venv/bin/activate

# 状态检查
agent-reach doctor

# 查看更新
agent-reach check-update
```

### 各平台使用示例

**Twitter/X 搜索：**
```bash
xreach search "自动驾驶" --json
```

**YouTube 字幕提取：**
```bash
yt-dlp --list-subs "URL"
yt-dlp --write-subs --sub-langs zh-CN "URL"
```

**B站视频：**
```bash
yt-dlp --dump-json "https://www.bilibili.com/video/xxxxx"
```

**微博热搜：**
```bash
mcporter call 'weibo.get_trendings(limit: 10)'
```

**抖音视频：**
```bash
mcporter call 'douyin.parse_douyin_video_info(url: "https://v.douyin.com/xxxxx")'
```

**微信公众号搜索：**
```bash
python3 -m miku_ai.search "关键词"
```

**任意网页：**
```bash
curl -s "https://r.jina.ai/https://example.com"
```

**全网语义搜索：**
```bash
mcporter call 'exa.web_search_exa(query: "AI Agent", num_results: 5)'
```

---

## 📋 待配置说明

### 1. 小红书（ARM64 需源码构建）
```bash
# 克隆并构建
git clone https://github.com/xpzouying/xiaohongshu-mcp.git ~/.agent-reach/tools/xiaohongshu-mcp
cd ~/.agent-reach/tools/xiaohongshu-mcp
docker build -t xiaohongshu-mcp .
docker run -d --name xiaohongshu-mcp -p 18060:18060 xiaohongshu-mcp
mcporter config add xiaohongshu http://localhost:18060/mcp

# 登录方式（使用 Cookie-Editor）：
# 1. 浏览器登录小红书 (xiaohongshu.com)
# 2. Cookie-Editor 插件 → Export → Header String
# 3. agent-reach configure xhs-cookies "key1=val1; key2=val2"
```

### 2. 小宇宙播客转文字
```bash
# 1. 获取免费 Groq API Key: https://console.groq.com（30秒注册，无需信用卡）
# 2. 配置
agent-reach configure groq-key gsk_xxxxx

# 使用方式
bash ~/.agent-reach/tools/xiaoyuzhou/transcribe.sh https://www.xiaoyuzhoufm.com/episode/xxxxx
```

### 3. LinkedIn（需要浏览器登录）
```bash
# 方式1：本地有桌面环境
linkedin-scraper-mcp --login --no-headless
# 浏览器会弹出，手动登录 LinkedIn

# 方式2：使用 VNC（服务器环境）
# 登录后启动服务
linkedin-scraper-mcp --transport streamable-http --port 8001
mcporter config add linkedin http://localhost:8001/mcp
```

### 4. Reddit
```bash
# 需要住宅代理（服务器 IP 被封锁）
# 获取代理：https://webshare.io ($1/month)
agent-reach configure proxy http://user:pass@ip:port
```

---

## 🔐 安全配置（如需要）

**Twitter/X Cookie（如需发帖或完整搜索）：**
```bash
# 1. 浏览器登录 Twitter
# 2. Cookie-Editor 插件 → Export → Header String
# 3. 配置
agent-reach configure twitter-cookies "key1=val1; key2=val2"
```

**代理配置：**
```bash
agent-reach configure proxy http://user:pass@ip:port
```

---

## 📝 备注

- 安装路径：`~/.agent-reach-venv/`
- 配置文件：`~/.agent-reach/config.json`
- 工具目录：`~/.agent-reach/tools/`
- 已集成到 Claude Code Skill: `~/.claude/skills/agent-reach`
- 抖音服务运行在 `localhost:18070`

---

## 🆕 更新记录

- **2026-03-13**: 完成抖音、微信公众号工具安装配置
- **2026-03-12**: 基础安装完成，8个渠道可用

---

*最后更新：2026-03-13*
