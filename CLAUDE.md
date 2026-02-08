# OPERL — Obsidian Vault Template with Self-Improving Agent (Ralph)

## What This Is

A distributable Obsidian vault template. Users clone it, run the bootstrap process with their project context, and get a fully structured knowledge base with a built-in self-improving agent called Ralph.

## Project Structure

```
BOOTSTRAP.md              — Instructions for adapting the template (delete after use)
Project Brief.md          — P0 document: what, why, who, success criteria
TODO Dashboard.md         — Consolidated work tracker (P0/P1/P2 tiers)
_MOC.md                   — Map of Content (vault index / navigation hub)
Templates/                — Reusable document templates
.obsidian/                — Obsidian editor settings
.ralph/                   — Self-improving agent framework (see .ralph/CLAUDE.md)
  SKILL.md                — Agent playbook (living instructions, grows each iteration)
  state.json              — Iteration counter, metrics, status flags
  guardrails.md           — Hard constraints (append-only, never remove)
  priorities.md           — Ordered work queue
  rubric.md               — Quality criteria for self-assessment
  templates/              — Iteration log and review checklist templates
  learnings/              — Iteration logs (agent long-term memory)
```

## Two Workflows

### 1. Bootstrap (first run on a new project)
Prompt: `Read BOOTSTRAP.md and adapt this vault for [project context]`

The agent classifies the project, fills the Project Brief, creates domain folders with seed notes, builds the TODO Dashboard, updates the MOC, configures Ralph, runs validation, then deletes BOOTSTRAP.md.

### 2. Ralph Iteration (ongoing improvement)
Prompt: `Read .ralph/SKILL.md and execute one full iteration of the Ralph loop`

The agent orients, plans (max 3 items), acts, validates, reflects, self-improves Ralph's own files, then commits. Each iteration improves both the vault and the instructions.

## Conventions

- **Frontmatter**: Every `.md` note has YAML frontmatter with `tags` (array) and `status` (one of: `TODO`, `active`, `partial`, `done`, `blocked`, `template`)
- **Links**: Use `[[wikilinks]]` for internal references. Bidirectional where mutual.
- **Headings**: H1 = note title, H2 = sections, H3 = subsections
- **Tags**: Lowercase, hyphenated. Domain tags match folder names.
- **Status flow**: `TODO` -> `active` -> `partial` -> `done`. Use `blocked` when dependencies unmet.

## Critical Rules

1. **Never fabricate content.** Factual claims must be verified. Mark unverified content with `[needs verification]`.
2. **Never alter meaning.** Fix structure and formatting; leave opinions and claims intact.
3. **Preserve voice.** Match the vault owner's tone. Don't impose generic assistant voice.
4. **Max 3 scope items per Ralph iteration.** Overreach causes inconsistency.
5. **Guardrails are append-only.** Never remove a guardrail. Propose removal via `state.json` flag.
6. **Every iteration gets a log.** Even failed ones. Especially failed ones.
7. **No destructive git ops.** No force push, no history rewrite, no publishing without human authorization.
8. **`.ralph/` is isolated.** Never move Ralph files out of `.ralph/`. Never merge agent operational files with vault content.

## Verification

After any changes, verify:
- All `[[wikilinks]]` resolve to actual files
- All frontmatter has `tags` and `status` fields
- No orphan notes introduced that should be connected
- Link count did not decrease (no link rot)
- `state.json` metrics are current
