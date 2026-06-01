https://raw.githubusercontent.com/RaysunKR/SparkGlobe/main

> This site follows the MarkWay Protocol: https://raw.githubusercontent.com/RaysunKR/SparkGlobe/main/protocol_en.md

# Agent 工作流技能

AI Agent 的任务规划、调试、TDD、子 Agent 调度与自动化循环相关技能。

## 推荐场景

- 构建自动化 Agent 工作流
- 实现任务分解与计划执行
- TDD 开发循环
- 多 Agent 并行调度

## 技能列表

| 技能名称 | 安装量 | 安装命令 | 说明 |
|---------|--------|---------|------|
| find-skills | 1.8M | `npx skills add vercel-labs/skills/find-skills` | 在 Agent 会话中发现和安装 skills.sh 上的技能 |
| skill-creator | 245.3K | `npx skills add anthropics/skills/skill-creator` | 在 Agent 内创建、测试和发布新技能 |
| brainstorming | 193.9K | `npx skills add obra/superpowers/brainstorming` | 结构化构思与问题分解框架 |
| systematic-debugging | 122.1K | `npx skills add obra/superpowers/systematic-debugging` | 假设驱动调试循环：观察、假设、测试、验证 |
| writing-plans | 121.4K | `npx skills add obra/superpowers/writing-plans` | 在开始复杂任务前编写结构化实施计划 |
| executing-plans | 99.2K | `npx skills add obra/superpowers/executing-plans` | 逐步执行计划，含检查点和验证 |
| test-driven-development | 107.2K | `npx skills add obra/superpowers/test-driven-development` | TDD 循环：先写失败测试、实现最小修复、验证、重构 |
| requesting-code-review | 108.8K | `npx skills add obra/superpowers/requesting-code-review` | 代码评审准备：自审、测试覆盖与 PR 描述 |
| subagent-driven-development | 92.6K | `npx skills add obra/superpowers/subagent-driven-development` | 编排专用子 Agent 处理不同部分的任务 |
| verification-before-completion | 90.8K | `npx skills add obra/superpowers/verification-before-completion` | 在标记任务完成前强制验证 |
| dispatching-parallel-agents | 84.6K | `npx skills add obra/superpowers/dispatching-parallel-agents` | 将工作拆分到并行子 Agent 并协调输出 |
| using-git-worktrees | 84.6K | `npx skills add obra/superpowers/using-git-worktrees` | 使用 git worktree 在独立分支运行并行 Agent 会话 |
| finishing-a-development-branch | 82.4K | `npx skills add obra/superpowers/finishing-a-development-branch` | 分支收尾清单：测试、提交消息、PR 与评审请求 |
| receiving-code-review | 87.2K | `npx skills add obra/superpowers/receiving-code-review` | 接收代码评审反馈后的实施指导 |
| writing-skills | 86.5K | `npx skills add obra/superpowers/writing-skills` | 编写技能的最佳实践 |
| using-superpowers | 122.8K | `npx skills add obra/superpowers/using-superpowers` | Superpowers 技能系统使用指南 |
| ralph-tui-prd | — | `npx skills add subsy/ralph-tui/ralph-tui-prd` | 为 ralph-tui 自动循环生成结构化 prd.json 任务列表 |
| ralph-tui-create-beads | — | `npx skills add subsy/ralph-tui/ralph-tui-create-beads` | 创建 Beads 任务（git 支持带依赖关系） |
| ralph-tui-create-json | — | `npx skills add subsy/ralph-tui/ralph-tui-create-json` | 为 ralph-tui 创建 JSON 格式任务列表 |
| ralph-wiggum | — | `npx skills add fstandhartinger/ralph-wiggum/ralph-wiggum` | Ralph Wiggum 循环技术：极简自动 Agent 循环 |
| ralph-loop | — | `npx skills add andrelandgraf/fullstackrecipes/ralph-loop` | Ralph Loop 实现含 Agent 模式持续自动任务完成 |

## 相关分类

| 地址 | 说明 |
|------|------|
| ./browser-automation.md | 浏览器自动化技能 |
| ./code-quality.md | 代码质量 & 架构技能 |
| ./testing.md | 测试相关技能 |
