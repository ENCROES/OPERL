# Ralph — Self-Improving Vault Improvement Loop

Ralph is a self-improving agent skill that lives inside your Obsidian vault. Each iteration, an agent reads Ralph's instructions, improves your vault (structure, content, linking, consistency), and then improves Ralph's instructions based on what it learned. The instructions bootstrap from a minimal seed into a rich, vault-specific playbook.

## Quick Start

1. Bootstrap the vault first (see `BOOTSTRAP.md` in the vault root).
2. Ensure the vault is a git repo with a GitHub remote (for persistence and rollback).
3. Prompt an agent: "Read `.ralph/SKILL.md` and execute one full iteration of the Ralph loop on this vault."
4. Review the iteration log in `.ralph/learnings/`.
5. Repeat. Each pass makes both the vault and the instructions better.

## How It Works

```
┌─────────────────────────────────────────────┐
│              ITERATION N                     │
│                                              │
│  Orient ─→ Plan ─→ Act ─→ Validate          │
│                              │               │
│                              ▼               │
│                          Reflect             │
│                              │               │
│                    ┌─────────┴─────────┐     │
│                    ▼                   ▼     │
│             Update Vault       Update Ralph  │
│             (content, links,   (SKILL.md,    │
│              structure, tags,   guardrails,   │
│              frontmatter)      rubric,       │
│                                checklist)    │
│                    │                   │     │
│                    └─────────┬─────────┘     │
│                              ▼               │
│                       Git Commit & Push      │
└─────────────────────────────────────────────┘
                       │
                       ▼
               ITERATION N+1
          (reads improved instructions)
```

## What's In the Box

| File | Purpose | Mutability |
|------|---------|------------|
| `SKILL.md` | Agent instructions — the living playbook | Grows every iteration |
| `state.json` | Iteration counter, vault metrics, status, flags | Updated every iteration |
| `guardrails.md` | Hard constraints the agent must never violate | Append-only |
| `priorities.md` | Ordered work queue | Reordered every iteration |
| `rubric.md` | Quality criteria for self-assessment | Refined over time |
| `templates/iteration-log.md` | Structure for iteration documentation | Stable template |
| `templates/review-checklist.md` | Pre-completion checklist | Append-only |
| `learnings/` | Iteration logs — the agent's long-term memory | Append-only |

## Key Properties

**Vault-native**: Ralph lives in `.ralph/` and understands Obsidian conventions — wikilinks, frontmatter, tags, MOCs, folder structure.

**Self-improving**: Instructions get better because every mistake teaches a lesson that gets encoded into SKILL.md, guardrails, or the checklist.

**Non-destructive**: Guardrails enforce meaning preservation, voice preservation, and factual verification. The agent is a steward, not an author.

**Ratcheting quality**: Guardrails and checks only grow. The vault gets strictly harder to break over time.

**Auditable**: Every change traces to an iteration log. Every instruction in SKILL.md cites why it was added.

**Tool-augmented**: The agent can use web search to fact-check, verify external links, and research topics. All tool usage is logged.

**Human-in-the-loop**: Every N iterations (default 5), the agent halts for human review. Guardrail removal always requires human approval.

## Running

Prompt example:

```
Read .ralph/SKILL.md and execute one full iteration of the Ralph loop on this vault.
```

For multiple iterations:

```
Read .ralph/SKILL.md and execute 3 iterations of the Ralph loop on this vault,
pausing between each for my review.
```

## Customization

Before first run, consider editing:

- **`priorities.md`**: Add vault-specific priorities you already know about.
- **`guardrails.md`**: Add vault-specific hard rules (e.g., "never modify anything in /journal — those are personal").
- **`rubric.md`**: Add domain-specific quality criteria (e.g., if it's a research vault, add citation standards).
- **`state.json`**: Adjust `human_review_interval` if 5 is too frequent/infrequent.

## Why Git?

The vault lives in GitHub for three reasons: (1) every iteration is a commit, so any change can be reviewed or reverted; (2) the agent can push changes without needing Obsidian open; (3) the iteration history itself becomes a changelog of vault evolution.
