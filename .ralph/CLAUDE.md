# .ralph/ — Ralph Framework Rules

> These rules apply when an agent is working inside `.ralph/`. They supplement the root CLAUDE.md.

## What This Directory Is

Ralph's workspace. Contains the self-improving agent's instructions, state, guardrails, quality rubric, and iteration logs. This is the agent's "brain" — the vault content outside `.ralph/` belongs to the human.

## Mutation Rules

| File | Rule | Rationale |
|------|------|-----------|
| `SKILL.md` | Append new heuristics, refine existing. Every addition must cite the iteration that motivated it. | Prevents speculative bloat. |
| `guardrails.md` | **Append-only.** Never remove or weaken a guardrail. | Safety ratchet. |
| `rubric.md` | Refine criteria, add new dimensions. Never lower the bar. | Quality ratchet. |
| `priorities.md` | Reorder freely. Add discovered items. Move completed items to "Completed" section. | Living work queue. |
| `state.json` | Increment `iteration`, update `last_updated`, update `vault_metrics`, set flags. Never reset the counter. | Audit trail. |
| `templates/` | Stable. Only modify to add fields, never remove existing fields. | Backwards compatibility with existing logs. |
| `learnings/` | **Append-only.** Never edit past iteration logs. They are the historical record. | Integrity of memory. |

## When Modifying SKILL.md

1. New instructions must trace to a specific iteration where their absence caused a problem.
2. Do not add speculative rules ("this might help someday").
3. If an existing instruction is unclear, clarify it — don't duplicate it with a slightly different phrasing.
4. Keep the file under control. If it grows past ~300 lines, consider whether instructions have become redundant.

## When Adding Guardrails

Format: `### G-NNN: Title` followed by the rule and a citation like `*(Added iteration 5 — near-miss with meaning alteration)*`.

## state.json

Read `state.json` directly for the current schema. Key constraint: never reset the `iteration` counter.
