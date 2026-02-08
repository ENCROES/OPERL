# Bootstrap Instructions for Claude Code

> This file tells Claude Code how to adapt this generic Obsidian vault template for a specific project. **Delete this file after bootstrapping is complete.**

## How to Use This Template

### 1. Setup
```bash
# Clone the template repo (or use GitHub's "Use this template" button)
git clone https://github.com/<YOUR-ORG>/obsidian-vault-template.git my-project-vault
cd my-project-vault
```

### 2. Bootstrap Prompt
Give Claude Code a prompt like this:

```
Read BOOTSTRAP.md, then adapt this Obsidian vault template for the following project:

**Project name**: {your project name}
**Summary**: {what it is — a few sentences}
**Context**: {any additional context: technologies, audience, constraints, inspiration}

Follow the bootstrap process in BOOTSTRAP.md.
```

The key idea: provide enough context for the agent to determine what kind of project this is, then let it decide what knowledge domains, folder structure, and work items make sense.

### 3. What Claude Code Should Do During Bootstrap

#### Phase 1: Understand & Classify
- Read the user's prompt context carefully.
- Determine the project's nature: Is it a software product? A book? A business? A research project? A creative work? A course? A physical product? Something hybrid?
- This classification drives everything — folder structure, note types, TODO items, and Ralph priorities.

#### Phase 2: Fill the Project Brief
- Fill `Project Brief.md` with the what, why, who, success criteria, scope, and constraints from the prompt.
- This is the single source of truth that all other notes will reference.

#### Phase 3: Create Domain Structure
This is the critical step. Based on the project type, create 3–6 domain folders with seed notes. The agent should choose what makes sense — **not** use a predetermined set. Examples:

**Software product** might get:
`Architecture/`, `Design/`, `Implementation/`, `Operations/`, `Reference/`

**Book or written work** might get:
`Research/`, `Outline/`, `Chapters/`, `Characters/`, `Worldbuilding/`

**Business** might get:
`Strategy/`, `Product/`, `Marketing/`, `Operations/`, `Finance/`

**Course or educational content** might get:
`Curriculum/`, `Modules/`, `Assessments/`, `Resources/`

**Research project** might get:
`Literature/`, `Methodology/`, `Data/`, `Analysis/`, `Findings/`

**Hardware / physical product** might get:
`Requirements/`, `Design/`, `Manufacturing/`, `Testing/`, `Supply-Chain/`

**Event or campaign** might get:
`Planning/`, `Logistics/`, `Content/`, `Promotion/`, `Post-Mortem/`

Each domain folder should contain 2–4 seed notes with frontmatter, placeholder structure, and `[[wikilinks]]` to related notes. Every seed note should link back to `[[Project Brief]]` and to sibling notes in related domains.

#### Phase 4: Build the TODO Dashboard
- Replace the generic TODO-02 with project-specific work items.
- Create a phased execution plan that reflects the project's actual workflow.
- Add dependency links between TODOs and the domain notes they produce.
- Use the P0/P1/P2 priority tiers: P0 blocks everything, P1 blocks the first milestone, P2 is future work.

#### Phase 5: Update the MOC
- Replace the "Domains" placeholder in `_MOC.md` with actual domain tables.
- Link every seed note. Verify all wikilinks resolve.

#### Phase 6: Configure Ralph
- Update `.ralph/priorities.md` with project-specific priorities discovered during bootstrap.
- Add any project-specific guardrails to `.ralph/guardrails.md`.
- Add domain-specific quality criteria to `.ralph/rubric.md` if applicable.
- Update `.ralph/state.json` vault metrics to reflect the current note count.

#### Phase 7: Validate & First Ralph Iteration
- Verify all `[[wikilinks]]` resolve to actual files.
- Verify all frontmatter has `tags` and `status` fields.
- Run one full Ralph iteration (read `.ralph/SKILL.md` and execute the loop).
- This validates the entire vault and creates the first learning log.

#### Phase 8: Cleanup
- Delete this `BOOTSTRAP.md` file — it's scaffolding, not vault content.
- Commit and push.

## What Ships in This Template

```
.obsidian/            — Obsidian editor settings
.ralph/               — Self-improving vault agent (Ralph)
  ├── SKILL.md        — Agent instructions (living playbook)
  ├── state.json      — Iteration counter and metrics
  ├── guardrails.md   — Hard constraints (append-only)
  ├── priorities.md   — Work queue (reordered each iteration)
  ├── rubric.md       — Quality criteria
  ├── templates/      — Iteration log and checklist templates
  └── learnings/      — Iteration logs (long-term memory)
Templates/            — Reusable document templates
Project Brief.md      — The P0 document: what, why, who
_MOC.md               — Map of Content (vault index)
TODO Dashboard.md     — Consolidated work tracker
BOOTSTRAP.md          — This file (delete after bootstrap)
```

Everything else — domain folders, seed notes, project-specific templates — gets created by the bootstrapping agent based on what the project actually needs.

## Conventions

- **Frontmatter**: Every note has `tags` and `status` (done/partial/TODO/active/template/blocked).
- **Links**: Use `[[wikilinks]]` for internal references. Bidirectional where mutual.
- **Headings**: H1 = note title (after frontmatter), H2 = sections, H3 = subsections.
- **Status flow**: `TODO` → `active` → `partial` → `done`. Use `blocked` when dependencies aren't met.
- **Tags**: Lowercase, hyphenated. Domain tags match folder names.

## Ralph Quick Reference

After bootstrap, improve the vault iteratively:

```
Read .ralph/SKILL.md and execute one full iteration of the Ralph loop on this vault.
```

Ralph will orient, plan, act, validate, reflect, and self-improve — then commit and push. Each iteration makes the vault (and Ralph's own instructions) better.
