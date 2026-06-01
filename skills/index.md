https://raw.githubusercontent.com/RaysunKR/SparkGlobe/main

> This site follows the MarkWay Protocol: https://raw.githubusercontent.com/RaysunKR/SparkGlobe/main/protocol_en.md

# 技能分类总览

skills.sh 全站技能分类索引，按领域分组。

| 分类 | 技能数 | 地址 | 说明 |
|------|--------|------|------|
| 前端 & React | 6 | ./frontend.md | React 性能规则、组件模式、Tailwind 设计系统、shadcn/ui |
| Next.js | 7 | ./nextjs.md | App Router、Server Components、缓存 API、Vercel 部署 |
| 设计 & UI | 16 | ./design.md | 前端设计模式、视觉打磨、设计系统提取、交互动效 |
| 移动端 | 6 | ./mobile.md | React Native、Expo 原生 UI、数据获取、NativeWind |
| Agent 工作流 | 20 | ./agent-workflows.md | 计划编写、调试循环、TDD、子 Agent 调度、自动循环 |
| 数据库 | 13 | ./databases.md | Postgres、Supabase、Firebase、Convex、Neon、Drizzle ORM |
| 测试 | 5 | ./testing.md | TDD 循环、Playwright 自动化、Web 测试、验证流程 |
| 营销 | 21 | ./marketing.md | SEO、文案撰写、CRO、增长策略、邮件序列、付费广告 |
| AI 媒体生成 | 25+ | ./ai-media.md | AI 图像/视频/音乐生成、换脸、图像修复、视频扩展 |
| 云 & 基础设施 | 20+ | ./cloud-infra.md | Azure 全栈服务、Firebase、Kubernetes、云迁移与成本优化 |
| 文档处理 | 5 | ./document-processing.md | PPTX/PDF/DOCX/XLSX 文件创建与解析、Canvas 设计 |
| 飞书/Lark | 30+ | ./lark.md | 飞书全功能 API：文档、多维表格、消息、审批、OKR、日历 |
| 代码质量 & 架构 | 20+ | ./code-quality.md | 代码审查、架构改进、TDD、诊断、PRD 生成、Caveman 工具链 |
| 浏览器自动化 | 3 | ./browser-automation.md | 网页操作、表单填写、截图、数据提取 |
| 开发者工具 | 8 | ./dev-tools.md | GitHub Actions、Linux 云安全、用户脚本、AI 论文复现 |

## 按场景查找技能

| 用户场景 | 推荐分类 |
|---------|---------|
| 构建 Web 应用 | frontend.md → nextjs.md → design.md → testing.md |
| 移动 App 开发 | mobile.md → design.md → databases.md |
| Agent 自动化 | agent-workflows.md → browser-automation.md → dev-tools.md |
| 营销增长 | marketing.md → design.md → ai-media.md |
| AI 内容创作 | ai-media.md → document-processing.md |
| 后端 & 数据库 | databases.md → cloud-infra.md → code-quality.md |
| 企业协作 | lark.md → document-processing.md → code-quality.md |
| 代码质量提升 | code-quality.md → testing.md → agent-workflows.md |

## 安装技能

所有技能均通过 skills.sh 安装：

```bash
npx skills add <owner/repo/skill-name>
```

例如：
```bash
npx skills add anthropics/skills/frontend-design
npx skills add obra/superpowers/brainstorming
npx skills add mattpocock/skills/grill-me
```

访问 [skills.sh](https://www.skills.sh/) 查看完整技能目录。
