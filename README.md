# Vibe Explainer

A Claude Code skill that generates visual change reports after every coding task. Built for vibe coders who build with AI and need to understand what's happening in their project without reading code.

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

If this repo is registered as a plugin marketplace:

```
/plugin marketplace add CamberCo/vibe-explainer
/plugin install vibe-explainer@vibe-explainer
```

Or install directly from GitHub:

```
/plugin install https://github.com/CamberCo/vibe-explainer
```

### Manual install

Clone this repo and copy the skill folder into your Claude Code skills directory:

```bash
git clone https://github.com/CamberCo/vibe-explainer.git
cp -r vibe-explainer/skills/vibe-explainer ~/.claude/skills/
```

Or to add it to a specific project (so it's shared with anyone who clones the repo):

```bash
cp -r vibe-explainer/skills/vibe-explainer your-project/.claude/skills/
```

### Claude.ai upload

1. Download this repo as a ZIP
2. Go to **Settings > Features > Skills**
3. Upload the ZIP file

### Recommended: Add a CLAUDE.md nudge

For the most consistent behaviour, add this line to your project's `CLAUDE.md`:

```
After completing any coding task, always use the vibe-explainer skill to generate a change report before giving your final summary.
```

## What's included

```
vibe-explainer/
├── .claude-plugin/
│   └── plugin.json              # Plugin metadata
├── skills/
│   └── vibe-explainer/
│       ├── SKILL.md             # Core instructions
│       └── references/
│           ├── output-template.md   # Report structure template
│           └── mermaid-patterns.md  # Diagram pattern library
└── README.md
```

## Cross-agent compatibility

This skill uses the open [Agent Skills](https://agentskills.io) standard (`SKILL.md` format), so it also works with Cursor, Gemini CLI, Codex CLI, and other compatible tools.

## You can also ask for a full project map

Beyond change reports, you can ask Claude: "Map out my entire project" and it will generate a comprehensive `PROJECT-MAP.md` covering your file structure, component relationships, database schema, API routes, external integrations, and environment variables.

## Built by

[CamberCo](https://camberco.co.uk) — Web development and AI consultancy based in Birmingham, UK.

## Licence

MIT
