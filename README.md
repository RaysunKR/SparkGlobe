<div align="center">

# 🌐 SparkGlobe

**AI Agent Skill Navigator**

*Decompose user tasks. Discover the best skills, workflows, and specialist agents.*

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Protocol: MarkWay](https://img.shields.io/badge/Protocol-MarkWay-blue.svg)](protocol_en.md)
[![Skills Indexed](https://img.shields.io/badge/Skills_Indexed-200+-green.svg)](skillsIndex/)
[![中文说明](https://img.shields.io/badge/README-中文-red.svg)](README_zh.md)

</div>

---

## ✨ What Is SparkGlobe?

SparkGlobe is a **MarkWay-protocol navigation index** that helps AI agents automatically discover, evaluate, and install the right skills for any task.

```
User Task → Task Decomposition → Fetch MarkWay Index → Recommend Skills + Agents + Workflows
```

**Why SparkGlobe?** Instead of agents guessing which tools to use, SparkGlobe provides a structured, protocol-compliant directory they can browse — like a **GPS for agent capabilities**.

| | |
|---|---|
| 🗂️ **200+ indexed skills** | From [skills.sh](https://www.skills.sh/), organized into 15 categories |
| 📡 **MarkWay protocol** | Every page follows the [MarkWay](protocol_en.md) static mode spec |
| 🧠 **Auto task decomposition** | Breaks down complex tasks and maps sub-tasks to skill categories |
| 🔗 **3 integrated resources** | Skills + Superpowers + The Agency in one navigation system |

---

## 🚀 Quick Start

### Install the SparkGlobe Skill

```bash
# Install via skills.sh CLI
npx skills add RaysunKR/SparkGlobe

# Or manually for Claude Code
cp skills/sparkglobe/SKILL.md ~/.claude/skills/
```

### Browse the Index Directly

Agents can fetch any page via raw GitHub URLs:

```
https://raw.githubusercontent.com/RaysunKR/SparkGlobe/master/index.md
https://raw.githubusercontent.com/RaysunKR/SparkGlobe/master/skillsIndex/{category}.md
```

---

## 📂 Directory Structure

```
SparkGlobe/
├── 📄 README.md                          # You are here
├── 📄 README_zh.md                       # 中文说明
├── 📄 LICENSE                            # MIT License
├── 📡 index.md                           # ← MarkWay root index (entry point)
├── 📡 skillsIndex/                       # Skill category pages
│   ├── index.md                          # Category overview + scenario guide
│   ├── frontend.md                       # 🖥️ Frontend & React (6 skills)
│   ├── nextjs.md                         # ▲ Next.js (7 skills)
│   ├── design.md                         # 🎨 Design & UI (19 skills)
│   ├── mobile.md                         # 📱 Mobile (6 skills)
│   ├── agent-workflows.md                # 🤖 Agent Workflows (21 skills)
│   ├── databases.md                      # 🗄️ Databases (15 skills)
│   ├── testing.md                        # 🧪 Testing (5 skills)
│   ├── marketing.md                      # 📢 Marketing (24 skills)
│   ├── ai-media.md                       # 🎬 AI Media Generation (26 skills)
│   ├── cloud-infra.md                    # ☁️ Cloud & Infrastructure (18 skills)
│   ├── document-processing.md            # 📑 Document Processing (5 skills)
│   ├── lark.md                           # 🐦 Lark/Feishu Ecosystem (16 skills)
│   ├── code-quality.md                   # 💎 Code Quality & Architecture (20+ skills)
│   ├── browser-automation.md             # 🌐 Browser Automation (7 skills)
│   └── dev-tools.md                      # 🔧 Developer & Research Tools (13 skills)
├── 🔧 skills/sparkglobe/SKILL.md         # Installable skill file
├── 📡 protocol_en.md                     # MarkWay Protocol Specification
├── 📡 protocol.md                        # MarkWay 协议规范（简体中文）
├── 📡 protocol_zh_TW.md                  # MarkWay 協議規範（繁體中文）
└── skills.sh.json                        # skills.sh repo configuration
```

---

## 🧭 How It Works

### For Agents

```
┌──────────────┐    ┌───────────────┐    ┌──────────────────┐    ┌─────────────────┐
│  User Task   │───▶│  Decompose    │───▶│  Fetch MarkWay   │───▶│  Recommend      │
│  "Build app" │    │  into subtasks│    │  category pages  │    │  skills + agents│
└──────────────┘    └───────────────┘    └──────────────────┘    └─────────────────┘
```

1. **Fetch** `index.md` to discover all 15 skill categories
2. **Decompose** the user's task into distinct sub-tasks
3. **Fetch** relevant category pages from `skillsIndex/{category}.md`
4. **Recommend** specific skills with `npx skills add` install commands

### For Humans

Browse the [skillsIndex/](skillsIndex/) directory to find skills by category, or install the SparkGlobe skill and let your agent handle discovery.

---

## 🔗 Referenced Resources

SparkGlobe integrates three complementary resources for comprehensive agent capability discovery:

### 1. 🧩 Skills — [skills.sh](https://www.skills.sh/)

The primary data source. The open agent skills ecosystem by [Vercel Labs](https://github.com/vercel-labs/skills) hosts 200+ reusable agent capabilities installable via `npx skills add`. SparkGlobe indexes these into 15 navigable categories.

```bash
npx skills add <owner/repo/skill-name>
```

### 2. ⚡ Superpowers — [obra/superpowers](https://github.com/obra/superpowers)

> ⚠️ **MANDATORY for all coding tasks — no exceptions.**

Disciplined development workflows that prevent common agent failure modes:

| Skill | Purpose |
|-------|---------|
| `brainstorming` | Explore intent and requirements before implementation |
| `writing-plans` | Structured plans before touching code |
| `test-driven-development` | Failing test → implement → refactor |
| `systematic-debugging` | observe → hypothesize → test → verify |
| `verification-before-completion` | Evidence before assertions |
| `executing-plans` | Step-by-step with checkpoints |
| `requesting-code-review` | Self-review + coverage + PR description |
| `receiving-code-review` | Technical rigor, not blind agreement |
| `finishing-a-development-branch` | Tests, commits, PR, review checklist |
| `dispatching-parallel-agents` | Split work across parallel subagents |

```bash
npx skills add obra/superpowers
```

### 3. 🎭 The Agency — [msitarzewski/agency-agents](https://github.com/msitarzewski/agency-agents)

144+ specialized AI agent personalities across 12 divisions. Each agent has a unique personality, defined workflows, deliverables, and success metrics.

| Division | Key Agents |
|----------|------------|
| 💻 Engineering | Frontend Developer, Backend Architect, AI Engineer, DevOps, Security |
| 🎨 Design | UI Designer, UX Researcher, Brand Guardian, Whimsy Injector |
| 💰 Paid Media | PPC Strategist, Paid Media Auditor, Tracking Specialist |
| 💼 Sales | Outbound Strategist, Deal Strategist, Discovery Coach |
| 📢 Marketing | Growth Hacker, SEO Specialist, Content Creator |
| 📊 Product | Product Manager, Sprint Prioritizer, Trend Researcher |
| 🎬 Project Mgmt | Studio Producer, Project Shepherd, Jira Steward |
| 🧪 Testing | Evidence Collector, Reality Checker, API Tester |
| 🎮 Game Dev | Unity, Unreal, Godot, Roblox, Blender specialists |
| 🥽 Spatial | XR Architect, visionOS Engineer, WebXR Developer |

```bash
git clone https://github.com/msitarzewski/agency-agents
cd agency-agents && ./scripts/install.sh --tool claude-code
```

### How They Work Together

```
┌──────────────────┐   ┌──────────────────┐   ┌──────────────────┐
│   SparkGlobe     │   │   Superpowers    │   │   The Agency     │
│                  │   │                  │   │                  │
│  What tool to    │   │  How to code     │   │  Who to assign   │
│  use for a task  │   │  with discipline │   │  as an expert    │
├──────────────────┤   ├──────────────────┤   ├──────────────────┤
│  Skill discovery │   │  Every coding    │   │  Complex projects│
│  & navigation    │   │  task — always   │   │  needing expert  │
│                  │   │                  │   │  perspectives    │
└──────────────────┘   └──────────────────┘   └──────────────────┘
```

---

## 📡 MarkWay Protocol

SparkGlobe follows the [MarkWay protocol](protocol_en.md) — an HTTP protocol standard designed for AI Agents that converts web content into structured Markdown.

Every `.md` page in this repository is MarkWay-compliant:

- ✅ Root index at `index.md`
- ✅ Category indexes in `skillsIndex/index.md`
- ✅ Protocol discovery via `protocol_en.md`
- ✅ All links end with `.md`
- ✅ All directory listings use `Address | Description` table format
- ✅ All relative paths start with `./`

---

## 📄 License

[MIT](LICENSE) — © [RaysunKR](https://github.com/RaysunKR)
