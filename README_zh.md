<div align="center">

# 🌐 SparkGlobe

**AI Agent 技能导航系统**

*自动分解用户任务，发现最佳技能、工作流和专家 Agent。*

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Protocol: MarkWay](https://img.shields.io/badge/Protocol-MarkWay-blue.svg)](protocol.md)
[![Skills Indexed](https://img.shields.io/badge/Skills_Indexed-200+-green.svg)](skillsIndex/)
[![English README](https://img.shields.io/badge/README-English-blue.svg)](README.md)

</div>

---

## ✨ SparkGlobe 是什么？

SparkGlobe 是一个**基于 MarkWay 协议的技能导航索引**，帮助 AI Agent 自动发现、评估和安装适合任何任务的技能。

```
用户任务 → 任务分解 → 拉取 MarkWay 索引 → 推荐技能 + Agent + 工作流
```

**为什么用 SparkGlobe？** 与其让 Agent 猜测用什么工具，SparkGlobe 提供一个结构化、协议兼容的目录供浏览 —— 就像 **Agent 能力的 GPS**。

| | |
|---|---|
| 🗂️ **200+ 索引技能** | 来自 [skills.sh](https://www.skills.sh/)，按 15 个分类组织 |
| 📡 **MarkWay 协议** | 每个页面都遵循 [MarkWay](protocol.md) 静态模式规范 |
| 🧠 **自动任务分解** | 将复杂任务分解并映射到技能分类 |
| 🔗 **3 大整合资源** | 技能 + Superpowers + The Agency，一个导航系统搞定 |

---

## 🚀 快速开始

### 安装 SparkGlobe 技能

```bash
# 通过 skills.sh CLI 安装
npx skills add RaysunKR/SparkGlobe

# 或手动安装到 Claude Code
cp skills/sparkglobe/SKILL.md ~/.claude/skills/
```

### 直接浏览索引

Agent 可通过 raw GitHub URL 直接拉取任何页面：

```
https://raw.githubusercontent.com/RaysunKR/SparkGlobe/master/index.md
https://raw.githubusercontent.com/RaysunKR/SparkGlobe/master/skillsIndex/{category}.md
```

---

## 📂 目录结构

```
SparkGlobe/
├── 📄 README.md                          # 英文说明
├── 📄 README_zh.md                       # 你在这里
├── 📄 LICENSE                            # MIT 许可证
├── 📡 index.md                           # ← MarkWay 根索引（入口）
├── 📡 skillsIndex/                       # 技能分类页面
│   ├── index.md                          # 分类总览 + 场景推荐
│   ├── frontend.md                       # 🖥️ 前端 & React（6 个技能）
│   ├── nextjs.md                         # ▲ Next.js（7 个技能）
│   ├── design.md                         # 🎨 设计 & UI（19 个技能）
│   ├── mobile.md                         # 📱 移动端（6 个技能）
│   ├── agent-workflows.md                # 🤖 Agent 工作流（21 个技能）
│   ├── databases.md                      # 🗄️ 数据库（15 个技能）
│   ├── testing.md                        # 🧪 测试（5 个技能）
│   ├── marketing.md                      # 📢 营销（24 个技能）
│   ├── ai-media.md                       # 🎬 AI 媒体生成（26 个技能）
│   ├── cloud-infra.md                    # ☁️ 云 & 基础设施（18 个技能）
│   ├── document-processing.md            # 📑 文档处理（5 个技能）
│   ├── lark.md                           # 🐦 飞书/Lark 生态（16 个技能）
│   ├── code-quality.md                   # 💎 代码质量 & 架构（20+ 个技能）
│   ├── browser-automation.md             # 🌐 浏览器自动化（7 个技能）
│   └── dev-tools.md                      # 🔧 开发者 & 研究工具（13 个技能）
├── 🔧 skills/sparkglobe/SKILL.md         # 可安装的技能文件
├── 📡 protocol_en.md                     # MarkWay Protocol Specification
├── 📡 protocol.md                        # MarkWay 协议规范（简体中文）
├── 📡 protocol_zh_TW.md                  # MarkWay 協議規範（繁體中文）
└── skills.sh.json                        # skills.sh 仓库配置
```

---

## 🧭 工作原理

### Agent 使用方式

```
┌──────────────┐    ┌───────────────┐    ┌──────────────────┐    ┌─────────────────┐
│   用户任务   │───▶│    分解任务   │───▶│  拉取 MarkWay    │───▶│    推荐         │
│  "构建应用"  │    │   为子任务    │    │  分类页面        │    │  技能 + Agent   │
└──────────────┘    └───────────────┘    └──────────────────┘    └─────────────────┘
```

1. **拉取** `index.md` 发现所有 15 个技能分类
2. **分解** 用户任务为子任务
3. **拉取** 相关分类页面 `skillsIndex/{category}.md`
4. **推荐** 具体技能并提供 `npx skills add` 安装命令

### 人工浏览

直接浏览 [skillsIndex/](skillsIndex/) 目录按分类查找技能，或安装 SparkGlobe 技能让 Agent 自动完成发现。

---

## 🔗 参考资源

SparkGlobe 整合了三个互补资源，提供全面的 Agent 能力发现：

### 1. 🧩 技能库 — [skills.sh](https://www.skills.sh/)

主要数据来源。[Vercel Labs](https://github.com/vercel-labs/skills) 维护的开放 Agent 技能生态系统，托管 200+ 个可通过 `npx skills add` 安装的可复用能力。SparkGlobe 将这些技能组织为 15 个可导航分类。

```bash
npx skills add <owner/repo/skill-name>
```

### 2. ⚡ Superpowers — [obra/superpowers](https://github.com/obra/superpowers)

> ⚠️ **所有编码任务必须使用，无例外。**

严格的开发工作流，防止 Agent 常见失败模式：

| 技能 | 用途 |
|------|------|
| `brainstorming` | 实现前探索意图和需求 |
| `writing-plans` | 编码前编写结构化实施计划 |
| `test-driven-development` | 失败测试 → 实现 → 重构 |
| `systematic-debugging` | 观察 → 假设 → 测试 → 验证 |
| `verification-before-completion` | 先验证再声明完成，证据优先 |
| `executing-plans` | 逐步执行，含检查点 |
| `requesting-code-review` | 自审 + 覆盖率 + PR 描述 |
| `receiving-code-review` | 技术严谨，不盲目同意 |
| `finishing-a-development-branch` | 测试、提交、PR、评审清单 |
| `dispatching-parallel-agents` | 拆分工作到并行子 Agent |

```bash
npx skills add obra/superpowers
```

### 3. 🎭 The Agency — [msitarzewski/agency-agents](https://github.com/msitarzewski/agency-agents)

144+ 个专业化 AI Agent 角色，分布在 12 个部门。每个 Agent 拥有独特个性、定义好的工作流、交付物和成功指标。

| 部门 | 关键 Agent |
|------|-----------|
| 💻 工程 | 前端开发、后端架构、AI 工程、DevOps、安全 |
| 🎨 设计 | UI 设计师、UX 研究员、品牌守护者、趣味注入师 |
| 💰 付费媒体 | PPC 策略师、付费媒体审计师、追踪专家 |
| 💼 销售 | 外发策略师、交易策略师、发现教练 |
| 📢 营销 | 增长黑客、SEO 专家、内容创作者 |
| 📊 产品 | 产品经理、冲刺优先级、趋势研究员 |
| 🎬 项目管理 | 制片人、项目牧羊人、Jira 管家 |
| 🧪 测试 | 证据收集者、现实检查者、API 测试员 |
| 🎮 游戏开发 | Unity、Unreal、Godot、Roblox、Blender 专家 |
| 🥽 空间计算 | XR 架构师、visionOS 工程师、WebXR 开发者 |

```bash
git clone https://github.com/msitarzewski/agency-agents
cd agency-agents && ./scripts/install.sh --tool claude-code
```

### 三者如何协同

```
┌──────────────────┐   ┌──────────────────┐   ┌──────────────────┐
│   SparkGlobe     │   │   Superpowers    │   │   The Agency     │
│                  │   │                  │   │                  │
│  用什么工具      │   │  如何规范地编码  │   │  安排谁来当专家  │
├──────────────────┤   ├──────────────────┤   ├──────────────────┤
│  技能发现        │   │  所有编码任务    │   │  需要专家视角    │
│  与导航          │   │  无例外必用      │   │  的复杂项目      │
└──────────────────┘   └──────────────────┘   └──────────────────┘
```

---

## 📡 MarkWay 协议

SparkGlobe 遵循 [MarkWay 协议](protocol.md) — 一个为 AI Agent 设计的 HTTP 协议标准，将网页内容转换为结构化 Markdown。

本仓库中每个 `.md` 页面都符合 MarkWay 规范：

- ✅ 根索引位于 `index.md`
- ✅ 分类索引位于 `skillsIndex/index.md`
- ✅ 协议发现通过 `protocol_en.md`
- ✅ 所有链接以 `.md` 结尾
- ✅ 所有目录清单使用 `Address | Description` 表格格式
- ✅ 所有相对路径以 `./` 开头

---

## 📄 许可证

[MIT](LICENSE) — © [RaysunKR](https://github.com/RaysunKR)
