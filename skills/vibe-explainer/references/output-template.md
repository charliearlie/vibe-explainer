# Change Report Output Template

Use this template structure for every change report. Skip sections that aren't relevant to the scope of the change (see "Determine report scope" in SKILL.md).

---

## Template

```markdown
# Change Report: [Short human-readable title]

**Date:** [YYYY-MM-DD HH:MM]
**Scope:** [One sentence: what was the goal of this work]

---

## What Changed (The Quick Version)

[2-4 bullet points in plain English. No file names, no code. Just what's different from the user's perspective.]

- Users can now...
- The app no longer...
- Performance improved for...

---

## Visual Map

[Include the most useful diagram(s) for this change. Pick from the patterns in mermaid-patterns.md. Always add a caption below each diagram.]

### [Diagram Title]

```mermaid
[diagram code]
```

**What you're looking at:** [1-2 sentences explaining the diagram for someone who's never seen one before. Point out the key thing to notice.]

---

## What Was Changed (The Details)

### [Group Name — e.g., "User Authentication" or "Homepage Layout"]

**Files touched:**
- `path/to/file.tsx` — [one-line description of what this file is responsible for]
- `path/to/other-file.ts` — [one-line description]

**What happened:**
[2-3 sentences in plain English explaining the change. Lead with the user-facing impact.]

**What this means:** [One sentence translating this into practical terms for the project owner.]

[Repeat this block for each logical group of changes]

---

## Database Changes

[Only include if the database schema was modified]

**New tables:**
- `table_name` — [what it stores, in plain English]

**Modified tables:**
- `table_name` — [what changed and why]

```mermaid
[ER diagram showing affected tables and their relationships]
```

**What you're looking at:** [Explain the boxes and lines. "Each box is a database table — think of it like a spreadsheet. The lines show which tables reference each other."]

---

## New Dependencies

[Only include if new packages/libraries were added]

| Package | What it does | Why it was added |
|---------|-------------|-----------------|
| `package-name` | [plain English] | [reason] |

---

## ⚠️ Heads Up

[Only include if changes touch sensitive areas: auth, payments, data deletion, security, external APIs, or anything with real-world consequences]

- [Clear description of the risk or important consideration]
- [What could go wrong if this isn't handled properly]

---

## Action Items

[Only include if the user needs to do something]

- [ ] [Action item with specific instructions]
- [ ] [Another action item]

Example:
- [ ] Add `DATABASE_URL` to your `.env` file — ask me if you need help with this
- [ ] Run `npm run db:migrate` to update your database
- [ ] Test the login flow manually to make sure it works as expected
```

---

## Scaling guidance

**Small fix (< 3 files, no architecture change):**
Use only: What Changed (Quick Version) + one detail group + Action Items if needed.

**Medium change (3-10 files, new component/route):**
Use: Quick Version + Visual Map (one diagram) + Detail groups + Action Items.

**Large feature/refactor (10+ files, new architecture, DB changes):**
Use the full template. Consider multiple diagrams showing different aspects (component relationships, data flow, DB schema).
