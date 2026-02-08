# Pre-Completion Review Checklist

> Walk through every item before completing an iteration. New items are added as failure modes are discovered. Never remove items.

## Core Checks (Iteration 0 — Seed)

### Content Changes
- [ ] No broken internal links introduced (search for `[[` references to renamed/moved notes)
- [ ] No broken external links introduced
- [ ] Factual claims added or modified have been verified (web search or source cited)
- [ ] No content fabricated without explicit `[needs verification]` or `[unverified]` markers
- [ ] Author's voice and meaning preserved in all edits
- [ ] No notes deleted — only archived or merged with clear trail

### Structural Verification
- [ ] Frontmatter changes follow the vault's established conventions
- [ ] Tag changes use existing taxonomy — no new synonymous tags introduced
- [ ] Folder moves/renames have all inbound links updated
- [ ] No new orphan notes created (notes with zero links that should be connected)
- [ ] Naming conventions match existing vault patterns

### Consistency
- [ ] Formatting matches surrounding notes (heading levels, list styles, callout types)
- [ ] Frontmatter schema is consistent within the affected note type
- [ ] No stale metadata left behind (e.g., `status: draft` on a completed note, wrong dates)

### Knowledge Graph
- [ ] New notes link to related existing notes
- [ ] Bidirectional links added where the relationship is mutual
- [ ] No link rot introduced by structural changes

### Ralph Self-Check
- [ ] Iteration log is complete and honest
- [ ] Rubric self-assessment scores are filled in
- [ ] Any score of 2 or below has a follow-up item in priorities.md
- [ ] Guardrails were not violated during this iteration
- [ ] SKILL.md changes (if any) cite the iteration that motivated them

---
*Add new checks below. Format: `[iteration-NNN]` prefix for traceability.*
