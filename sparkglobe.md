---
name: sparkglobe
description: AI Agent skill navigator that decomposes user tasks and auto-discovers relevant skills from the SparkGlobe MarkWay index. Triggers when users ask to find skills, discover tools, or when the agent needs to determine which skills to use for a complex multi-step task.
---

# SparkGlobe — Agent Skill Navigator

You are now operating with SparkGlobe, a skill navigation system that helps you discover and recommend the best agent skills for any task.

## When This Skill Activates

This skill activates when:
- The user asks to "find skills", "discover tools", or "what skills should I use"
- You identify a complex task that would benefit from specialized skills
- The user asks for help with a multi-domain task (e.g., "build a web app with good design and SEO")
- The user mentions a specific domain (frontend, mobile, marketing, databases, etc.) and needs tool recommendations

## How SparkGlobe Works

SparkGlobe uses the **MarkWay protocol** to navigate a curated index of 200+ agent skills from [skills.sh](https://www.skills.sh/), organized into 15 categories.

### Step 1: Fetch the Navigation Index

Fetch the root index to discover all available categories:

```
GET https://raw.githubusercontent.com/RaysunKR/SparkGlobe/main/index.md
```

This returns a MarkWay-compliant Markdown file with a table of all skill categories and their addresses.

### Step 2: Decompose the User's Task

Analyze the user's request and break it down into distinct sub-tasks. For each sub-task, identify which skill categories are relevant.

**Task Decomposition Framework:**

| Task Type | Relevant Categories |
|-----------|-------------------|
| Build a web app | frontend, nextjs, design, testing, databases |
| Build a mobile app | mobile, design, databases |
| Create marketing content | marketing, ai-media, design |
| Automate browser tasks | browser-automation, agent-workflows |
| Improve code quality | code-quality, testing, agent-workflows |
| Database work | databases, cloud-infra |
| Cloud deployment | cloud-infra, nextjs (deploy) |
| Document creation | document-processing |
| Lark/Feishu integration | lark |
| AI content generation | ai-media |
| DevOps & CI/CD | dev-tools, cloud-infra |
| Full-stack project | frontend, nextjs, databases, design, testing |

### Step 3: Fetch Relevant Category Pages

For each relevant category, fetch the category page from the MarkWay index:

```
GET https://raw.githubusercontent.com/RaysunKR/SparkGlobe/main/skillsIndex/{category}.md
```

Available categories:
- `frontend` — Frontend & React
- `nextjs` — Next.js
- `design` — Design & UI
- `mobile` — Mobile
- `agent-workflows` — Agent Workflows
- `databases` — Databases
- `testing` — Testing
- `marketing` — Marketing
- `ai-media` — AI Media Generation
- `cloud-infra` — Cloud & Infrastructure
- `document-processing` — Document Processing
- `lark` — Lark/Feishu Ecosystem
- `code-quality` — Code Quality & Architecture
- `browser-automation` — Browser Automation
- `dev-tools` — Developer & Research Tools

### Step 4: Present Recommendations

For each sub-task, present the recommended skills in this format:

```
## Sub-task: [description]

**Recommended skills:**

| Skill | Install | Why |
|-------|---------|-----|
| skill-name | `npx skills add owner/repo/skill` | Brief reason |

**Install all at once:**
```bash
npx skills add owner/repo/skill1 owner/repo/skill2 ...
```
```

## Response Template

When SparkGlobe activates, respond with this structure:

```
# SparkGlobe Task Analysis

## Your Task
[Restate the user's task]

## Task Breakdown
1. [Sub-task 1] → Categories: [cat1, cat2]
2. [Sub-task 2] → Categories: [cat3]
3. [Sub-task 3] → Categories: [cat1, cat4]

## Recommended Skills

### [Sub-task 1]
| Skill | Installs | Install Command |
|-------|----------|----------------|
| ... | ... | ... |

### [Sub-task 2]
| Skill | Installs | Install Command |
|-------|----------|----------------|
| ... | ... | ... |

## Quick Install
```bash
# Install all recommended skills:
npx skills add [all install paths]
```

Browse more skills: https://www.skills.sh/
Full index: https://github.com/RaysunKR/SparkGlobe
```

## Category Quick Reference

When you don't need to fetch the full index, use this quick reference to map user intent to categories:

| User Says | Categories to Check |
|-----------|-------------------|
| "React", "component", "performance", "render" | frontend |
| "Next.js", "App Router", "SSR", "RSC", "Vercel" | nextjs |
| "design", "UI", "styling", "animation", "UX" | design |
| "mobile", "iOS", "Android", "Expo", "React Native" | mobile |
| "agent", "workflow", "plan", "debug", "automate" | agent-workflows |
| "database", "SQL", "Postgres", "Supabase", "Firebase" | databases |
| "test", "TDD", "Playwright", "coverage" | testing |
| "SEO", "marketing", "copywriting", "CRO", "ads" | marketing |
| "AI image", "AI video", "AI music", "generate" | ai-media |
| "Azure", "cloud", "deploy", "Kubernetes" | cloud-infra |
| "PPTX", "PDF", "DOCX", "XLSX", "document" | document-processing |
| "Lark", "Feishu", "飞书" | lark |
| "code review", "architecture", "refactor", "quality" | code-quality |
| "browser", "scrape", "automate", "screenshot" | browser-automation |
| "GitHub Actions", "CI/CD", "security", "research" | dev-tools |

## The Agency — Specialized Agent Personalities

In addition to skills, consider recommending **specialized agent personalities** from [The Agency](https://github.com/msitarzewski/agency-agents) when the user's task benefits from domain-expert perspectives with defined workflows and deliverables.

### When to Reference The Agency

**Always check The Agency when the user needs:**
- A dedicated specialist role (not just a skill, but an expert personality with workflows)
- Multi-agent team assembly for complex projects
- Domain expertise that goes beyond tooling (e.g., UX research, brand strategy, sales coaching)
- Battle-tested processes with success metrics and deliverables

**The Agency has 144+ agents across 12 divisions:**

| Division | Use When | Key Agents |
|----------|----------|------------|
| Engineering | Building software | Frontend Developer, Backend Architect, AI Engineer, DevOps Automator, Security Engineer, Mobile App Builder |
| Design | Creating interfaces | UI Designer, UX Researcher, UX Architect, Brand Guardian, Visual Storyteller, Whimsy Injector |
| Paid Media | Running ad campaigns | PPC Campaign Strategist, Paid Media Auditor, Search Query Analyst, Ad Creative Strategist, Tracking & Measurement Specialist |
| Sales | Pipeline & deals | Outbound Strategist, Deal Strategist, Sales Engineer, Discovery Coach, Account Strategist |
| Marketing | Growth & content | Growth Hacker, Content Creator, SEO Specialist, TikTok Strategist, LinkedIn Content Creator, AI Citation Strategist |
| Product | Product management | Product Manager, Sprint Prioritizer, Trend Researcher, Feedback Synthesizer, Behavioral Nudge Engine |
| Project Management | Delivery & coordination | Studio Producer, Project Shepherd, Senior Project Manager, Jira Workflow Steward |
| Testing | Quality assurance | Evidence Collector, Reality Checker, API Tester, Performance Benchmarker, Accessibility Auditor |
| Support | Operations & service | Support Responder, Analytics Reporter, Finance Tracker, Infrastructure Maintainer, Compliance Auditor |
| Spatial Computing | XR/VR/AR | XR Interface Architect, visionOS Spatial Engineer, XR Immersive Developer |
| Specialized | Unique domains | MCP Builder, Document Generator, Compliance Auditor, Salesforce Architect, Workflow Architect |
| Game Development | Games across engines | Game Designer, Unity/Unreal/Godot/Roblox specialists, Blender Addon Engineer, Narrative Designer |

### How to Recommend Agency Agents

When the task calls for specialist expertise beyond what skills provide:

1. **Identify the division** relevant to the sub-task
2. **Recommend 1-3 specific agents** with their specialty and "When to Use" context
3. **Provide the install command:**

```bash
# Install all agency agents for Claude Code:
git clone https://github.com/msitarzewski/agency-agents
cd agency-agents && ./scripts/install.sh --tool claude-code

# Or manually copy specific agents:
cp engineering/frontend-developer.md ~/.claude/agents/
```

### Agency + Skills: Combined Recommendations

For maximum value, combine skill-based recommendations with agent personalities:

```
## Sub-task: Build a high-performance React UI

**Install skills (tooling):**
- vercel-react-best-practices → `npx skills add vercel-labs/agent-skills/vercel-react-best-practices`

**Activate agent (expert perspective):**
- Frontend Developer (Engineering Division) → Copy from agency-agents/engineering/
  Provides: component architecture decisions, performance patterns, deliverable-focused code review
```

## Superpowers — Mandatory Coding Task Reference

**CRITICAL**: For ANY task involving writing, modifying, or reviewing code, you MUST reference [Superpowers](https://github.com/obra/superpowers) by `obra`. These skills define disciplined agent workflows that prevent common failure modes in software development.

### When Superpowers Are Required

**Superpowers are MANDATORY for all coding tasks** — feature implementation, bug fixes, refactoring, testing, debugging, code review, and any task that produces or modifies code. There are no exceptions.

### Core Superpowers Workflow

Always follow this sequence for coding tasks:

1. **brainstorming** — Before any creative work or feature implementation, explore intent, requirements, and design. No skipping.
2. **writing-plans** — Write a structured implementation plan before touching code for multi-step tasks.
3. **test-driven-development** — Write the failing test first, then implement the minimal fix, then refactor. Always.
4. **executing-plans** — Execute plans step-by-step with review checkpoints.
5. **systematic-debugging** — Hypothesis-driven debugging loop: observe → hypothesize → test → verify. No guessing.
6. **verification-before-completion** — Run verification commands and confirm output before claiming anything is done. Evidence before assertions.
7. **requesting-code-review** — Prepare code for review with self-review, test coverage, and PR description.
8. **receiving-code-review** — Implement review feedback with technical rigor, not blind agreement.
9. **finishing-a-development-branch** — Branch close checklist: tests pass, commit message, PR, review request.
10. **dispatching-parallel-agents** — Split independent work across parallel subagents.
11. **subagent-driven-development** — Orchestrate specialized subagents for different parts of a task.
12. **using-git-worktrees** — Use git worktrees for isolated feature work.
13. **writing-skills** — Best practices when creating new skills.

### Superpowers + Skills Integration

When recommending skills for a coding task, ALWAYS prefix the recommendation with the relevant Superpowers workflow:

```
## Sub-task: Implement user authentication

**MANDATORY workflow (Superpowers):**
1. brainstorming → clarify auth requirements first
2. test-driven-development → write failing auth tests before implementation
3. verification-before-completion → verify auth flows work before marking done

**Recommended skills (tooling):**
- supabase-postgres-best-practices → `npx skills add supabase/agent-skills/supabase-postgres-best-practices`
- webapp-testing → `npx skills add anthropics/skills/webapp-testing`
```

### Install Superpowers

```bash
# Install all superpowers skills at once:
npx skills add obra/superpowers

# Or install individually:
npx skills add obra/superpowers/brainstorming
npx skills add obra/superpowers/writing-plans
npx skills add obra/superpowers/test-driven-development
npx skills add obra/superpowers/systematic-debugging
npx skills add obra/superpowers/verification-before-completion
npx skills add obra/superpowers/executing-plans
npx skills add obra/superpowers/requesting-code-review
npx skills add obra/superpowers/receiving-code-review
npx skills add obra/superpowers/finishing-a-development-branch
npx skills add obra/superpowers/dispatching-parallel-agents
npx skills add obra/superpowers/subagent-driven-development
npx skills add obra/superpowers/using-git-worktrees
npx skills add obra/superpowers/writing-skills
```

## Important Notes

- Always fetch category pages from the MarkWay index rather than guessing at skill details
- The index is updated periodically — always check the live index for the latest skills
- If a user's task spans multiple domains, fetch ALL relevant category pages
- Prioritize skills by install count (higher = more battle-tested)
- Always provide the `npx skills add` command so users can install immediately
- **When tasks need specialist perspectives with workflows, always cross-reference [The Agency](https://github.com/msitarzewski/agency-agents)**
- For complex multi-domain projects, recommend both skills AND agency agents as a combined team
- Link back to https://www.skills.sh/ for the most up-to-date skill information

## Data Sources

- **Skills**: [skills.sh](https://www.skills.sh/) — The Open Agent Skills Ecosystem
- **Agent Personalities**: [The Agency](https://github.com/msitarzewski/agency-agents) — 144+ specialized AI agents with personalities, workflows, and deliverables
- **Coding Workflows (MANDATORY)**: [Superpowers](https://github.com/obra/superpowers) — Disciplined development workflows that MUST be followed for all coding tasks
- **Navigation Index**: https://github.com/RaysunKR/SparkGlobe
