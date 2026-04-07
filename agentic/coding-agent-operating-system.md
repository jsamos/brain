# Coding Agent Operating System: Rules, Skills, State, and Workflow

Source: `https://www.reddit.com/r/ClaudeCode/comments/1seq4lc/please_can_someone_who_is_really_building/`

## Contents

 - [What this optimizes for](#what-this-optimizes-for)
 - [A pragmatic coding-agent playbook](#a-pragmatic-coding-agent-playbook)
 - [Rules vs Skills: a structure that keeps things consistent](#rules-vs-skills)
 - [A concrete day-to-day flow (research → build → ship)](#day-to-day-flow)
 - [Copy/paste prompt templates (adapt to your repo)](#prompt-templates)
 - [Sessions and terminal layout: reducing “multiple sessions” chaos](#sessions-and-terminal-layout)

<a id="what-this-optimizes-for"></a>
## What this optimizes for

- Consistency across sessions
- Low cognitive load (fewer decisions about “which workflow do I run now?”)
- Clear separation between “figure out what to do” and “do it”
- Guardrails that are always-on (rules) vs capabilities that are invoked (skills)

<a id="a-pragmatic-coding-agent-playbook"></a>
## A pragmatic coding-agent playbook

### The core diagnosis

If everything is a “skill”, consistency becomes opt-in. If everything is “agents”, orchestration debt and context sprawl creep in. The core principle:

- Use **rules** for always-on behavior and constraints.
- Use **skills** for on-demand, high-leverage workflows.
- Use **markdown state** so each session doesn’t reset to zero.
- Use **separate sessions** for research vs build to prevent scope creep.

### The simplest structure that still scales

- A small set of **rule files** that load every session (identity, behavioral constraints, operational workflow).
- A small set of **pipeline skills** that cover your recurring end-to-end loops (feature work, ship, PR handling).
- A lightweight **state folder** (plans, decisions, session handoff, todos) that the agent reads/writes every time.

### Practical heuristics

- Prefer **rules over skills** for anything that must happen every session.
- Split **research** and **build** into separate sessions; the research session outputs a plan file, the build session executes it.
- Persist “memory” in **markdown files**, not only chat history.
- Scope specialized helpers narrowly; avoid dumping global context into every helper.
- Consolidate skills aggressively; if a skill triggers less than weekly, it likely shouldn’t exist.
- Reduce cognitive load by sequencing skills into a **pipeline** so you’re not constantly choosing “what now?”
- Keep an eye on **context growth**; start fresh plans at natural boundaries instead of dragging stale context.
- Treat state files as an interface: keep always-on guidance minimal, and pull in specialized workflows only when the current phase requires them.

### What “good” looks like day-to-day

- You can answer “what are we doing and why?” by opening one folder of markdown.
- There is a single default “rail” for feature work (plan → implement → test → ship) and deviations are explicit.
- PRs stop feeling like bureaucracy because they become a repeatable quality gate (tests, changelog, checklist), not an improvisation session.

<a id="rules-vs-skills"></a>
## Rules vs Skills: a structure that keeps things consistent

### The distinction (the lever)

- **Rules**: always-on constraints and standards that should apply every session without you remembering to invoke anything.
- **Skills**: on-demand workflows you call when needed.

If you put standards into skills, your “system” becomes optional and inconsistent.

### A minimal rule set (3 files)

#### 1) Identity

Defines who the assistant is in this repo and what it is optimizing for.

- Role: senior pair programmer
- Boundaries: what it can/can’t change without explicit approval
- Relationship: how it should use specialized helpers (if at all)

#### 2) Behavioral (hard constraints from real failures)

Encode rules only after you’ve been burned by the failure.

- Don’t present uncertainty as fact
- Verify before asserting
- If the same mechanism fails twice, pivot to a different approach
- Don’t expand scope without stating tradeoffs and asking for prioritization

#### 3) Operational (how work happens)

Your workflow protocol.

- Where plans live
- What to read at session start
- How to hand off state at session end
- How to stage changes and how to check quality gates
- How to pass context to specialized helpers (scoped only)

### What should be a skill (and what shouldn’t)

#### Skills that tend to pay for themselves

- A “feature rail” that outputs a plan file, then executes it
- A “ship rail” that runs checks, updates changelog, and prepares a PR description
- A “self-review rail” that validates against repo conventions and quality gates

#### Skills that tend to become clutter

- Skills that replicate native behavior with extra ceremony
- Skills that you invoke rarely or only for novelty
- Multiple skills that always run together (merge them)

### Pipeline thinking: remove the “which skill now?” decision

Instead of 18 unrelated skills, aim for 3–6 rails:

- Intake → clarify → plan
- Implement → test → integrate
- Review → fix → ship

If you need special modes (security pass, perf pass), they slot into the rail rather than becoming separate entry points.

<a id="day-to-day-flow"></a>
## A concrete day-to-day flow (research → build → ship)

### Principle: separate “figure out what to do” from “do it”

The strongest workflow advice here is splitting sessions:

- **Research session**: clarifies requirements, scans codebase, proposes options, writes a plan to markdown.
- **Build session**: reads the plan, implements exactly that, runs checks, prepares a PR.

This reduces scope creep and makes the work auditable.

### Suggested state files (small, boring, reliable)

- `plan.md`: the approved plan for the current slice of work
- `decisions.md`: architecture decisions + why
- `session_handoff.md`: what changed, what’s next, what to verify
- `todo.md`: the smallest next actions

### Feature flow template

#### Research session output

- Problem statement (what “done” means)
- Constraints (security, performance, timelines)
- Proposed approach
- File/area touch list
- Tests/checks to run
- Rollback strategy (if relevant)

#### Build session execution

- Load `plan.md`
- Implement in small, reviewable slices
- Keep context lean; reset between major steps if needed
- Verify with tests/checks
- Self-review against rules/conventions
- Prepare PR: description, checklist, changelog updates if your org requires it

### PR handling stance (hybrid, not fully automated)

Two competing realities:

- The agent catches a lot.
- Humans still need a shared “definition of done” and a safety net.

A workable hybrid:

- Automate repeatable checks (tests, lint, changelog discipline, basic security checks).
- Keep manual review as a final gate for high-risk changes and for knowledge sharing.

<a id="prompt-templates"></a>
## Copy/paste prompt templates (adapt to your repo)

### Session start (load state, set boundaries)

Ask:

- Read `plan.md`, `decisions.md`, `session_handoff.md`, `todo.md` from the project state folder.
- Summarize the current objective in 3 bullets.
- List the next 5 actions, smallest-first.
- State what you will not do without explicit approval.

### Research session template (outputs a plan file)

Ask:

- Clarify “definition of done” with questions (only what’s necessary).
- Scan the codebase to locate where changes should happen.
- Propose 1–2 implementation options with tradeoffs.
- Write `plan.md` with:
  - Scope
  - Steps
  - Files to touch
  - Risks
  - Test plan
  - Rollback plan (if needed)

### Build session template (executes the plan)

Ask:

- Read `plan.md` and restate it as a checklist.
- Implement step-by-step, stopping after each step to verify locally.
- Keep changes small; prefer incremental commits.
- After implementation, run tests/lint/build and report results.
- Write `session_handoff.md` with what changed and what to do next.

### Specialized helper scoping template

Ask:

- Create a specialized helper with only:
  - The specific task
  - The relevant file paths
  - The relevant constraints (rules)
  - The expected output format

Avoid:

- Passing the entire repo context or all “memory” to every helper.

### “Two-strike pivot” template (when stuck)

Ask:

- If you attempt the same mechanism twice and it fails, stop.
- Explain why it’s failing.
- Propose a fundamentally different approach.
- Pick the safest alternative and proceed.

<a id="sessions-and-terminal-layout"></a>
## Sessions and terminal layout: reducing “multiple sessions” chaos

### What this suggests

- A single session per project can outperform many sessions if it keeps you oriented.
- If you do parallelize, use structure (named sessions/windows/worktrees) rather than freeform terminals.

### Practical options mentioned

- A terminal session orchestrator for returning to named sessions
- A terminal multiplexer with a more visible UI and named panes/windows
- A terminal app with a spatial layout (e.g. a predictable 2x2 grid per project) and a left-side project/session overview

### Layout principle: keep it spatial and predictable

One stable layout reduces overhead:

- Editor
- Coding agent session
- Tests / CI / build runner
- “General” shell (git, ssh, logs)

