# The Feedback Loop Your AI Coding Workflow Is Missing

**Sources**

- [Anthropic — Harness design for long-running applications](https://www.anthropic.com/engineering/harness-design-long-running-apps)
- [r/ClaudeAI — Anthropic shares how to make Claude code better with a harness](https://www.reddit.com/r/ClaudeAI/comments/1s6jouf/anthropic_shares_how_to_make_claude_code_better/)

---

Large language models can write code. That much is settled. What remains unsettled is what happens when you ask one to keep writing code, hour after hour, across hundreds of files, through shifting requirements and accumulating context. Anthropic's engineering team recently published a detailed post on designing what they call a "harness" for long-running AI applications. The 100+ comments that followed on r/ClaudeAI constitute a field report from the people who have been building these systems in production, often before the blog post gave them a name.

## Two failure modes that define the problem

Anthropic identifies two core weaknesses in extended AI coding sessions, and virtually every practitioner in the discussion confirms encountering both.

**Context anxiety** is the degradation of coherence as the conversation grows. Early in a session, the model has a clear picture of the project. By the time the context window approaches its physical limit, that picture has been overwritten by a pile of diffs, error messages, discarded plans, and stale instructions. The model does not forget in the way a person forgets; it drowns. Outputs begin to contradict earlier decisions, variable names get hallucinated, and architectural choices quietly reverse themselves.

**Self-evaluation bias** is more insidious. When asked to review its own work, a model overwhelmingly approves it. One developer describes building a separate evaluation step that explicitly instructs the evaluator to "ignore your previous output and evaluate from first principles," because without that directive, the evaluator agrees with the generator roughly 90% of the time. The model is not lying; it is structurally incapable of adversarial self-assessment when the same weights, the same training, and the same prompt context produce both the work and the judgment.

## The core idea: separate generation from critique

The architecture Anthropic proposes draws on the intuition behind generative adversarial networks. Instead of one model doing everything, you split the work:

- A **generator** produces code, designs, or plans.
- An **evaluator** provides structured critique against explicit criteria.
- Optionally, a **planner** sits above both, decomposing the task and routing subtasks.

For frontend work, the post recommends four scoring criteria emphasizing aesthetics and creativity, with somewhere between five and fifteen revision cycles producing results that break free of default "template soup." For full-stack applications, a three-agent architecture (planner, generator, evaluator) is presented as the baseline.

The mechanism is not magic. It is iteration with feedback, which is what every well-run engineering team already does when a developer writes code and a reviewer reads it. The novelty is in systematizing that loop for autonomous agents that would otherwise run unchecked.

## What practitioners have actually built

The discussion reveals that many developers arrived at these patterns independently, often with considerably more complexity than the three-role baseline.

One developer describes a system with approximately twelve specialized roles: pseudo-code writers, test writers, code implementers, contract definers, code reviewers, and a compliance reviewer that checks output against the original specification. The key insight from this setup is that **contract testing** was the single biggest contributor to eliminating hallucinated features. The model's habit of helpfully adding unrequested functionality, which can cascade into system-breaking side effects, stopped almost entirely once a dedicated agent existed whose only job was to verify that the delivered code matched a formally defined contract.

Another practitioner working on an autonomous background execution system (running Claude Code jobs without human supervision) reports that the hardest engineering problem was not orchestration at all. It was **writing task definitions tightly enough** that the model could complete them without mid-run course correction. This is a crucial and underappreciated distinction: the instinct when output quality drops is to add another review agent, but the actual fix is often a better-scoped task with a clearer definition of "done."

A third developer runs five specialized sub-agents on every pull request: performance, security, regression, database, and requirements. The reviews consistently catch issues and suggest "niche performance increases" that would otherwise slip through.

## The role separation principle

The deepest technical lesson running through the discussion is that **the evaluator must not optimize for the same objective as the generator**.

Generators naturally optimize for "does it work" or "does it match the request." Evaluators need fundamentally different questions: Is the code safe? Is it maintainable? Does it introduce regressions? Does it respect the boundaries of what was asked? These are orthogonal concerns, and treating them as one question (by having the same model check its own output with a mild "please review" prompt) collapses the adversarial tension that makes the pattern work.

Several commenters push this further: ideally, the evaluator should be a **different model or a different provider entirely**. If both generator and evaluator are the same model with the same training biases, certain classes of error will be systematically invisible to both. Using, say, Claude for generation and a different model for review introduces genuine diversity of perspective. Not everyone has the budget for this, but even using **different prompts with different evaluation rubrics** for the same model produces measurably better results than a generic "check this code" instruction.

## Context management: the unglamorous backbone

While role separation gets the conceptual spotlight, the practitioners emphasize that **state and memory management** is what determines whether a multi-agent system actually works in production versus merely impressing in a demo.

Key operational patterns that emerge:

**Clear context between phases.** One developer clears the conversation context between briefing, specification, and delivery stages, treating each as a fresh session with a structured handoff document. When briefs grow too large, the delivery agent needs to compact mid-run, which introduces risk.

**Sub-agents with isolated context windows.** Rather than letting one monolithic session accumulate everything, experienced users spawn sub-agents for specific tasks. Each sub-agent gets its own clean context, does its work, and reports back. This mirrors the cave-diving analogy one commenter offers: lightweight "scout" agents (using cheaper, faster models) explore the codebase and establish paths, while the more capable "main diver" agents operate within pre-mapped territory at greater depth.

**Task tracking that survives compaction.** When context does get compacted (summarized to free up window space), a dedicated task manager or external state file ensures the system can re-orient. Without this, compaction creates its own form of amnesia.

**Persisting decisions, not just actions.** A subtle but critical point: the state layer needs to record what the agent **decided** and **why**, not just what files it changed. Without this, an agent recovering from a context reset has no way to reconstruct the reasoning behind prior choices and may silently reverse them.

## The cheaper alternative: better context files

Not every project needs a multi-agent pipeline. Multiple commenters argue, persuasively, that a well-written `CLAUDE.md` file (or equivalent project context document) with architecture decisions, stack choices, constraints, and coding conventions can solve much of the context anxiety problem on its own.

The logic is straightforward: if the model can read a comprehensive, current description of the project's structure and rules at the start of every session, it has less reason to drift. The model does not need to infer what framework you are using or guess at your naming conventions; it reads them from a single source of truth.

Some developers automate the generation of these context files from the codebase itself, keeping them synchronized as the project evolves. The claim, which appears credible based on the reported experiences, is that **solid context files plus structured prompts get you roughly 80% of the harness benefit at essentially zero marginal cost**. The remaining 20%, which is where multi-agent review catches genuine logic errors and architectural mistakes, is where the heavier infrastructure earns its keep.

A related practice is separating behavioral instructions (`CLAUDE.md`, which loads automatically) from architectural documentation (`architecture.md`, which agents read on demand). This keeps the always-loaded context lean and focused on how to behave, while detailed structural knowledge remains accessible without bloating every interaction.

## The economics nobody can ignore

The elephant in every comment thread about multi-agent systems is cost. Running three to five agents per task, each consuming context and generating output, multiplies token usage by a corresponding factor. On subscription plans with usage caps, this is not an abstract concern; it directly limits how much work you can do in a day.

The cynical read, articulated vividly by the thread's most-upvoted comment (201 points), is that the vendor telling you to use more of their product to fix problems with their product has an obvious conflict of interest. The "shovel-peddler selling tinier shovels" framing resonated widely.

The pragmatic read is that the technique works and the question is whether the quality improvement justifies the cost for your specific situation. Prototyping and exploration may not need harnesses. Production migrations, security-sensitive codebases, and long-running autonomous builds may not be able to afford skipping them. Several developers on the highest-tier subscription plans report running multi-agent review pipelines all day without hitting limits, while others on lower tiers describe constant anxiety about running out.

## When to harness and when to hold back

The emerging consensus, stripped of both hype and cynicism, suggests a practical decision framework:

**Start with context files and task scoping.** Write a thorough project context document. Define tasks with explicit acceptance criteria and boundaries. Use a single agent with structured prompts. This handles the majority of day-to-day coding work.

**Add a separate evaluator** when you notice the model approving its own flawed output, when tasks are complex enough that "does it run" is not a sufficient quality bar, or when you are building something that will be difficult to manually review after the fact.

**Add a planner** when the work involves multiple interdependent tasks that need sequencing, parallelization decisions, or phased delivery.

**Add specialized reviewers** (security, performance, regression, compliance) when the stakes of the project demand it and the budget supports it.

**Scale back** as models improve. Anthropic's own post suggests removing harness elements that become unnecessary with more capable models. Treat the structure as scaffolding, not as permanent architecture. The goal is reliable output, not maximal process.

## The deeper shift

Underneath the debates about naming and pricing lies a genuine conceptual transition in how people relate to AI coding tools. The single-prompt, single-response model that defined the first wave of LLM coding is giving way to something that looks more like **managing a small, opinionated team**. You define roles, set standards, establish review processes, and accept that the cost of quality includes the cost of disagreement and iteration.

Whether you call it a harness, a pipeline, a workflow, or an autonomous execution engine, the underlying insight is the same: a model that generates code and then checks its own work is performing theater. A model that generates code while a structurally independent process evaluates it against criteria the generator never sees is performing engineering. The gap between those two things is where the bugs live.
