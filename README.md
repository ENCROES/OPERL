# OPERL

An Obsidian vault template with a built-in self-improving AI agent called Ralph.

Provide a project description, and the agent builds a structured knowledge base — domain folders, seed notes, wikilinks, a TODO dashboard, and a Map of Content. Ralph then iterates on the vault continuously, improving both the content and its own instructions each cycle.

## Quick Start

In Claude Code:

```
Read BOOTSTRAP.md and adapt this vault for: [your project description]
```

The agent classifies your project, creates the structure, fills in the brief, and hands you a working vault.

## Structure

```
BOOTSTRAP.md          — One-time setup instructions (deleted after use)
Project Brief.md      — Project definition: what, why, who, success criteria
TODO Dashboard.md     — Work tracker (P0/P1/P2 tiers)
_MOC.md               — Map of Content (vault index)
Templates/            — Reusable document templates
.ralph/               — Self-improving agent framework
```

## Ralph

Ralph is a self-improving agent that runs inside the vault. Each iteration follows a loop: orient, plan (max 3 items), act, validate, reflect, self-improve, commit. Every iteration improves the vault and refines Ralph's own instructions.

Run an iteration:

```
Read .ralph/SKILL.md and execute one full iteration of the Ralph loop on this vault.
```

## Credits

The Ralph loop was created by [Geoffrey Huntley](https://github.com/ghuntley).

## License

See repository for license details.
