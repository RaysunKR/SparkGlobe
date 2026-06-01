https://raw.githubusercontent.com/RaysunKR/SparkGlobe/master

> This site follows the MarkWay Protocol: https://raw.githubusercontent.com/RaysunKR/SparkGlobe/master/protocol_en.md

# Agent Workflow Skills

AI Agent task planning, debugging, TDD, sub-agent dispatch, and autonomous loops.

## Best For

- Building automated agent workflows
- Implementing task decomposition and plan execution
- TDD development loops
- Multi-agent parallel dispatch

## Skills

| Skill | Installs | Install Command | Description |
|-------|----------|----------------|-------------|
| find-skills | 1.8M | `npx skills add vercel-labs/skills/find-skills` | Discover and install skills from skills.sh inside an agent session |
| skill-creator | 245.3K | `npx skills add anthropics/skills/skill-creator` | Create, test, and publish new skills from within your agent |
| brainstorming | 193.9K | `npx skills add obra/superpowers/brainstorming` | Structured ideation and problem decomposition frameworks |
| systematic-debugging | 122.1K | `npx skills add obra/superpowers/systematic-debugging` | Hypothesis-driven debugging loop: observe, hypothesize, test, verify |
| writing-plans | 121.4K | `npx skills add obra/superpowers/writing-plans` | Write structured implementation plans before starting complex tasks |
| executing-plans | 99.2K | `npx skills add obra/superpowers/executing-plans` | Execute a plan step-by-step with checkpoints and verification |
| test-driven-development | 107.2K | `npx skills add obra/superpowers/test-driven-development` | TDD loop: write the failing test first, implement the minimal fix, verify, then refactor |
| requesting-code-review | 108.8K | `npx skills add obra/superpowers/requesting-code-review` | Prepare code for review: self-review, test coverage, and pull request description |
| subagent-driven-development | 92.6K | `npx skills add obra/superpowers/subagent-driven-development` | Orchestrate specialized subagents for different parts of a task |
| verification-before-completion | 90.8K | `npx skills add obra/superpowers/verification-before-completion` | Force a verification pass before any task is marked complete |
| dispatching-parallel-agents | 84.6K | `npx skills add obra/superpowers/dispatching-parallel-agents` | Split work across parallel subagents and coordinate their outputs |
| using-git-worktrees | 84.6K | `npx skills add obra/superpowers/using-git-worktrees` | Use git worktrees to run parallel agent sessions on separate branches |
| finishing-a-development-branch | 82.4K | `npx skills add obra/superpowers/finishing-a-development-branch` | Branch close checklist: tests, commit message, pull request, and review request |
| receiving-code-review | 87.2K | `npx skills add obra/superpowers/receiving-code-review` | Guidance for implementing code review feedback |
| writing-skills | 86.5K | `npx skills add obra/superpowers/writing-skills` | Best practices for writing skills |
| using-superpowers | 122.8K | `npx skills add obra/superpowers/using-superpowers` | Superpowers skill system usage guide |
| ralph-tui-prd | — | `npx skills add subsy/ralph-tui/ralph-tui-prd` | Generate structured prd.json task lists for ralph-tui's autonomous loop |
| ralph-tui-create-beads | — | `npx skills add subsy/ralph-tui/ralph-tui-create-beads` | Create Beads tasks (git-backed, with dependencies) for ralph-tui |
| ralph-tui-create-json | — | `npx skills add subsy/ralph-tui/ralph-tui-create-json` | Create JSON-format task lists for ralph-tui |
| ralph-wiggum | — | `npx skills add fstandhartinger/ralph-wiggum/ralph-wiggum` | The Ralph Wiggum loop technique: simplified autonomous agent loop with minimal setup |
| ralph-loop | — | `npx skills add andrelandgraf/fullstackrecipes/ralph-loop` | Ralph loop implementation with agent mode for sustained autonomous task completion |

## Related

| Address | Description |
|---------|-------------|
| ./browser-automation.md | Browser automation skills |
| ./code-quality.md | Code quality & architecture skills |
| ./testing.md | Testing skills |
