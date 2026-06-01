# SparkGlobe

> An AI Agent skill navigator built on the MarkWay protocol — decompose user tasks and auto-discover the best agent skills, workflows, and specialist personalities.

## What Is SparkGlobe?

SparkGlobe is a **MarkWay-based navigation index** for AI agent skills. It provides a structured, protocol-compliant directory that agents can browse to discover, evaluate, and install the right skills for any task.

**Core idea**: User task → task decomposition → fetch MarkWay index → recommend skills + agents + workflows.

## Features

- **200+ indexed skills** from [skills.sh](https://www.skills.sh/), organized into 15 categories
- **MarkWay protocol compliant** — every page follows the MarkWay static mode specification
- **Auto task decomposition** — the SparkGlobe skill breaks down complex tasks and maps sub-tasks to skill categories
- **15 skill categories**: Frontend & React, Next.js, Design & UI, Mobile, Agent Workflows, Databases, Testing, Marketing, AI Media Generation, Cloud & Infrastructure, Document Processing, Lark/Feishu Ecosystem, Code Quality & Architecture, Browser Automation, Developer & Research Tools

## Directory Structure

```
SparkGlobe/
├── README.md                          # This file
├── README_zh.md                       # Chinese version
├── LICENSE                            # MIT License
├── index.md                           # MarkWay root index (entry point)
├── protocol.md                        # MarkWay protocol (Simplified Chinese)
├── protocol_en.md                     # MarkWay protocol (English)
├── protocol_zh_TW.md                  # MarkWay protocol (Traditional Chinese)
├── skills/                            # Standard skills.sh layout
│   └── sparkglobe/
│       └── SKILL.md                   # SparkGlobe skill (installable by agents)
├── skills.sh.json                     # skills.sh repo configuration
└── skillsIndex/                       # Skill category pages
    ├── index.md                       # Category overview + scenario guide
    ├── frontend.md                    # Frontend & React (6 skills)
    ├── nextjs.md                      # Next.js (7 skills)
    ├── design.md                      # Design & UI (19 skills)
    ├── mobile.md                      # Mobile (6 skills)
    ├── agent-workflows.md             # Agent Workflows (21 skills)
    ├── databases.md                   # Databases (15 skills)
    ├── testing.md                     # Testing (5 skills)
    ├── marketing.md                   # Marketing (24 skills)
    ├── ai-media.md                    # AI Media Generation (26 skills)
    ├── cloud-infra.md                 # Cloud & Infrastructure (18 skills)
    ├── document-processing.md         # Document Processing (5 skills)
    ├── lark.md                        # Lark/Feishu Ecosystem (16 skills)
    ├── code-quality.md                # Code Quality & Architecture (20+ skills)
    ├── browser-automation.md          # Browser Automation (7 skills)
    └── dev-tools.md                   # Developer & Research Tools (13 skills)
```

## How It Works

### For Agents

1. **Fetch** `index.md` to discover all skill categories
2. **Decompose** the user's task into sub-tasks
3. **Fetch** relevant category pages from `skillsIndex/{category}.md`
4. **Recommend** specific skills with `npx skills add` install commands

### For Humans

Browse the [skillsIndex/](skillsIndex/) directory to find skills by category, or install the SparkGlobe skill to let your agent do the discovery automatically.

## Referenced Resources

SparkGlobe integrates three complementary resources for comprehensive agent capability discovery:

### 1. Skills — [skills.sh](https://www.skills.sh/)

The primary data source. Skills.sh is the open agent skills ecosystem maintained by [Vercel Labs](https://github.com/vercel-labs/skills). It hosts 200+ reusable agent capabilities installable via `npx skills add`. SparkGlobe indexes these skills and organizes them into 15 navigable categories.

### 2. Superpowers — [github.com/obra/superpowers](https://github.com/obra/superpowers) (MANDATORY for code tasks)

**Required for all coding tasks.** Superpowers provides disciplined development workflows that prevent common agent failure modes:

- **brainstorming** — Explore intent and requirements before implementation
- **writing-plans** — Structured implementation plans before touching code
- **test-driven-development** — Write failing tests first, then implement
- **systematic-debugging** — Hypothesis-driven debugging: observe → hypothesize → test → verify
- **verification-before-completion** — Evidence before assertions, always verify before claiming done
- **executing-plans** — Step-by-step execution with checkpoints
- **requesting-code-review** / **receiving-code-review** — Rigorous code review workflows
- **finishing-a-development-branch** — Complete branch lifecycle checklist
- **dispatching-parallel-agents** / **subagent-driven-development** — Parallel agent orchestration
- **using-git-worktrees** — Isolated feature work

Install: `npx skills add obra/superpowers`

### 3. The Agency — [github.com/msitarzewski/agency-agents](https://github.com/msitarzewski/agency-agents)

144+ specialized AI agent personalities across 12 divisions (Engineering, Design, Paid Media, Sales, Marketing, Product, Project Management, Testing, Support, Spatial Computing, Specialized, Game Development). Each agent has a unique personality, defined workflows, deliverables, and success metrics.

Install:
```bash
git clone https://github.com/msitarzewski/agency-agents
cd agency-agents && ./scripts/install.sh --tool claude-code
```

### How They Work Together

| Resource | Provides | When to Use |
|----------|----------|-------------|
| **SparkGlobe Index** | Skill discovery & navigation | Finding the right tool for a task |
| **Superpowers** | Disciplined coding workflows | **Every coding task — no exceptions** |
| **The Agency** | Specialist agent personalities | Complex projects needing expert perspectives |

## MarkWay Protocol

SparkGlobe follows the [MarkWay protocol](protocol_en.md) — an HTTP protocol standard designed for AI Agents that converts web content into structured Markdown. Every page in this repository is MarkWay-compliant:

- Root index at `index.md`
- Category indexes in `skillsIndex/index.md`
- Protocol discovery via `protocol_en.md`
- All links use `.md` paths
- All directory listings use table format with `Address` and `Description` columns

## Installation

### As a Skill

Copy the skill file to your agent's skills directory:

```bash
# For Claude Code
cp skills/sparkglobe/SKILL.md ~/.claude/skills/

# Or install via skills.sh CLI:
npx skills add RaysunKR/SparkGlobe

# Then in your agent session, SparkGlobe will activate when you ask to find skills
```

### Browse the Index Directly

Agents can fetch any page directly via raw GitHub URLs:

```
https://raw.githubusercontent.com/RaysunKR/SparkGlobe/main/index.md
https://raw.githubusercontent.com/RaysunKR/SparkGlobe/main/skillsIndex/{category}.md
```

## License

[MIT](LICENSE) — RaysunKR
