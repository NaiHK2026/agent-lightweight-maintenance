# Agent Lightweight Maintenance

A small Codex skill and AI coding agent workflow for breaking repeated agent loops, reducing context bloat, and preparing lightweight project handoffs.

It is designed for moments when an AI coding agent keeps re-reading the same files, repeats broad plans, carries stale assumptions, or turns a small code edit into a long debugging session.

Use it when you need to stop the loop, identify the files that actually own the issue, and move forward with one small action plus one narrow verification command.

## Common Pain Points

- "My AI coding agent keeps looping on the same fix."
- "A tiny text or UI change became a huge repository scan."
- "The agent keeps inspecting generated output instead of source files."
- "Old notes, stale assumptions, or retired features keep coming back."
- "I need a short handoff before starting a new conversation."
- "I want to slim an old project without deleting useful work."

## What It Helps With

- Stop repeated broad exploration.
- Identify the files that actually own the current issue.
- Separate current work from stale history.
- Produce short handoffs for new conversations or collaborators.
- Classify files as keep, archive, or drop before cleanup.
- Run the narrowest useful verification instead of defaulting to full rebuilds.

## Good Fit

- Codex sessions that feel context-heavy or repetitive.
- Long-running coding conversations that need a reset.
- Old projects that need lightweight recovery before new work.
- Fast edit mode for small source changes.
- Project handoffs where the next agent should not rediscover everything.

## Not A Good Fit

- Replacing normal debugging, tests, or code review.
- Automatically deleting files without user approval.
- Preserving every historical note as current project context.

## Repository Layout

```text
skills/
  agent-lightweight-maintenance/
    SKILL.md
    agents/
      openai.yaml
```

The skill itself is intentionally limited to `SKILL.md` and `agents/openai.yaml`. This keeps the installed skill lightweight.

## Suggested GitHub Topics

`codex`, `codex-skill`, `ai-coding-agent`, `agent-workflow`, `developer-tools`, `context-management`, `handoff`, `debugging-workflow`

## Install Locally

Copy the skill folder into your Codex skills directory:

```bash
cp -R skills/agent-lightweight-maintenance ~/.codex/skills/
```

Then start a new Codex session and invoke it with:

```text
Use $agent-lightweight-maintenance.
```

## Example Prompt

```text
Use $agent-lightweight-maintenance.

This project feels stuck in a loop. Stop broad exploration, read only the lightweight project map/status files if present, identify the owning files, and give me one smallest next action plus one narrow verification command.
```

## Publishing Checklist

- Keep the skill vendor-neutral and project-neutral.
- Do not include personal paths, project names, or private workflow assumptions.
- Keep generated output, screenshots, logs, and dependency folders out of the repo.
- Keep the installed skill folder small: `SKILL.md` plus optional `agents/openai.yaml`.
