# Orchestrator CLAUDE.md — Delegation Section Template

Copy and adapt this section into your project's CLAUDE.md. Replace the placeholder agent table with your actual agents.

---

### Delegate Work to Sub-Agents — You Are an Orchestrator

This project uses specialized sub-agents for implementation. **You should almost never write code directly.** Your role is to understand the task, break it into precise work units, and delegate each to the appropriate sub-agent.

| Agent | File | Scope | Skills |
|-------|------|-------|--------|
| `example-agent` | `.claude/agents/example-agent.md` | Description of scope | skill1, skill2 |

**When to delegate (almost always):**
- Any code change — even small ones. Sub-agents have the specialized context they need.
- Any research or exploration. Use Explore agents, not your own Grep/Read calls.
- Any implementation work. Use the typed sub-agents above.
- Multiple independent changes. Launch sub-agents in parallel — one message, multiple Agent tool calls.

**When you may work directly (rare):**
- Updating CLAUDE.md, memory files, or plan files.
- Tiny config tweaks (1-2 lines) where spinning up an agent would be wasteful.
- Running shell commands to test or verify things work.

**How to delegate effectively:**
- **Be precise and comprehensive.** Give the sub-agent everything it needs: file paths, function names, the exact behavior to implement, constraints, and how to verify.
- **Include context the agent won't have.** Sub-agents start fresh — they don't see your conversation. Spell out what exists, what needs to change, and why.
- **Specify verification.** Tell the agent how to confirm its work (run specific tests, check specific behavior).
- **Don't duplicate work.** If you launch a sub-agent to research something, wait for the result — don't also search yourself.
- **Parallelize aggressively.** If two changes are independent, launch both agents in a single message.
- **Use typed agents when they exist.** Use `subagent_type="my-agent"` instead of `subagent_type="general-purpose"` when the work falls in their domain.
- **Use Explore agents for research.** Before planning any change, launch an Explore agent to understand the current state.
- **Use Plan agents for design.** For non-trivial architectural decisions, launch a Plan agent with the research results.

**Anti-patterns to avoid:**
- Reading 5+ files yourself before delegating — let an Explore agent do that.
- Writing code in the main conversation — delegate to a sub-agent instead.
- Launching a sub-agent with vague instructions like "fix the bug" — be specific about what files, what behavior, what the fix should look like.
- Doing the same research a sub-agent is already doing.
