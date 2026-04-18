# El Clásico — Ronaldo vs LLMs

What if we had an El Clásico with Ronaldo on one side and LLMs on the other? It would be interesting to see who wins.

---

If you've spent any time building with LLMs over the past year, you've probably had this argument with yourself, a teammate, or a Slack thread at 2 AM:

> "Should I just use the biggest, most expensive model? Or should I wire up a smaller, cheaper model into an agent framework?"

Or, if you're a beginner like me, you've probably wondered:

> "What even *are* these agentic AI frameworks, and how are they linked to LLMs?"

The honest answer to both questions is *it depends* — but that's a useless answer. So let me give you a better one, using the only analogy that reliably wins arguments anywhere in the world: **football**, and **Ronaldo**.

## The Setup

Imagine two footballers.

On one side, you have **Cristiano Ronaldo**. Five Ballon d'Ors. Decades of top-flight experience. The kind of player who can change a match in six seconds. Ronaldo is your **frontier LLM** — think Claude Opus, or Gemini Pro. Enormous capability packed into a single "forward pass" of intuition, vision, and execution. Expensive. Slower. But elite.

On the other side, you have a **promising U19 national-level player**. Talented, coachable, sharp — but nowhere near Ronaldo's level individually. This player is your **smaller, cheaper LLM** — a Claude Sonnet, or a Gemini Flash. Good. Fast. Affordable. Not great.

Now here's the interesting question: **what happens when you put 11 of these U19 players on a pitch against a solo Ronaldo?**

That's the agent question in disguise.

A football team of 11 — goalkeeper, defenders, midfielders, attackers — with coordinated positions, set plays, and a game plan, is structurally identical to an **agentic framework**. Each player is a specialist node. The team has planning (the coach), memory (match history, scouting reports), tools (set pieces, formations), and communication protocols (shouts, hand signals, positional awareness).

One Ronaldo alone is a single LLM call. A full team is a multi-agent system.

With that lens, let's walk through the cases — starting with the one everyone already knows is true.

---

## Case 0 (The Base Case): One-on-One, Ronaldo Beats the U19 Player. Always.

Before we get clever, let's state the obvious.

Put Ronaldo one-on-one against a single U19 player — no teammates, no framework, same task, same rules — and Ronaldo wins every single time. Dribble past him. Beat him in the air. Outshoot him. Outthink him. There is no task on a football pitch where a lone U19 kid beats a lone Ronaldo.

Same thing in LLM land. For any given prompt, given no framework around either model, **Opus will beat Sonnet. Gemini Pro will beat Gemini Flash.** The bigger model is more capable — that's literally why you pay more for it. Reasoning is sharper, edge cases are handled better, nuance survives.

> **The base case:** more capable model beats less capable model, head-to-head. Always. This isn't interesting — but it's the baseline you have to beat for any of the following cases to matter.

So why would anyone *ever* reach for a smaller model? Because in the real world, you almost never hold everything else constant. Budget matters. Latency matters. Parallelism matters. And the *shape of the task* matters most of all.

Let's see where that takes us.

---

## Case 1: A Full 90-Minute Match → Team of U19 Players Beats Solo Ronaldo

Put Ronaldo alone on a pitch against 11 coordinated U19 players and ask him to win a full match. He loses. Every time.

Not because he isn't brilliant — he is — but because football over 90 minutes is a **coordination problem**. Somebody has to defend the goal. Somebody has to build play from the back. Somebody has to be in the box when the cross comes in. Ronaldo, for all his talent, cannot be in two places at once, cannot mark three attackers, cannot take a goal kick and finish it.

This is exactly what happens with **long, multi-step, tool-using tasks** in the LLM world.

Give Opus a prompt like *"research the top 10 competitors for my startup, pull their pricing from each site, summarize their positioning into a Notion doc, and draft an outreach email to each of their unhappy customers on Reddit"* — and even the best frontier model will stumble as a single call. Not because it lacks intelligence, but because the task requires browsing, scraping, parsing, writing, critiquing, retrying, and memory across dozens of steps.

Meanwhile, an agent framework built on Sonnet (or Gemini Flash) can crush this. The framework itself provides the structure: a planner decomposes the task, a researcher agent browses, a writer agent drafts, a critic agent reviews, a memory system tracks what's been done. No single step needs Ronaldo-level brilliance. Every step needs *reliability* and *coordination* — plus the ability to run many of them cheaply and in parallel.

> **The takeaway:** for long-horizon, multi-step, tool-heavy tasks, a well-designed agent framework running on a smaller model will routinely beat a single call to a frontier model.

---

## Case 2: A Penalty Shootout → Ronaldo Beats the Team's Best Kicker

Now flip it. Same two sides, but change the match to a penalty shootout. Ronaldo steps up alone. The team of 11 sends up their designated penalty taker — the best kicker they have. One shot each.

