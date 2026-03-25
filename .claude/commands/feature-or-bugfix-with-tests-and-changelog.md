---
name: feature-or-bugfix-with-tests-and-changelog
description: Workflow command scaffold for feature-or-bugfix-with-tests-and-changelog in clawdbot.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /feature-or-bugfix-with-tests-and-changelog

Use this workflow when working on **feature-or-bugfix-with-tests-and-changelog** in `clawdbot`.

## Goal

Implements a new feature or bugfix, updates implementation, adds/updates tests, and updates the changelog.

## Common Files

- `src/**/*.ts`
- `src/**/*.test.ts`
- `extensions/**/*.ts`
- `extensions/**/*.test.ts`
- `CHANGELOG.md`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Edit or add implementation files (e.g., src/ or extensions/)
- Edit or add corresponding test files (*.test.ts)
- Update CHANGELOG.md with a summary of the change

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.