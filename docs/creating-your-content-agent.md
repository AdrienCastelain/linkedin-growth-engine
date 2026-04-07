# Creating Your Content Agent

> **What this is:** A step-by-step guide to wrapping the LinkedIn Growth Engine skill in a persistent agent identity. The agent template at [`agent/content-agent-template.md`](../agent/content-agent-template.md) is the file you'll customize. This doc explains why, when, and how.
>
> **The short version:** You don't need an agent. The skill works without one. Build the agent if you're committing to weekly batches for 3+ months and you want a persistent identity that loads everything correctly every time without you re-explaining your brand.

---

## When to build an agent (and when not to)

### Skip the agent if:

- You're trying the workflow for the first time and want to see if it produces good output
- You're running batches once a month or less
- You don't use Claude Code (the template is plain markdown — it works anywhere — but the runtime conventions assume Claude Code)
- You're still figuring out your brand profile and your voice samples are likely to change every week
- You're evaluating multiple content systems and haven't decided which one you'll commit to

### Build the agent if:

- You're committing to weekly batches for the next 3+ months
- You're tired of re-loading the rulebook, brand profile, and workflow every time you run the system
- You're in Claude Code and you want to address the agent by name via the Agent tool
- You want consistent voice protocol enforcement across every single batch
- You're managing content for multiple brands and want a separate agent identity per brand (one Sage for Brand A, one Atlas for Brand B)

**The honest answer for most users:** Start without an agent. Ship 2-3 weekly batches with the skill alone. Once you're sure the system works for you, take 30 minutes to build the agent.

---

## What an agent is (and isn't)

**An agent is a persistent identity** that loads the same context every time it runs:
- The LinkedIn Growth Engine skill (rulebook, modules, workflow)
- Your brand profile (voice samples, pillars, story bank)
- Decision authority boundaries (what it can do without asking, what it must escalate)
- A response format (signals which agent is speaking)
- A quality bar (the standards every output must meet)

**An agent is NOT:**
- A separate AI model. It uses whatever model you're already running (Claude Sonnet, Claude Opus, GPT-4, etc.).
- A scheduled job. It only runs when you invoke it. There's no cron, no autonomous execution.
- A different runtime. It's a markdown file your existing AI loads as context.
- Magic. The agent's quality is exactly the quality of the skill + brand profile + your prompts. The agent is just structured glue.

---

## The 3-step setup

### Step 1 — Copy the template

```bash
cp agent/content-agent-template.md my-content-agent.md
```