Here's the thing: the team still has 10 other players. It still has a coach, a plan, a formation. But none of that matters when it's just one player on the spot. The framework goes quiet. The coordination evaporates. It's suddenly one kicker against one keeper, and the only thing that counts is how good that one player actually is.

Ronaldo scores. The team's kicker doesn't. All the structure that won the 90-minute match is useless here, because this task has nothing to coordinate on.

This is the **single-shot, high-skill task** in LLM terms.

- "Write a legally precise contract clause."
- "Translate this poem while preserving meter."
- "Debug this tricky SQL query involving three window functions."
- "Summarize this dense 40-page research paper."

For these, an agent framework of cheaper models is overkill *and worse*. You don't need planning. You don't need tool use. You don't need five Sonnet agents arguing with each other. At the moment of decision, only one agent's output actually matters — and it's a Sonnet-level output, not an Opus-level one. The framework didn't help; it just added latency and cost.

Calling an agent framework for a task like this is like telling your U19 team to hold a tactical meeting before the penalty. By the time they've finished the meeting, Ronaldo has already tucked his into the top corner.

> **The takeaway:** for narrow, single-shot, high-skill tasks, just call the biggest model you can afford. A framework can't help you in the moment where only raw capability matters.

---

## Case 3: The Long Throw-In Specialist → A Role Ronaldo Simply Doesn't Play

Here's where it gets interesting. Think about Rory Delap at Stoke City — not a world-class footballer overall, not even close to Ronaldo's level. But his **long throw-ins** were so devastating they terrorized elite Premier League defenses for years. Arsenal, Chelsea, Liverpool — all of them had to hold special training sessions just to deal with one guy's throw-ins.

Now imagine Ronaldo lining up against that same task. Ronaldo is the greatest generalist attacker of a generation. But he doesn't train long throws. It's not his role. Put him against Delap in a long-throw contest and a "much less skilled" player wins — *because the task is narrow and the specialist has spent 10,000 hours on exactly this one thing*.

You see the same thing with goalkeepers. Any average professional keeper will stop more shots than Ronaldo would in goal, because the role requires a completely different skill set than the one Ronaldo has mastered.

Translate this to LLMs: for **repeated, narrow tasks where you can fine-tune or specialize**, a smaller model often matches — and sometimes beats — a frontier model. A Sonnet fine-tuned on medical record summarization will frequently match or outperform a cold Opus call on that exact task, at a fraction of the cost and latency. A Gemini Flash tuned on your specific classification schema can beat a raw Gemini Pro on that schema, every single time.

The frontier model is a brilliant generalist. But generalists, by definition, haven't spent 10,000 hours on *your* specific task. A focused smaller model has.

> **The takeaway:** specialization matches or beats raw horsepower when the task is narrow and repetitive. Fine-tuned small models are the Rory Delaps of the LLM world — limited in range, devastating in their niche.

---

## Case 4: The Stadium Is on Fire → Edge Cases Break Everything

Picture this: the ball bursts mid-match. The floodlights cut out. A pigeon lands on the penalty spot. Then the referee runs onto the pitch shouting in a language no one on the team speaks.

Ronaldo, as an individual, improvises. He kicks the busted ball anyway, squints through the dark, walks around the pigeon. He's one player solving one problem with one brain. The team, meanwhile, is in meltdown. The defender is waiting for a pass signal that isn't coming. The midfielder is running a set piece for a ball that no longer exists. The striker is shouting for the lights. The goalkeeper is chasing the pigeon. *The coordination that made the team strong is now what's breaking it.*

This is the dirty secret of agent frameworks: **they are brittle at the seams**. The individual agents can be world-class, and the whole thing still collapses when the environment goes even slightly off-script.

In production this plays out in painfully specific ways:

- The tool you orchestrate against ships a minor schema change, and three downstream agents silently start receiving garbage
- An API you depend on starts rate-limiting you, and your planner agent keeps retrying in a loop while your critic agent congratulates it for trying
- A user writes their request in an unexpected format, and your router sends it to the wrong sub-agent, which confidently hallucinates an answer
- One step's output subtly drifts, and the next agent builds an entire plan on top of that drift before anyone notices

None of these are model failures. They're *system* failures — and every additional agent, tool, and hand-off is another seam where reality can sneak in and tear the thing apart.

A single Opus call, given the same weird situation in its context, often handles it more gracefully than a complex Sonnet-based agent. Not because Opus is smarter at that specific moment — but because there's no brittle plumbing to break. It can see the whole strange situation at once, reason about it end-to-end, and respond. One brain, one decision, one failure surface.

> **The takeaway:** every component in your agent system is a seam. Every seam is a place reality can rip it open. Complexity has a real tax, and you pay it the day something unexpected happens — which is every day in production.

