# Bootstrap Skill

A Claude Code skill that scaffolds new projects for agent-driven development.

It walks through: brainstorming the idea, splitting work into sub-agents, setting up the project (package manager, linting, type checking), writing agent definitions, installing relevant skills, and creating a CLAUDE.md with orchestration guidance.

## Install

```bash
npx skills add dcjohnston/bootstrap-skill
```

## What it does

1. **Brainstorm** — scope the project and nail key decisions
2. **Work breakdown** — identify 3-6 independent sub-agents
3. **Scaffold** — project structure, deps, linting (ruff/mypy, eslint/tsc), entry points
4. **Sub-agents** — `.claude/agents/*.md` with scoped system prompts
5. **Skills** — find and install relevant skills via `npx skills`
6. **CLAUDE.md** — orchestrator instructions with delegation patterns
7. **Verify** — everything builds, lints, and type-checks clean