(Or wherever your agent definitions live. In Claude Code that's typically `.claude/agents/` or `~/.claude/agents/`. In other runtimes, anywhere accessible to your AI session.)

### Step 2 — Fill in the markers

Open `my-content-agent.md`. Replace every `[FILL IN: ...]` block with your own answer.

The markers are sorted from most to least important:

1. **North Star** (1 sentence) — what does this agent exist to grow?
2. **Identity** — name, who it reports to, who it works with
3. **Voice Protocol** — which brand profile file it loads (this is the most important block — get this right or the agent will drift)
4. **Decision Authority** — what it can do without asking, what it must escalate
5. **Quality Bar metrics** — how you'll know it's working

The example at [`agent/examples/example-content-agent.md`](../agent/examples/example-content-agent.md) shows what a fully filled-in version looks like (a fictional agent named "Sage" working for the fictional fractional CMO "Alex Hayes").

### Step 3 — Wire it to the skill

In your agent's startup or system prompt, make sure it loads:

1. The LinkedIn Growth Engine skill (`SKILL.md` at the project root, or wherever you installed it)
2. Your brand profile (`_user/my-brand-profile.md`)
3. Module 19 (Cultural Profiles) if your audience is non-US
4. The workflow (`CONTENT-GENERATION-WORKFLOW.md`)

In Claude Code, this happens automatically once you've registered the skill. In other runtimes, you may need to paste these as context at the start of every agent invocation.

---

## How to address the agent

Once the agent file exists and the skill is loaded, you can invoke the agent like this:

### In Claude Code

```
Use the [agent name] agent to run a content batch this week.
```

The Agent tool will spawn a session that loads your agent file and the skill, then executes whatever you asked for.

### In single chat (Claude.ai, ChatGPT)

```
You are [agent name], the content agent defined in the file below. Load your agent definition, then load the brand profile and run the LinkedIn Growth Engine workflow in [First-Run / Returning] Mode.

Agent definition:
[paste my-content-agent.md]

Brand profile:
[paste _user/my-brand-profile.md]

Skill:
[paste SKILL.md and the workflow file]
```

This is verbose but works in any chat-based runtime.

### In Cursor or other IDE agents

Same as single chat, but use the chat panel and reference file paths if your IDE supports it.

---

## What the agent file looks like

The template has these sections (filled-in example: [`agent/examples/example-content-agent.md`](../agent/examples/example-content-agent.md)):

### North Star

One sentence describing what the agent exists to grow. **Make it about outcomes, not tasks.**

- ❌ "I write LinkedIn posts" (task)
- ✅ "I grow [your brand] by turning strategy into LinkedIn content that holds dwell time and matches your voice." (outcome)

### Philosophy

Five-bullet commitment statement. The default in the template is:

> Committed expert: deliver results, give honest expertise, take ownership, bring proactive value, see things through.

You can rewrite this to match your own values, but most people use the default.

### Response Format

How the agent prefixes its responses. The template suggests:

> **[Agent Name] | Content Creator | [Current Project]:**

This signals which agent is speaking and what it's working on. Useful when you have multiple agents in the same conversation.

### Identity

Name, role, who it reports to, who it coordinates with. For solo operators, "reports to" is usually just you. "Coordinates with" can be left blank.

### Voice Protocol (mandatory)

The most important section. The agent loads the brand profile *first*, then the rulebook, then the workflow. The voice protocol enforces this order so the agent never generates content without the brand voice in context.

The template has this baked in:

> Before writing ANY content, this agent identifies the brand voice:
> 1. Load the brand profile — write as that brand, not as the agent itself
> 2. Load the LinkedIn Growth Engine Rulebook
> 3. If no brand profile exists, STOP and flag it

You list the brand profile path in the "Active brand profile" table.

### Skills Bundle

What skills the agent loads. At minimum: the LinkedIn Growth Engine rulebook and the workflow. You can add other skills (e.g., a research skill, a copywriting skill, a brand-specific style guide).

### Decision Authority

The CAN / CANNOT / ESCALATE structure. This is where you decide what the agent is allowed to do without asking you:

- **CAN** (autonomous): Run weekly batches, draft posts, run quality checks, monitor engagement
- **CANNOT** (must ask first): Change content strategy, launch campaigns without sign-off, publish anything that deviates from brand voice
- **ESCALATE** (immediate flag): Negative brand mentions, PR-level issues, engagement dropping >20%

This section is the difference between an agent you trust to ship batches autonomously and an agent that confirms every decision with you. Most users start cautious and loosen the boundaries after Batch 4-6.

### Quality Bar

The standards every output must meet. The template defaults:

- Pass all 12 per-post quality checks from the workflow's Step 5
- Match the brand voice on the documented voice profile
- Be specific enough that a colleague would recognize the brand wrote it
- Connect to one of the brand's declared content pillars

Plus the metrics you track (engagement rate, follower growth, response time, calendar adherence). Set these to match your goals.

### Session Lifecycle (optional)

If you're using a memory or session-tracking system with your agent, run something like this at the start and end of every session:

- **On start:** Load any session/memory tools, recall past learnings, load brand profile + skill
- **On end:** Capture anything you learned (failures, wins, voice corrections), close the session

If you don't have a memory layer, skip this section. The skill works without one.

### Model Routing

Default model for the agent (typically the fastest one that still produces good content), with an upgrade rule for harder tasks:

- **Default:** Claude Sonnet 4.6 (fast, voice-accurate)
- **Upgrade to:** Claude Opus 4.6 for monthly performance reviews, newsletter drafts, or high-stakes launches
- **Downgrade:** Usually N/A — content benefits from a strong base model

---

## How to test your agent before relying on it

### Test 1 — Voice match

Ask the agent to draft a single post on a topic from your pillars. Compare the post to your reference voice samples. Does it sound like the same person?

If yes: voice protocol is working.
If no: your brand profile needs more or better samples. Re-fill §5c and re-test.

### Test 2 — Decision authority

Ask the agent to do something that should trigger a CANNOT or ESCALATE rule. (E.g., "publish this post immediately without my review.")

If the agent refuses and explains which rule it's hitting: authority is wired correctly.
If the agent complies: rewrite your CAN/CANNOT/ESCALATE section to be more explicit, or add specific language to the system prompt.

### Test 3 — Quality bar

Ask the agent to produce a post that obviously violates the rulebook (e.g., one with a Tier 1 banned word). Check that the agent's Step 5 quality check catches it before delivery.

If yes: quality bar is enforced.
If no: the agent isn't loading the rulebook correctly. Pass it explicitly in the system prompt.

---

## Multi-brand setup

If you're managing content for multiple brands, create one agent file per brand. Don't try to use one agent for two brands — voice drift is guaranteed.

```
agents/
  sage-for-alex.md          ← agent for Brand A
  atlas-for-quinn.md        ← agent for Brand B
  rowan-for-internal.md     ← agent for your own brand
```

Each agent file points to a different brand profile. Each agent has a different identity and voice protocol. They don't share state.

---

## Common mistakes

1. **Building the agent before you've shipped a batch with the skill alone.** You don't yet know what your brand profile needs. Ship 2-3 batches first, refine the profile, then build the agent.
2. **Filling in the agent template but skipping the brand profile path.** The agent has nothing to load. It defaults to generic AI voice. The whole point of the agent is to enforce the brand profile load — that one field is mandatory.
3. **Setting CAN to "publish without review" before you trust the system.** Don't grant autonomous publishing authority until you've seen 4+ batches go through clean. The wrong post on autopilot is much worse than the right post on a 5-minute review delay.
4. **Multiple agents reading from the same brand profile.** This is fine if they're coordinating (e.g., one drafts, one reviews) but if they're meant to be independent, give each its own profile.
5. **Forgetting to update the agent when the brand profile changes.** The agent file references the brand profile by path. If you rename the profile, update the agent.

---

## What changes when you have an agent

**Without the agent (skill alone):**
- Every session starts with "load the rulebook, load my brand profile, load the workflow"
- You re-explain the agent's role and constraints in each new conversation
- Quality bar is enforced via the workflow's own quality gates

**With the agent:**
- You invoke the agent by name and it loads everything
- Decision authority is documented and consistent
- You stop thinking about "did I load everything?" and start thinking about the content
- The agent file becomes the version-controlled record of how this brand's content gets made

The savings per session is small (~2-3 minutes). The savings over a quarter (12-13 batches) is meaningful (30-40 minutes plus less context-switching cost). Build the agent if the math makes sense for your cadence.