---

## Case 5: A Team of Ronaldos vs a Team of U19 Players → Ronaldos Win. Don't Forget This.

Before we wrap up, one last scenario — and this one matters because it's the baseline that agent-framework evangelists sometimes forget.

Imagine a full match — 11 vs 11 — but one side has 11 Ronaldo clones and the other side has 11 U19 players. Same formation, same coach, same tactics, same pitch. Everything equal, except the players.

The team of Ronaldos wins. Not close.

Translated to LLMs: if you build **the exact same agent framework** — same planner, same tools, same memory, same critic loop — and you run one version on Opus and another on Sonnet, **the Opus version wins.** Agent frameworks don't magically equalize base model quality. A better player in every position makes a better team. That's just math.

This is important to internalize, because it's tempting to read the earlier cases and conclude that agent frameworks are some kind of cheat code for weaker models. They aren't. What agent frameworks let you do is make a *different tradeoff* — give up some raw capability per step in exchange for coordination, parallelism, tool use, and cost. That tradeoff is often worth it. But it is a tradeoff, not a free lunch.

Budget matters — you can't afford to run 11 Ronaldos on every request. Latency matters — a Ronaldo takes longer to make every decision. Parallelism matters — you can run 20 U19 players in the time it takes one Ronaldo to move. That's *why* teams of U19 players exist in production. Not because they're secretly better than Ronaldos. Because they're good enough, fast enough, and cheap enough — at scale.

> **The takeaway:** agent frameworks aren't a way to make weaker models better. They're a way to make *cheaper, faster, more parallelizable* models *good enough* for the right tasks. If cost and latency weren't a factor, you'd always pick the team of Ronaldos.

---

## Closing Remarks: What a Real-World Team Actually Looks Like

Here's the honest truth nobody says out loud: **you can't get 11 Ronaldos**. Nobody can. Not on a football pitch, not in an agent system. Budgets are finite. Latency is finite. You have to make peace with that.

So what does a *real* team look like — the kind you'd actually field in production?

Imagine a squad of 11. Most of the players are solid U19s — fast, cheap, reliable, good at their roles. They do the defending, the passing, the running, the tool-calling, the summarization, the routing. Nothing spectacular, but they never stop moving.

Then in the middle of the park, you've got a **Ronaldo as the captain** — your frontier model, called on for the ambiguous decisions, the creative leaps, the moments where raw capability actually matters. You don't play him every ball. You play him on the ones that count.

And somewhere on the flank, you've got your **Rory Delap** — the specialist. Not a superstar overall, but absolutely world-class at one specific thing. A Sonnet fine-tuned on your exact support ticket distribution. A small model specialized on your schema. When that specific situation comes up, you bring him on and everyone else gets out of his way.

*That's* a production agent system. A few Ronaldo-level calls at the decisive moments, a specialist or two for the narrow recurring tasks, and a team of cheap, reliable U19s doing the overwhelming majority of the work. Every role played by the right kind of player, at the right cost, for the right task.

You won't win every match with this team. But you'll win most of them — and you'll be able to afford to show up every week, which is the one thing a team of 11 Ronaldos could never do.

---

## So What Do You Actually Build?

Here's the decision tree I keep coming back to:

- **Is the task a single-shot, high-skill ask?** → Just call the biggest model. No framework.
- **Is the task long, multi-step, and tool-heavy?** → Build an agent framework. A smaller model is usually fine.
- **Is the task repeated and narrow?** → Specialize. Fine-tune a small model. It'll be your Rory Delap.
- **Is the environment unpredictable and messy?** → Lean toward fewer moving parts. Complexity breaks.

> **A note that balances all of the above:** in practice, you rarely need just one of these answers. Most real systems need all of them at once — which is why the hybrid lineup from the closing section exists. Go hybrid: a cheap model for the routine steps, a frontier model for the hard ones, and a fine-tuned specialist where it earns its keep. The bullets above tell you *which* player to pick; the hybrid tells you how to put them on the same team.

The mistake most teams make is treating "agent vs. big model" as a philosophical war instead of an engineering choice. It isn't one. Ronaldo is not better than a team. A team is not better than Ronaldo. They are better at *different matches*.

And remember the base case: holding everything else equal, Opus beats Sonnet and Gemini Pro beats Flash — always. The interesting question is never *which model is smarter*. The interesting question is **what match are you playing, and what lineup wins that match at a cost you can afford?**

Your job as a builder is to look at the match in front of you — the actual task, the latency budget, the failure modes, the cost envelope — and pick the lineup that wins *that* game.

And if you get it right, the scoreboard will tell you.

---

*If you enjoyed this, I write about applied ML, LLM systems, and building production AI at scale. Follow for more.*
