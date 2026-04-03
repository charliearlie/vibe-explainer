# Vibe Explainer

A Claude Code plugin that generates visual change reports after every coding task. Built for vibe coders who build with AI and need to understand what's happening in their project without reading code.

## What it does

After Claude Code finishes any task, it automatically generates a **Change Report** containing:

- **Plain-English summary** of what changed and why it matters
- **Mermaid diagrams** showing how components connect, how data flows, and what the database looks like
- **File change maps** highlighting what was added, modified, or deleted
- **Risk flags** when changes touch sensitive areas like auth, payments, or data deletion
- **Action items** if you need to do anything (set env variables, run migrations, etc.)

Every technical term is explained in plain language. Every diagram has a caption telling you what you're looking at.

## Example output

After adding user authentication to a Next.js app, you'd get a report including:

- A sequence diagram showing the login flow (user → app → auth service → database)
- An entity-relationship diagram of the new `users` and `sessions` tables
- A file change map showing which files were created vs modified
- A checklist: "Add `AUTH_SECRET` to your `.env` file"

Reports are saved to `docs/change-reports/` in your project so you can always look back at what changed and when.

## Install

### Claude Code Plugin (recommended)

**Step 1:** Register the marketplace:

```
/plugin marketplace add charliearlie/vibe-explainer
```

**Step 2:** Install the plugin:

```
/plugin install vibe-explainer@vibe-explainer
```

That's it. The skill will now activate automatically after coding tasks.

### Manual install

If you prefer not to use the plugin system, clone and copy the skill folder directly:

```bash
git clone https://github.com/charliearlie/vibe-explainer.git
cp -r vibe-explainer/plugins/vibe-explainer/skills/vibe-explainer ~/.claude/skills/
```

Or to add it to a specific project (so it's shared with anyone who clones the repo):

```bash
cp -r vibe-explainer/plugins/vibe-explainer/skills/vibe-explainer your-project/.claude/skills/
```

### Claude.ai upload

1. Download the `vibe-explainer.skill` file from [Releases](https://github.com/charliearlie/vibe-explainer/releases)
2. Go to **Settings > Features > Skills**
3. Upload the file

### Recommended: Add a CLAUDE.md nudge

For the most consistent behaviour, add this line to your project's `CLAUDE.md`:

```
After completing any coding task, always use the vibe-explainer skill to generate a change report before giving your final summary.
```

## Repo structure

```
vibe-explainer/
├── marketplace.json                          # Marketplace catalog
├── plugins/
│   └── vibe-explainer/
│       ├── .claude-plugin/
│       │   └── plugin.json                   # Plugin metadata
│       └── skills/
│           └── vibe-explainer/
│               ├── SKILL.md                  # Core instructions
│               └── references/
│                   ├── output-template.md    # Report structure template
│                   └── mermaid-patterns.md   # Diagram pattern library
├── README.md
└── LICENSE
```

## Full project mapping

Beyond change reports, you can ask Claude: "Map out my entire project" and it will generate a comprehensive `PROJECT-MAP.md` covering your file structure, component relationships, database schema, API routes, external integrations, and environment variables.

## Cross-agent compatibility

This skill uses the open [Agent Skills](https://agentskills.io) standard (`SKILL.md` format), so it also works with Cursor, Gemini CLI, Codex CLI, and other compatible tools. For manual install on those platforms, copy the `skills/vibe-explainer/` directory into the appropriate skills location for your tool.

## Built by

[CamberCo](https://camberco.co.uk) — Web development and AI consultancy based in Birmingham, UK.

## Licence

MIT
