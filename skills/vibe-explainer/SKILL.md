---
name: vibe-explainer
description: Generate a visual "Change Report" after completing any coding task, explaining what changed in plain English with Mermaid diagrams and architecture maps. Use this skill every time you finish implementing, refactoring, fixing, or modifying code — before giving your final summary to the user. Also trigger when the user asks "what did you change?", "explain what happened", "show me a map of the changes", "what does my project look like now?", or any variation of wanting to understand their codebase or recent changes visually. This skill is designed for vibe coders who may not read code fluently and need to understand their project through diagrams and plain-language descriptions.
---

# Vibe Explainer

Generate a visual Change Report after every coding task so non-developers can understand what happened and how their project works.

## Why this matters

The person using this skill may not read code. They're building with AI and need to understand their project well enough to make decisions, explain it to others, debug problems, and stay in control. Your job is to be the translator between code and comprehension.

## When to generate a report

After completing any task that changes code, creates files, modifies database schemas, adds dependencies, or alters how components connect to each other. This includes bug fixes, new features, refactors, config changes, and dependency updates.

Also generate on demand when the user asks to understand their codebase or recent changes.

## Report generation process

### Step 1: Inventory the changes

Before writing anything, assess what actually changed:

- Which files were created, modified, or deleted?
- Were any new dependencies added?
- Did the database schema change?
- Were new API routes or endpoints created?
- Did the relationships between components change?
- Were environment variables or config values added/changed?

### Step 2: Determine report scope

Not every change needs every section. Scale the report to the work:

- **Small fix** (typo, style tweak, single-line bug fix): Brief summary + what-it-means. No diagrams needed.
- **Medium change** (new component, new route, bug fix touching multiple files): Summary + file map + one or two targeted diagrams + what-it-means.
- **Large feature or refactor** (new feature, architectural change, DB migration, multi-file refactor): Full report with all sections.

### Step 3: Write the report

Use the output template in `references/output-template.md`. Read it before writing.

Use the Mermaid pattern library in `references/mermaid-patterns.md` for diagram syntax. Read it before writing any diagrams.

### Writing rules

These are non-negotiable:

1. **No unexplained jargon.** If you use a technical term, define it inline in parentheses the first time. Example: "a React component (a reusable building block of your user interface)".

2. **Lead with what it does, not how it works.** "Users can now reset their password from the login screen" comes before any mention of API routes or database columns.

3. **Every diagram needs a plain-English caption** explaining what the reader is looking at and why it matters.

4. **File paths are always relative to the project root.** No absolute paths.

5. **Group related changes together** by feature or purpose, not by file type. Don't list "all modified .tsx files" — instead group by "Login feature changes" or "Database updates".

6. **Be honest about risk.** If a change touches authentication, payments, data deletion, or anything else with real consequences, flag it clearly in a "Heads Up" callout.

7. **Use the phrase "What this means"** liberally. After any technical explanation, add a sentence starting with "What this means:" that translates it into practical impact.

8. **Action items go at the end.** If the user needs to do anything (set an env variable, run a migration, restart a server, test something manually), collect these into a clear checklist at the bottom.

## Delivering the report

Output the report as a markdown file saved to `docs/change-reports/YYYY-MM-DD-HH-MM-description.md` in the project directory. Use a short kebab-case description of the change, e.g., `2025-06-15-14-30-add-user-auth.md`.

Also print a brief summary (3-5 sentences max) directly in the chat, ending with: "Full change report saved to `docs/change-reports/[filename]`."

If the `docs/change-reports/` directory doesn't exist, create it.

## Full project mapping

When the user asks for a full project overview (not just a change report), generate a comprehensive map covering:

- Project structure overview (what each top-level directory does)
- All major components and how they connect
- Database schema with table relationships
- API routes and what they do
- External services and integrations
- Environment variables and what each one controls
- Data flow for the main user journeys

Save this as `docs/PROJECT-MAP.md` and tell the user where to find it.
