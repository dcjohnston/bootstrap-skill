# Project Structure Patterns

## Common Structure (All Languages)

Every bootstrapped project should have:

```
project/
├── CLAUDE.md                    # Orchestrator instructions (required)
├── .claude/
│   └── agents/                  # Sub-agent definitions (required)
│       ├── agent-a.md
│       ├── agent-b.md
│       └── agent-c.md
├── data/                        # Seed data, fixtures, configs
├── tests/                       # Test files mirroring src structure
└── src/                         # Source code
```

## Python Projects

```
project/
├── CLAUDE.md
├── pyproject.toml               # All config (deps, tools, build)
├── uv.lock
├── .claude/agents/
├── src/
│   └── {package}/
│       ├── __init__.py
│       ├── __main__.py          # CLI entry point
│       ├── config.py            # Settings, env vars, constants
│       ├── models.py            # Pydantic data models
│       └── {modules...}
├── templates/                   # Jinja2 or other templates (if needed)
├── static/                      # Static assets (if needed)
├── data/                        # Input data, fixtures
├── tests/
│   ├── conftest.py
│   └── test_{modules...}
└── output/                      # Generated output (if needed)
```

Setup: `uv init --package {name}`, then `uv add` dependencies.

## TypeScript / Node Projects

```
project/
├── CLAUDE.md
├── package.json
├── tsconfig.json
├── .claude/agents/
├── src/
│   ├── index.ts                 # Entry point
│   ├── config.ts
│   ├── types.ts                 # Shared type definitions
│   └── {modules...}
├── tests/
│   └── {modules...}.test.ts
└── data/
```

Setup: `npm init`, then `npm install` dependencies.

## Full-Stack Projects

```
project/
├── CLAUDE.md
├── .claude/agents/
│   ├── frontend-agent.md
│   ├── api-agent.md
│   └── db-agent.md
├── frontend/                    # Separate package
│   ├── package.json
│   ├── src/
│   └── tests/
├── backend/                     # Separate package
│   ├── pyproject.toml (or package.json)
│   ├── src/
│   └── tests/
└── data/
```

## Key Principles

1. **`src/` layout always.** Prevents import confusion, works with all build tools.
2. **Tests mirror source.** `src/foo/bar.py` → `tests/test_bar.py` (or `tests/foo/test_bar.py`).
3. **Data is separate from code.** Input data, fixtures, and generated output get their own top-level directories.
4. **Config is centralized.** One config file/module that reads env vars and defines constants.
5. **Models are shared.** A single `models` file/module that all agents reference for data contracts.
