# agentic — table of contents

**Purpose:** Notes on agentic coding: roles, context, evaluation, and economics. Use the table to choose a file; each row is a **page** you can load without reading siblings.

**Parent:** [brain/INDEX.md](../INDEX.md)

## Pages

| File | Keywords | Use when | Sections (outline) |
|------|----------|----------|---------------------|
| [harness-long-running-ai-coding.md](harness-long-running-ai-coding.md) | harness, generator, evaluator, planner, context anxiety, self-evaluation bias, CLAUDE.md, multi-agent, cost, tokens | Designing or debugging long coding sessions with agents; splitting builder vs reviewer; context rot; specs vs more agents; token and subscription trade-offs | Two failure modes; separate generation from critique; what practitioners built; role separation; context management; cheaper alternative (context files); economics; when to harness; deeper shift |
| [deliberate-mvp-vision-first.md](deliberate-mvp-vision-first.md) | MVP, vision, unconstrained prompt, paid work, scope, sandbagging, estimates, acceptance criteria | Choosing what to ship first with AI; avoiding guessed MVPs; when to dream big vs cut to a small MVP for clients | Opening; The Problem with Starting Small; The Exercise: Vision First, Then Scope Down; Why This Saves Money, Not Just Time; The Discipline of Cutting; The Compound Effect |
| [clarity-over-codegen.md](clarity-over-codegen.md) | clarity, problem definition, fuzzy goals, prompting, acceptance criteria, spec-first, intent, code review, workflow | Designing prompts that specify intent before generating code; avoiding polished confusion; using the model as a clarification engine | The "polished confusion" failure mode; This problem predates AI; AI can help you get clear; The real-world source of fuzziness: people; Why code literacy still matters; The skill shift; Putting it into practice |
| [staged-multi-agent-review-quality.md](staged-multi-agent-review-quality.md) | multi-agent, review, plan gate, qualify, consensus, cross-model, tokens, git, security, reasoning depth, parallel sessions | Staging plan and code review with separate agent context; pipelines; tie-breaking; cross-stack review; token economics; production harness controls | Core pattern (plan + post-implementation review); Operational cadence; Consensus and redundancy; Cross-stack review; Economics; Security and production; Summary |
