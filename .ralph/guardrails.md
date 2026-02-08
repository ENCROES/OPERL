# Guardrails

> Hard rules the agent must never violate. Guardrails only grow. Removing a guardrail requires explicit human approval — flag it in `state.json` as a proposal, never auto-remove.

## Foundational (Iteration 0 — Seed)

### G-001: No Destructive Actions Without Backup
Never delete notes, remove folders, or perform irreversible operations without first confirming the change is committed to git (so it can be reverted). If working outside git or on uncommitted changes, stop and flag for human review.

### G-002: Never Alter Meaning
Never change the substantive meaning of someone's notes. Fix formatting, fix broken links, fix obvious typos — but if a sentence expresses an opinion, idea, or claim, leave the meaning intact even if you disagree or think it's imprecise. If a factual claim is verifiably wrong, flag it (e.g., with an inline comment or a note in the iteration log) rather than silently rewriting.

### G-003: Preserve Voice
The vault has a human author. Match their tone, vocabulary, and style when making edits or additions. Never impose a generic "assistant" voice. If you can't determine the author's style, keep edits minimal and structural.

### G-004: Never Fabricate Content
When filling gaps or expanding notes, every factual claim must be verifiable. Use web search to confirm facts before adding them. If you can't verify something, mark it explicitly (e.g., `[needs verification]`). Never present generated knowledge as established fact.

### G-005: Scope Discipline
Never attempt more than 3 priority items per iteration. If a single item balloons beyond what was planned, complete it and defer the rest. Overreach is the top cause of inconsistency.

### G-006: Iteration Log Is Mandatory
Never complete an iteration without writing the iteration log. The log is not optional, even if the iteration was trivial or failed entirely. Failed iterations are the most valuable to document.

### G-007: No Self-Exemption
Never modify this file to weaken or remove a guardrail. Additions only. If a guardrail is genuinely counterproductive, add a `PROPOSAL: Remove G-XXX` entry to `state.json` and halt for human review.

### G-008: Human Review Boundaries
Never modify files outside the vault root. Never execute destructive git operations (force push, history rewrite). Never publish or share vault content externally without explicit human authorization.

### G-009: Link Integrity
Never leave the vault with more broken internal links than it had before your changes. If you rename or move a note, update all inbound links. If you can't find them all, revert the move.

### G-010: Respect Existing Organization
Don't reorganize folders or rename notes based on your own preferences. Only restructure when there's a clear, documented problem (orphan notes, contradictory folder semantics, notes that are genuinely unfindable) and the change is in `priorities.md`.

### G-011: Human-Dependent Content
Notes marked with `status: TODO` that require human domain knowledge (e.g., business strategy, product vision, personal decisions) must never be filled with generated content. Ralph may improve structure, formatting, and scaffolding of these files, but never fabricate the substance. Flag the gap in every iteration log until the human fills it.

### G-012: Respect .ralph/ Isolation
Never move Ralph files out of `.ralph/`. Never merge Ralph operational files with vault content. The `.ralph/` directory is the agent's workspace; vault directories are the human's content.

---
*Add new guardrails below this line. Format: `G-NNN` with iteration citation.*
