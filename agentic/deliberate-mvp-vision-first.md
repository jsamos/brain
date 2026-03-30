# The Deliberate MVP: How to Dream Big with AI and Still Ship Smart

**Sources**

- [r/ClaudeAI — claude has no idea what you're capable of](https://www.reddit.com/r/ClaudeAI/comments/1ryeh0y/claude_has_no_idea_what_youre_capable_of/)
- [r/ClaudeAI — you are claude's missing link](https://www.reddit.com/r/ClaudeAI/comments/1s67p67/you_are_claudes_missing_link/) (acceptance criteria follow-up)

---

There is a particular kind of waste that plagues AI-assisted development: not the waste of building too little, but the waste of building too little *on purpose*, without ever understanding what "too little" is relative to. When developers sit down with Claude Code and ask it to build something for a paying client or a commercial product, they tend to start constrained. Ship an MVP. Keep it simple. Iterate on friction. Sound advice on its own—until you realize that the MVP they shipped was a guess, not a decision.

A recent thread on r/ClaudeAI, titled "claude has no idea what you're capable of," went semi-viral (680+ upvotes, 130+ comments) around a deceptively simple idea: before you plan, before you write a line of code, ask Claude to describe the unconstrained ideal. "If time and labor were not a consideration, what would the optimal version of X look like? Don't plan, just describe." The author, a non-coder from TV and film who works with a team called MontGoWork, frames this as the philosophy for passion projects—dreaming with no ceiling. But buried in the same post is the sentence that matters most for anyone shipping software for money:

> "for money projects i still go simplest mvp and iterate on friction. but even for those the exercise is worth doing once because your mvp stops being a guess and becomes a deliberate subset of something you've already thought through."

That distinction—*guess* versus *deliberate subset*—is where the real value lives.

## The Problem with Starting Small

When you open a new Claude Code session and describe a product, the model makes quiet assumptions about you. It assumes you are resource-constrained, probably working alone, probably short on time, and probably not interested in architectural complexity you will not use in version one. Those are reasonable defaults. They are also a trap.

Multiple commenters in the thread confirmed the pattern. One noted that Claude "always defaults to the most boring, safe implementation possible—it's like it's trying to save me money or time I didn't ask it to save." Another observed that when Claude presents options, it tends to recommend the quickest path to something working: "'recommended' means 'easiest path forward' in AI speak," the original poster replied. A third described spending years incrementally building an internal infrastructure reporting tool, then watching Claude Code nail the full architecture in two minutes of plan mode once it was asked to describe the optimal version without constraints. Fifteen years of organic growth, replicated in a single prompt—because nobody had ever asked the tool to think past next quarter.

The issue is not that shipping an MVP is wrong. The issue is that most MVPs are carved from fog. You know what the first version should do, roughly. You have a sense of what users need. But you do not have a clear picture of the product's full potential, which means every cut you make—every feature you defer, every shortcut you accept—is made without knowing what you are cutting *toward*. You are not simplifying a vision. You are simplifying a hunch.

## The Exercise: Vision First, Then Scope Down

The proposed workflow is short enough to fit in a paragraph. Before touching any plan or implementation, prompt Claude to describe the optimal version of the product with no resource constraints. Then iterate. Push back. Challenge the description. Ask for more depth, more ambition, more specificity. Keep going until the model can describe *your* ideal back to you without correction—what the OP calls "locking the vision."

That last part is critical and was reinforced in the thread's most substantive exchange. The OP added in a follow-up comment: "the iteration step is the whole game. the prompt gets you started but the real work is pushing back until claude can describe your ideal back to you without correction. when you stop correcting, the vision is locked. that's when you know you're working from the same mental model instead of trusting the black box."

Only after that alignment is achieved do you start making scope decisions. And now those decisions look completely different. Instead of asking "what should version one do?", you are asking "given this fully articulated product, what is the smallest slice that delivers value while preserving the path to everything else?" The MVP becomes a conscious extraction from a known whole, not a bottom-up assemblage of features that seemed important at the time.

One commenter described pairing this vision phase with structured specs: "removing those constraints early helps you see what's actually possible, then you can cut it down to a real MVP." Another described a multi-phase workflow—vision in chat, then a `PLAN.md`, then phased implementation prompts scoped to context windows—where the plan gets nuked once the MVP ships and is replaced by clean architecture documentation. The vision lives long enough to inform the cuts, then the cuts inform the code.

## Why This Saves Money, Not Just Time

There is a pragmatic argument here that goes beyond ambition. When you define the full product before scoping the MVP, you get several things for free.

First, you get an architectural spine that accounts for the future. An MVP carved from a vision inherits structural decisions—data models, service boundaries, API shapes—that anticipate what comes next. An MVP built from scratch often paints itself into corners that cost real money to refactor when version two arrives.

Second, you get better time estimates. The thread surfaced a striking pattern around Claude's broken sense of duration. One user reported that Claude presented three implementation options with timelines of one, three, and five months. When challenged, Claude admitted the first option would take about 18 hours with the user's setup—but it had defaulted to human-developer-speed estimates. Another team wired a calibration loop into their pipeline and found tasks completing at 5% or less of Claude's estimated effort. A third user described a go-live plan estimated at five days that was completed in three hours.

If you run the vision exercise to its logical extreme—the OP notes that "the end is always 'an agent builds and operates X autonomously'"—you get a ceiling. And once you have the ceiling, you can locate yourself on the map between where you are and where the product could theoretically go. That orientation turns time estimation from guesswork into triangulation. For paid work, where scoping errors translate directly into budget overruns or undercharging, that orientation is worth real money.

Third, you get a communication artifact. The locked vision is not just a planning tool; it is a client-facing document waiting to happen. When a stakeholder asks "why didn't you build X in version one?", the answer is no longer "we didn't think of it." It is "we scoped it for version three, here's the roadmap, here's why the current architecture supports it." The deliberate MVP carries its own justification.

## The Discipline of Cutting

None of this works without the willingness to cut aggressively once the vision is locked. The OP is explicit about this: passion projects get the full dream treatment, but money projects still ship the simplest MVP and iterate on friction. The vision exercise does not change the shipping philosophy. It changes the *quality* of the shipping decisions.

One commenter pushed back on the upfront cost: "the exercise costs time upfront and for money projects some people will skip it. Worth building it into a repeatable template so the activation energy is basically zero." That is a fair point. The exercise is not free—it burns tokens, it burns thinking time, it requires several rounds of back-and-forth before the vision stabilizes. But the OP's follow-up post (which became its own viral thread) makes the counter-argument: planning is cheap, debugging is expensive. The tokens spent on vision are a fraction of the tokens wasted when Claude rebuilds the same feature three times because nobody defined what "done" looks like.

For paid work specifically, the calculus tilts even further. A client-facing product that ships with a clear path forward—where every deferral was a conscious choice, where the architecture already accommodates the next three phases—is worth more than one that shipped fast but will need to be substantially reworked to grow. The deliberate MVP is not slower. It is more honest about what it is and what it is not.

## The Compound Effect

The thread's most technically interesting contribution came from a team that tracked estimated versus actual effort across sprints and found a compounding pattern: "tools built in sprint N accelerate sprint N+1." One reply distilled it: "the system isn't just doing work, it's building infrastructure that makes the next round of work cheaper. That's where the compounding happens."

This is the payoff of the deliberate MVP at scale. When your first version is a conscious subset of a known whole, the infrastructure you build in version one is not throwaway scaffolding—it is the foundation for version two. The vision exercise does not just improve the first ship. It improves the rate at which every subsequent ship gets cheaper and faster. For teams billing by the project or operating on fixed budgets, that compounding is the difference between margins that shrink and margins that grow.

The romantic version of this story is about dreaming big and removing ceilings. The practical version—the one that matters for paid work—is about knowing exactly what you are building, choosing exactly how much of it to build first, and making sure every line of code you ship is a step toward the rest of it. The MVP is still small. It is just no longer a guess.
