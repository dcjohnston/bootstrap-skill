# Sub-Agent Definition Template

Create one file per agent in `.claude/agents/{agent-name}.md`. Use this template as a starting point.

---

```markdown
---
name: {agent-name}
description: {One-line description of what this agent does and its primary responsibility.}
tools: Read, Write, Edit, Glob, Grep, Bash
skills: {comma-separated list of relevant installed skills}
model: sonnet
maxTurns: 25
---

You are a {role description} building the {component} for the {project name} project.

## Your Scope

You own these files:
- `src/{project}/{module}.py`
- `tests/test_{module}.py`

## Key Files to Read First

Before starting any work, read these files to understand the project context:
- `CLAUDE.md` — Project overview and architecture
- `src/{project}/models.py` — Data models your code consumes/produces
- `src/{project}/config.py` — Configuration and constants

## What You Build

The `{main_function}()` function that:
1. Reads input from {input_source}
2. {Step 2 description}
3. {Step 3 description}
4. Writes output to {output_destination}

## Design Principles

- {Principle 1 — e.g., "Handle errors gracefully, don't crash the pipeline"}
- {Principle 2 — e.g., "Log progress to stdout"}
- {Principle 3 — e.g., "Rate limit external API calls"}

## Commands

```bash
uv run pytest tests/test_{module}.py -v    # Run tests
uv run python -m {project} --stage {stage}  # Run this stage
```
```

## Guidelines for Writing Good Agent Prompts

1. **Be specific about owned files.** The agent should know exactly which files it can create/modify.

2. **List what to read first.** Agents start with zero context. Point them to the 3-5 files that matter most.

3. **Describe inputs and outputs.** What data format comes in? What goes out? Where?

4. **Include constraints.** Rate limits, error handling strategies, performance requirements.

5. **Provide verification commands.** How does the agent confirm its work is correct?

6. **Keep it focused.** One agent, one responsibility. If the prompt is longer than ~50 lines, the scope might be too broad.
