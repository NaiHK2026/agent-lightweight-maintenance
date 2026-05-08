---
name: agent-lightweight-maintenance
description: Use as an AI coding agent loop breaker and context cleanup workflow when the agent repeats broad exploration, carries stale assumptions, bloats context, turns small edits into long sessions, or needs lightweight recovery, fast edit, handoff, or project slimming before continuing work.
---

# Agent Lightweight Maintenance

Use this skill to stop looped work, reduce context weight, and keep the next action small, verifiable, and easy to hand off.

This skill does not run on a timer by itself. Use it at checkpoints:

- after the agent repeats the same plan or file scan twice
- when a small code edit becomes a broad repository investigation
- before opening a new agent conversation
- before copying an old project into a new project
- before commit or handoff after a long session
- after a build/debug loop lasts more than 2-3 attempts
- when the user asks for "fast edit", "context cleanup", "reduce weight", "stop exploring", "handoff", or equivalent wording

## Core Rule

Stop expanding context. Preserve only what is needed for the next concrete task.

Prefer:

- project rules or agent instructions, if present
- a lightweight project map, if present
- a current status or handoff file, if present
- directly relevant source files
- the narrowest verification command
- a short handoff note

Avoid:

- re-reading the whole repository
- listing large asset or dependency folders
- inspecting generated output unless directly required
- repeating old plans
- carrying stale assumptions
- copying exploratory notes into new projects

## Lightweight Files

Read these only if they exist and are relevant:

- `AGENTS.md`
- `docs/source-map.md`, `SOURCE_MAP.md`, or another project map
- `docs/progress.md`, `STATUS.md`, `WORKLOG.md`, or another current status file
- `docs/verification.md` or documented verification commands
- directly relevant source files

Do not assume these files exist. Do not create new governance files unless they reduce future work.

Status files are not worklogs. They should hold current state, next action, blockers, verification, and "Do Not Revisit" only.

## Stale Context Rules

- If a feature is retired, mark it retired in the project map or status before editing behavior.
- Move old attempts, long verification history, browser passes, and exploratory notes out of current status.
- If project map, status, and source code disagree, stop and resolve the disagreement before editing behavior.
- For large files, use targeted search to find the owning region before reading broadly.
- If the same fix or plan repeats twice, stop and produce a Loop Break Summary instead of trying again.

## Lightweight Recovery Flow

1. Read project rules if present.
2. Read the lightweight project map if present.
3. Read the current status or handoff file if present.
4. State the current objective in one sentence.
5. Identify the smallest files that own the behavior.
6. Ignore generated output such as `dist/`, `build/`, `.next/`, `out/`, `_site/`, `coverage/`, screenshots, logs, and temporary exports unless directly required.
7. Make or recommend the smallest coherent next action.
8. Run the narrowest useful verification command.
9. Update an existing status file only with current state, next step, blocker, verification result, and "Do Not Revisit".
10. Report briefly.

## Project Slimming / Handoff Flow

When reducing an old project or preparing a lightweight transfer:

1. Do not copy the whole repository blindly.
2. Keep source files required for current behavior.
3. Keep minimal governance files that actively reduce future work.
4. Keep docs that are still used by the current project.
5. Keep runtime assets required by current pages, builds, tests, or demos.
6. Do not copy dependency folders, generated output, screenshots, logs, old exports, unused raw assets, speculative plans, stale drafts, or duplicated notes.
7. If unsure whether to remove a file, put it on an archive proposal first instead of deleting it.

## Keep / Archive / Drop

Use this classification:

- **Keep**: needed for build, current behavior, deployment, tests, or the next task.
- **Archive**: useful history, but not needed for the next task.
- **Drop**: generated output, duplicates, stale plans, local junk, unused experiments, or dependency folders.

Never delete user work unless explicitly asked. Prefer reporting a proposed cleanup list first.

## Loop Break Prompt

When a session is looping, reset with:

```text
Use $agent-lightweight-maintenance.

Stop broad exploration. Read only project rules, a lightweight project map, and a current status or handoff file if present.

Summarize:
- current objective
- files that actually own the current issue
- what has already been tried
- conflicting docs or stale assumptions
- retired features that should not be revisited
- one smallest next action
- one narrow verification command

Do not repeat old plans. Do not inspect generated output or large asset folders unless directly required.
```

## Loop Break Summary

Use this exact shape after repeated attempts:

```text
Current objective:
Already tried:
Conflicting docs:
Retired assumptions:
Owning files:
Smallest next action:
Narrow verification:
Do not revisit:
Blocker:
```

Do not continue implementation until the loop is reduced to one smallest next action.

## Handoff Output

A lightweight handoff should be under 12 lines:

```text
Objective:
Current state:
Relevant files:
Already tried:
Next action:
Verification:
Do not revisit:
Blocker:
```

## Reporting

Keep the final report short:

- what was kept or changed
- what was intentionally ignored
- verification result
- next concrete action
