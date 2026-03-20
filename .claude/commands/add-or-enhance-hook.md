---
name: add-or-enhance-hook
description: Workflow command scaffold for add-or-enhance-hook in oh-my-opencode.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /add-or-enhance-hook

Use this workflow when working on **add-or-enhance-hook** in `oh-my-opencode`.

## Goal

Add a new hook or enhance an existing hook, including implementation, tests, and registration.

## Common Files

- `src/hooks/{hook-name}/index.ts`
- `src/hooks/{hook-name}/*.ts`
- `src/hooks/{hook-name}/*.test.ts`
- `src/hooks/index.ts`
- `src/config/schema/hooks.ts`
- `src/plugin/hooks/*.ts`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Create or modify hook implementation files under src/hooks/{hook-name}/
- Update or add corresponding test files under src/hooks/{hook-name}/
- Update src/hooks/index.ts to register the hook (for new hooks)
- Optionally update src/config/schema/hooks.ts or related schema/config files
- Optionally update plugin hooks or interface files

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.