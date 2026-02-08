Run a full validation pass on this vault without making changes.

## Checks
1. **Link integrity**: Find all `[[wikilinks]]` and verify each resolves to an actual file.
2. **Frontmatter**: Every `.md` file (except in `.ralph/` and `.obsidian/`) has YAML frontmatter with `tags` (array) and `status` fields.
3. **Orphan detection**: Find notes with zero inbound or outbound wikilinks that should be connected.
4. **Stub detection**: Find notes under 100 words with no outbound links.
5. **Tag consistency**: List all tags in use and flag potential duplicates or inconsistencies.
6. **MOC coverage**: Verify `_MOC.md` links to all domain folders and key notes.
7. **Rubric assessment**: Score each dimension in `.ralph/rubric.md` (1-5).
8. **Guardrail compliance**: Verify no guardrail violations exist in the current vault state.

## Output
Print a structured report with:
- Pass/fail for each check
- Counts: total notes, orphans, broken links, stubs, notes without frontmatter
- Rubric scores
- Recommended priorities for the next Ralph iteration
- Do NOT make any changes — report only.
