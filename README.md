# Agent Lightweight Maintenance

A lightweight maintenance skill for AI coding agents that get stuck in loops, over-read repositories, or carry stale project context.

Use it when a small edit turns into a long session, the agent keeps revisiting retired features, or a handoff needs to stay short enough for the next agent to act immediately.

## Before / After

Before:

- The agent repeatedly scans the repository.
- Generated output, screenshots, logs, or dependency folders get inspected again.
- Retired features and old attempts keep returning as active context.
- `progress.md`, `STATUS.md`, or the handoff file becomes a worklog.

After:

- The agent reads only project rules, source map, and current status if present.
- It identifies the files that actually own the current issue.
- It produces a Loop Break Summary.
- It takes one smallest next action.
- It runs one narrow verification command.

## Use When

- Your agent keeps repeating the same plan.
- Small edits take too long.
- Current status files become long worklogs.
- A source map or project map is stale.
- Generated output is being inspected instead of source files.
- You need a lightweight handoff for a new conversation or collaborator.
- You want to slim an old project without deleting useful work.

## Sample Prompt

```text
Use $agent-lightweight-maintenance.

We are in a loop. Stop editing and produce a Loop Break Summary.

Read only project rules, a source map, and a current status or handoff file if present.
Identify the files that actually own the current issue.
Give me one smallest next action and one narrow verification command.
Do not inspect generated output or large asset folders unless directly required.
```

## Install Locally

Copy the skill folder into your Codex skills directory:

```bash
cp -R skills/agent-lightweight-maintenance ~/.codex/skills/
```

Then start a new Codex session and invoke it with:

```text
Use $agent-lightweight-maintenance.
```

## Repository Layout

```text
skills/
  agent-lightweight-maintenance/
    SKILL.md
    agents/
      openai.yaml
```

## Suggested GitHub Topics

`codex`, `codex-skill`, `ai-coding-agent`, `agent-workflow`, `developer-tools`, `context-management`, `handoff`, `debugging-workflow`
