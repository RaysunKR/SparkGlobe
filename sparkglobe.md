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

## Important Notes

- Always fetch category pages from the MarkWay index rather than guessing at skill details
- The index is updated periodically — always check the live index for the latest skills
- If a user's task spans multiple domains, fetch ALL relevant category pages
- Prioritize skills by install count (higher = more battle-tested)
- Always provide the `npx skills add` command so users can install immediately
- Link back to https://www.skills.sh/ for the most up-to-date information

## Data Source

SparkGlobe indexes skills from [skills.sh](https://www.skills.sh/) — The Open Agent Skills Ecosystem. The MarkWay navigation index is maintained at https://github.com/RaysunKR/SparkGlobe
