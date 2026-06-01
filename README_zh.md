# SparkGlobe

> 基于 MarkWay 协议的 AI Agent 技能导航系统 — 自动分解用户任务，发现最佳 Agent 技能、工作流和专家角色。

## SparkGlobe 是什么？

SparkGlobe 是一个**基于 MarkWay 协议的技能导航索引**。它提供结构化的、协议兼容的目录，Agent 可以浏览该目录来发现、评估和安装适合任何任务的技能。

**核心理念**：用户任务 → 任务分解 → 拉取 MarkWay 索引 → 推荐技能 + Agent + 工作流。

## 功能特点

- **200+ 索引技能**，来自 [skills.sh](https://www.skills.sh/)，按 15 个分类组织
- **遵循 MarkWay 协议** — 每个页面都遵循 MarkWay 静态模式规范
- **自动任务分解** — SparkGlobe 技能将复杂任务分解并映射到技能分类
- **15 个技能分类**：前端 & React、Next.js、设计 & UI、移动端、Agent 工作流、数据库、测试、营销、AI 媒体生成、云 & 基础设施、文档处理、飞书/Lark 生态、代码质量 & 架构、浏览器自动化、开发者 & 研究工具

## 目录结构

```
SparkGlobe/
├── README.md                          # 英文说明
├── README_zh.md                       # 本文件（中文说明）
├── LICENSE                            # MIT 许可证
├── index.md                           # MarkWay 根索引（入口）
├── protocol.md                        # MarkWay 协议（简体中文）
├── protocol_en.md                     # MarkWay 协议（英文）
├── protocol_zh_TW.md                  # MarkWay 协议（繁体中文）
├── sparkglobe.md                      # SparkGlobe 技能文件（可安装到 Agent）
└── skillsIndex/                       # 技能分类页面
    ├── index.md                       # 分类总览 + 场景推荐
    ├── frontend.md                    # 前端 & React（6 个技能）
    ├── nextjs.md                      # Next.js（7 个技能）
    ├── design.md                      # 设计 & UI（19 个技能）
    ├── mobile.md                      # 移动端（6 个技能）
    ├── agent-workflows.md             # Agent 工作流（21 个技能）
    ├── databases.md                   # 数据库（15 个技能）
    ├── testing.md                     # 测试（5 个技能）
    ├── marketing.md                   # 营销（24 个技能）
    ├── ai-media.md                    # AI 媒体生成（26 个技能）
    ├── cloud-infra.md                 # 云 & 基础设施（18 个技能）
    ├── document-processing.md         # 文档处理（5 个技能）
    ├── lark.md                        # 飞书/Lark 生态（16 个技能）
    ├── code-quality.md                # 代码质量 & 架构（20+ 个技能）
    ├── browser-automation.md          # 浏览器自动化（7 个技能）
    └── dev-tools.md                   # 开发者 & 研究工具（13 个技能）
```

## 工作原理

### Agent 使用方式

1. **拉取** `index.md` 发现所有技能分类
2. **分解** 用户任务为子任务
3. **拉取** 相关分类页面 `skillsIndex/{category}.md`
4. **推荐** 具体技能并提供 `npx skills add` 安装命令

### 人工浏览

直接浏览 [skillsIndex/](skillsIndex/) 目录按分类查找技能，或安装 SparkGlobe 技能让 Agent 自动完成发现。

## 参考资源

SparkGlobe 整合了三个互补资源，提供全面的 Agent 能力发现：

### 1. 技能库 — [skills.sh](https://www.skills.sh/)

主要数据来源。Skills.sh 是由 [Vercel Labs](https://github.com/vercel-labs/skills) 维护的开放 Agent 技能生态系统，托管了 200+ 个可通过 `npx skills add` 安装的可复用 Agent 能力。SparkGlobe 将这些技能索引并组织为 15 个可导航分类。

### 2. Superpowers — [github.com/obra/superpowers](https://github.com/obra/superpowers)（代码任务必选）

**所有编码任务必须使用。** Superpowers 提供严格的开发工作流，防止 Agent 常见失败模式：

- **brainstorming** — 实现前探索意图和需求
- **writing-plans** — 编码前编写结构化实施计划
- **test-driven-development** — 先写失败测试，再实现
- **systematic-debugging** — 假设驱动调试：观察 → 假设 → 测试 → 验证
- **verification-before-completion** — 先验证再声明完成，证据优先于断言
- **executing-plans** — 逐步执行，含检查点
- **requesting-code-review** / **receiving-code-review** — 严格的代码评审工作流
- **finishing-a-development-branch** — 完整的分支生命周期清单
- **dispatching-parallel-agents** / **subagent-driven-development** — 并行 Agent 编排
- **using-git-worktrees** — 隔离的功能开发

安装：`npx skills add obra/superpowers`

### 3. The Agency — [github.com/msitarzewski/agency-agents](https://github.com/msitarzewski/agency-agents)

144+ 个专业化 AI Agent 角色，分布在 12 个部门（工程、设计、付费媒体、销售、营销、产品、项目管理、测试、支持、空间计算、专业领域、游戏开发）。每个 Agent 拥有独特的个性、定义好的工作流、交付物和成功指标。

安装：
```bash
git clone https://github.com/msitarzewski/agency-agents
cd agency-agents && ./scripts/install.sh --tool claude-code
```

### 三者如何协同

| 资源 | 提供什么 | 何时使用 |
|------|---------|---------|
| **SparkGlobe 索引** | 技能发现与导航 | 为任务找到合适的工具 |
| **Superpowers** | 严格的编码工作流 | **所有编码任务，无例外** |
| **The Agency** | 专家 Agent 角色 | 需要专家视角的复杂项目 |

## MarkWay 协议

SparkGlobe 遵循 [MarkWay 协议](protocol.md) — 一个为 AI Agent 设计的 HTTP 协议标准，将网页内容转换为结构化 Markdown。本仓库中的每个页面都符合 MarkWay 规范：

- 根索引位于 `index.md`
- 分类索引位于 `skillsIndex/index.md`
- 协议发现通过 `protocol_en.md`
- 所有链接使用 `.md` 路径
- 所有目录清单使用表格格式，包含 `Address` 和 `Description` 列

## 安装

### 作为技能安装

将技能文件复制到你的 Agent 技能目录：

```bash
# Claude Code
cp sparkglobe.md ~/.claude/skills/

# 在 Agent 会话中，当你请求查找技能时 SparkGlobe 会自动激活
```

### 直接浏览索引

Agent 可以通过 raw GitHub URL 直接拉取任何页面：

```
https://raw.githubusercontent.com/RaysunKR/SparkGlobe/main/index.md
https://raw.githubusercontent.com/RaysunKR/SparkGlobe/main/skillsIndex/{category}.md
```

## 许可证

[MIT](LICENSE) — RaysunKR
