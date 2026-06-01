https://raw.githubusercontent.com/RaysunKR/SparkGlobe/main

> This site follows the MarkWay Protocol: https://raw.githubusercontent.com/RaysunKR/SparkGlobe/main/protocol_en.md

# Skills Category Overview

Complete skills.sh index organized by domain. Each category links to a detailed skill listing with install commands.

| Category | Skills | Address | Description |
|----------|--------|---------|-------------|
| Frontend & React | 6 | ./frontend.md | React performance rules, component patterns, Tailwind design systems, shadcn/ui |
| Next.js | 7 | ./nextjs.md | App Router, Server Components, caching APIs, Vercel deployment patterns |
| Design & UI | 16 | ./design.md | Frontend design patterns, visual polish, design system extraction, interaction & animation |
| Mobile | 6 | ./mobile.md | React Native, Expo native UI, data fetching, NativeWind |
| Agent Workflows | 20 | ./agent-workflows.md | Plan writing, debugging loops, TDD, sub-agent dispatch, autonomous loops |
| Databases | 15 | ./databases.md | Postgres, Supabase, Firebase, Convex, Neon, Drizzle ORM |
| Testing | 5 | ./testing.md | TDD loops, Playwright automation, web testing, verification passes |
| Marketing | 24 | ./marketing.md | SEO, copywriting, CRO, growth strategy, email sequences, paid ads |
| AI Media Generation | 26 | ./ai-media.md | AI image/video/music generation, face swap, inpainting, video extension |
| Cloud & Infrastructure | 18 | ./cloud-infra.md | Azure full-stack services, Firebase, Kubernetes, cloud migration & cost optimization |
| Document Processing | 5 | ./document-processing.md | PPTX/PDF/DOCX/XLSX file creation and parsing, canvas design |
| Lark/Feishu | 16 | ./lark.md | Full Lark platform API: docs, spreadsheets, messaging, approvals, OKR, calendar |
| Code Quality & Architecture | 20+ | ./code-quality.md | Code review, architecture improvement, TDD, diagnostics, PRD generation, Caveman toolchain |
| Browser Automation | 7 | ./browser-automation.md | Web automation, form filling, screenshots, data extraction |
| Developer & Research Tools | 13 | ./dev-tools.md | GitHub Actions, Linux cloud security, userscripts, AI paper reproduction |

## Find Skills by Scenario

| User Scenario | Recommended Categories |
|---------------|----------------------|
| Build a web app | frontend.md → nextjs.md → design.md → testing.md |
| Mobile app development | mobile.md → design.md → databases.md |
| Agent automation | agent-workflows.md → browser-automation.md → dev-tools.md |
| Marketing & growth | marketing.md → design.md → ai-media.md |
| AI content creation | ai-media.md → document-processing.md |
| Backend & databases | databases.md → cloud-infra.md → code-quality.md |
| Enterprise collaboration | lark.md → document-processing.md → code-quality.md |
| Improve code quality | code-quality.md → testing.md → agent-workflows.md |

## Install Skills

All skills are installed via skills.sh:

```bash
npx skills add <owner/repo/skill-name>
```

Examples:
```bash
npx skills add anthropics/skills/frontend-design
npx skills add obra/superpowers/brainstorming
npx skills add mattpocock/skills/grill-me
```

Visit [skills.sh](https://www.skills.sh/) for the full skill directory.
