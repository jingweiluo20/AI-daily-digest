# AI 行业中文日报

一个 AI 驱动的每日信息聚合工具,整合国内 30 个头部 AI 公众号和海外 AI builders 的最新动态,生成结构化中文日报。

## 你会得到什么

一份结构清晰的中文日报,包含:

- 国内 30 个头部 AI 公众号最新文章(大模型厂商官方号 + 晚点LatePost、硅基观察Pro、Founder Park 等三方媒体)
- 25+ 位海外 AI builders 在 X/Twitter 上的关键观点(Swyx、Kevin Weil、Andrej Karpathy 等)
- 所有原始内容的链接
- 国内在前、海外在后的分区结构,适合快速阅读

## 安装(作为 Claude Code / Mira Skill)

> ⚠️ 安装时务必使用下方命令,本地文件夹名必须是 `AI-daily-digest`,否则 skill 名字会注册错误。

```bash
git clone https://github.com/jingweiluo20/AI-daily-digest.git ~/.claude/skills/AI-daily-digest
```

安装完成后,在 Claude Code / Mira 中输入 `/AI-daily-digest` 即可触发。

## 自动化(GitHub Actions)

仓库内置定时任务 `.github/workflows/daily-digest.yml`,每天自动:
1. 抓取国内公众号 + 海外 builders 最新内容
2. 用 DeepSeek 生成中文日报
3. Commit 到 `digests/` 目录归档
4. 推送到飞书群(如配置了 `FEISHU_WEBHOOK`)

### 需要配置的 Secrets

在 repo Settings → Secrets and variables → Actions 添加:

- `LLM_API_KEY`:DeepSeek API Key(必填)
- `FEISHU_WEBHOOK`:飞书机器人 webhook URL(可选,不填则只归档不推送)

## 文件结构

```
├── scripts/generate-digest.js   核心引擎(抓取 + 总结 + 推送)
├── feed-wechat.json             国内 30 个公众号 RSS 清单
├── .github/workflows/           GitHub Actions 定时任务
├── digests/                     每日日报归档
├── SKILL.md                     Mira/Claude Code Skill 定义
└── README.md
```
