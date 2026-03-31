# When AI Can Code, Clarity Becomes the Scarce Resource

**Sources**

- [r/ClaudeAI — Unpopular opinion: problem clarity is more valuable than coding right now](https://www.reddit.com/r/ClaudeAI/comments/1s7g1w9/unpopular_opinion_problem_clarity_is_more/)

**Parent:** [agentic/INDEX.md](INDEX.md)

---

You can hand an LLM a half-formed idea and it will still give you something that looks complete: functions, files, tests, even a confident explanation of why it chose that approach. The uncomfortable truth is that this "completeness" can be an illusion. When the underlying problem is fuzzy, the model can't read your mind—it can only produce a polished version of whatever ambiguity you gave it.

That's why, in practice, problem clarity often matters more than raw code-writing speed.

## The "polished confusion" failure mode

Modern models are excellent at generating coherent artifacts. If you ask for "a feature" without specifying constraints, edge cases, non-goals, or what success looks like, the model will fill gaps with defaults and plausible assumptions. The output may compile. It may even look elegant. But it can still be fundamentally misaligned with what you needed—because the target was never pinned down.

This isn't a moral failure of the model. It's a predictable outcome of an underspecified request.

## This problem predates AI

Unclear goals have always created churn. Teams build the wrong thing quickly, then spend cycles reworking it, debating intent, and patching around mismatched expectations. AI doesn't invent that dynamic—it accelerates it. If ambiguity used to cost days, now it can cost hours but happen more often, because generating the first draft is cheap.

## AI can help you get clear—if you use it that way

A key nuance: LLMs aren't only code printers; they can be clarification engines. If you prompt for the right kind of thinking—questions, assumptions, alternatives, risks—they can help turn a fuzzy idea into something actionable.

The model can assist with clarity, but it won't automatically do it. If you ask for code, you'll get code. If you ask it to interrogate the problem, you'll get a better problem statement.

## The real-world source of fuzziness: people

The oldest challenge in product work persists: stakeholders and users often don't fully know what they want. They describe outcomes in vague terms, contradict themselves, or change priorities midstream. Engineers end up balancing speed and accuracy under shifting constraints.

AI doesn't remove that responsibility. It can, however, make the trade-offs more visible—by forcing you to choose what to specify, what to defer, and what to validate.

## Why code literacy still matters

Even if AI writes the code, someone has to judge it. Knowing how to read, debug, and reason about logic remains vital—like being able to read the map when the tool is doing the driving. When clarity is missing, you need that literacy even more, because you're validating not just correctness but intent: does this implementation match the actual goal?

## The skill shift: from typing to communicating intent

The practical takeaway is straightforward: the differentiator becomes your ability to communicate what you want—product thinking, design sense, constraints, acceptance criteria, and trade-offs. In an AI-assisted workflow, "good prompting" isn't about clever incantations; it's about making intent explicit and testable.

When generation is cheap, precision is valuable. The better you are at turning a vague desire into a crisp spec, the more the model's speed helps rather than harms.

## Putting it into practice

None of this has to stay abstract. A simple workflow can make clarity the default rather than something you remember after the first bad draft.

**1. Start with the problem, not the solution.** Before writing a prompt that asks for code, spend a few minutes stating what you're trying to achieve in plain language: the goal, the constraints, who it's for, and what "done" looks like. If you can't write two sentences about it, the model can't build it well either.

**2. Let the model interview you.** Ask it to list the assumptions it would make, surface questions it needs answered, and propose two or three interpretations of your request with their trade-offs. Pick one. Now you have a shared understanding before a single line of code exists.

**3. Write acceptance criteria before implementation.** Have the model draft what success looks like—edge cases, expected behavior, failure modes—then use those as the spec it codes against. This flips the usual order: tests and criteria first, generation second.

**4. Review for intent, not just correctness.** When the code comes back, don't just check whether it runs. Check whether it matches the goal you defined in step one. If you find yourself unsure, that's a sign the goal was still fuzzy—loop back and tighten it.

**5. Treat each cycle as a tightening loop.** Clarify → generate → validate → refine the spec → generate again. Each pass sharpens the problem and the output. The model gets faster at generating; you get faster at specifying. Over time, you spend less effort on rework and more on the parts only a human can decide.

The workflow is deliberately lightweight—no new tools, no framework, just a habit of putting clarity before speed. In practice, it turns AI from a fast but unreliable typist into something closer to a capable collaborator: one that moves quickly in the direction you actually pointed it.
