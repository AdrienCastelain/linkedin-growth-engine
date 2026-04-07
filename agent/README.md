# Content Agent Template

The LinkedIn Growth Engine works on its own — load the skill, fill in a brand profile, run the workflow. But if you're using Claude Code (or any agent framework) and you want to spin up a dedicated content agent that does the same thing every week without needing to be re-prompted, this folder is for you.

## What's in here

- **`content-agent-template.md`** — A reusable agent definition with `[FILL IN: ...]` markers for everything you need to customize. Copy it, fill it in, point your agent runner at it.
- **`examples/example-content-agent.md`** — A fully filled-in example using a fictional fractional CMO named Alex Hayes and an agent named Sage. Use it as a reference for what a finished template looks like.

## Skill vs. agent — what's the difference?

The **skill** is the rulebook, modules, and workflow. It's the *content system*. You can use it interactively without ever creating an agent — just load the skill in your Claude Code session and follow the steps.

The **agent** is a persistent identity with its own memory, voice protocol, decision boundaries, and quality bar. It loads the skill every time, applies it consistently, and gets better at your specific brand over time.

## Should I bother creating an agent? (the decision question)

**Skip the agent** if any of these are true:
- You're trying the workflow for the first time and want to see if it produces good output
- You're running this once a month or less
- You don't use Claude Code (the agent template is markdown — it'll work anywhere — but the runtime conventions assume Claude Code)

**Build the agent** if any of these are true:
- You're committing to weekly batches for 3+ months
- You want the same agent identity to run the workflow every week without re-explaining your brand
- You're in Claude Code and you want to address the agent by name via the Agent tool

The honest answer for most users: **start without an agent, ship 2-3 weekly batches, then build the agent once you're sure the system works for you.** The agent is a productivity layer on top of the skill, not a prerequisite.

## How to create your own content agent in 3 steps

### Step 1 — Copy the template

```
cp content-agent-template.md ../my-content-agent.md
```

(Or wherever your agent definitions live. In Claude Code that's typically `.claude/agents/` or `~/.claude/agents/`.)

### Step 2 — Fill in the markers

Open the file and replace every `[FILL IN: ...]` block with your own answer. The markers are sorted from most to least important:

1. **North Star** — what does this agent exist to grow?
2. **Identity** — name, who it reports to, who it works with
3. **Voice Protocol** — which brand profile it loads (this is the most important block — get this right or the agent will drift)
4. **Decision Authority** — what it can do without asking, what it must escalate
5. **Quality Bar metrics** — how you'll know it's working

The `examples/example-content-agent.md` file shows a complete filled-in version if you want to see what "done" looks like.

### Step 3 — Wire it to the skill

In your agent's startup or system prompt, make sure it loads:

1. The LinkedIn Growth Engine skill (`../SKILL.md` from this folder, or wherever you installed it)
2. Your brand profile
3. The cultural profile from `modules/19-cultural-profiles.md` if your audience is non-US

Then test it: ask it to draft a single LinkedIn post and see whether the voice matches your brand profile and whether it passes the quality gates. If it doesn't, tighten the brand profile (most voice drift is profile-precision drift, not agent drift).

## Do I need an agent framework?

No. The template is just markdown. It's structured so any of these will work:

- **Claude Code** — drop it in `.claude/agents/` and address it via the Agent tool
- **Cursor / other IDE agents** — paste it as a system prompt
- **Custom scripts using the Anthropic SDK** — load it as the system message
- **No tooling at all** — keep it as a reference doc and paste the relevant blocks into chat manually

The point of the template isn't the format. It's the discipline: voice locked, rules loaded, decisions bounded, quality measured. Whatever runtime you use, that's the goal.
