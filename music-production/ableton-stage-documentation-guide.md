# Agent guide — stage docs

This file lives in `docs/stages/` next to the step docs it governs.

Each stage file is a **how-to for one deliverable** referenced by [music-production-process.md](ableton-house-production-workflow.md). The parent doc stays high-level; stage docs hold the build steps.

**Reference:** [stage-1-template-drum-rack.md](ableton-house-drum-rack-template.md)

---

## File naming

```
stage-{N}-{phase-slug}-{task-slug}.md
```

Use `{phase-slug}` when the task belongs to a named phase in the parent doc (e.g. Stage 1 **Template**). Omit it when the task is the phase itself (e.g. sample folder, archive).

Files go in this folder (`docs/stages/`).

| Part | Rule | Example |
|------|------|---------|
| `N` | Stage number from the parent doc (1–6) | `1` |
| `phase-slug` | Phase within the stage, if applicable | `template` |
| `task-slug` | Short kebab-case name for the single task | `drum-rack` |

Examples:

- `stage-1-template-drum-rack.md` — build the house drum rack preset
- `stage-1-template-bass-rack.md` — build the bass rack (future)
- `stage-1-sample-folder.md` — curate the go-to sample folder (future)

One file = one artifact or one prep task. A stage can have several files.

---

## Scope

Each stage doc answers: **what do I build, and how do I know I'm done?**

**In scope:** Ableton steps, naming, save location, checklists, house-specific defaults.

**Appendix:** Never add or write an appendix unless the user explicitly asks. You may suggest topics for a future appendix (e.g. "where to find Drum Rack in the browser") — list suggestions in chat, not in the file.

**Out of scope (keep in the parent doc only):** weekly rhythm, session modes, arrangement rules, mixing workflow, export/archive policy. Link to the parent; do not repeat paragraphs.

**Intro rule:** State the deliverable in the first paragraph (`House Drums.adg`, five pads, track name **Drums**). Say why once (one-time prep). Do not open with template workflow or groove programming unless that *is* the deliverable.

---

## Document structure

Use this order. Omit sections that do not apply.

```markdown
# Stage {N} — {Task title}

**Part of:** [Music Production Process](../music-production-process.md)

{1–2 sentences: deliverable + why once.}

## Examples
- 2–3 bullets: quick paths, not full instructions

## Done when
- [ ] checkboxes — verifiable, specific to this task

## Build (pick one path)
**Path name**
1. numbered steps

## {Reference section}
Tables or defaults (MIDI notes, track names, file names) — only if useful
```

Do not include an **Appendix** section unless the user asks for one.

### Section notes

| Section | Purpose |
|---------|---------|
| **Intro** | Deliverable in 1–2 sentences. Concise. User should know what this doc is for in 10 seconds. |
| **Examples** | Illustrate choices; do not duplicate **Build** steps. |
| **Done when** | Checkbox list. Match the deliverable — not parent-doc goals (e.g. do not add "program a groove in 2 minutes" to a rack-build doc unless that is the task). |
| **Build** | One or more named paths (existing preset / from scratch / hybrid). Numbered steps ending in save + name. |
| **Appendix** | **User permission only.** DAW UI mechanics (browser paths, drag-and-drop, Hot-Swap Sample). If UI steps are unclear, suggest appendix topics in chat — do not draft the section. When writing one after approval: numbered flow, setup first; do not repeat **Build** steps. |

---

## Writing style

- Imperative steps: `New MIDI track → …`
- Bold **track names**, **device names**, and preset filenames (`House Drums.adg`)
- House genre assumed (Ableton Live, arrangement view) — same as parent doc
- No filler ("This doc is about…"). Lead with the deliverable.
- Prefer **replace** over **swap** in UI instructions; use **Hot-Swap Sample** only when naming the Ableton control.

---

## After creating a file

1. Add a link in the parent doc under the matching stage (e.g. Stage 1 Template row or a **Steps** list).
2. Read the intro aloud: if it does not name the artifact, rewrite the intro only — do not restructure the whole doc unless asked.
3. Do not add an appendix unless the user requests it.

---

## Self-review checklist

Before finishing:

- [ ] Filename matches `stage-{N}-{phase-slug}-{task-slug}.md` (or `stage-{N}-{task-slug}.md` when there is no phase) in `docs/stages/`
- [ ] **Part of** link points to `../music-production-process.md`
- [ ] Intro names one deliverable
- [ ] No duplicated paragraphs from the parent doc
- [ ] **Done when** items are testable without starting a creative session
- [ ] No **Appendix** added without explicit user permission
