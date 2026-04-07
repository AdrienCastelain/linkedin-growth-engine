# LinkedIn Growth Engine

You know those LinkedIn posts that smell like ChatGPT in the first sentence? This is how you stop writing those.

A free, open-source content system with strong opinions about what AI-assisted LinkedIn content should and shouldn't sound like. Built for solo experts selling services on LinkedIn — fractional executives, consultants, indie founders, technical experts, and anyone who manages content for one or more brands and is tired of the AI tells.

---

## See the difference (90 seconds)

Most AI content tools generate posts like this:

> Three years ago I was a junior consultant who thought I knew how to price.
>
> I told a founder client to keep her pricing flat at her first renewal. "Don't risk the relationship," I said. "Customer loyalty is everything."
>
> She did. They renewed. I felt good.
>
> Six months later she lost two of those accounts to a competitor who repriced. The "loyalty" I'd protected was actually a discount they were exploiting.
>
> That was the day I learned: real loyalty pays full price.
>
> Now I never recommend flat renewals.
>
> What's the lesson you learned the hard way about pricing?

Looks fine, right? It isn't. It's a textbook AI pattern: naïve-past-self → tidy resolution → wise-present-self → poster-line moral → engagement-bait question. Once you see it you can't unsee it.

This system catches that pattern automatically and replaces it with something like this:

> A founder client wanted to raise her renewal prices 40% last spring. A competitor had just repriced and she wanted to follow.
>
> I talked her down to 15%.
>
> Six months later I sat with her enterprise CSM and went through the renewal data. Two of her three biggest accounts would have paid the 40% without blinking. The third was on the fence at 25%.
>
> The math: those two accounts were ~$350K ACV each. The 25-point delta between 15% and 40% was roughly $175K-$180K over the year. I'd cost her almost two hundred grand by being cautious on her behalf.
>
> Here's the part that still bothers me. I wasn't being conservative. I was anchoring. The competitor's pricing felt like data, so I treated it like data. It wasn't data. It was a single observation about one company's risk tolerance, dressed up as market intelligence.
>
> ...
>
> Maybe the worst pricing mistakes are the ones where the consultant thought she was being careful.

Same author, same pricing topic, completely different post. The second one makes the writer look *worse* at the end, not wiser. That's the whole point. **Tidy redemption arcs are the AI tell.**

The full before/after — including the rule that catches it, why it failed, and how the rewrite was generated — is in [`examples/anti-pattern-catches/README.md`](./examples/anti-pattern-catches/README.md), Catch 5. If you read one file in this whole project, read that one.

---

## What it is

A canonical rulebook (1,200+ lines of opinionated, defensible content rules), 19 modules, an executable weekly workflow, and an optional agent template — all designed to work as a Claude Code skill or as a standalone reference for any LLM workflow.

**Why it exists:** AI-written LinkedIn content is detectable. The detection costs you reach (LinkedIn's algorithm flags it) and credibility (your readers spot the patterns). This project documents the specific rules and workflows that make AI-assisted content actually pass for human — backed by 12 quality gates per post, an independent critic loop, and a batch variety audit.

---

## What we mean by "good" (read this before you decide if it's for you)

Every content tool optimizes for *something*. Most of them don't say what. This one does.

**A "good" LinkedIn post, by this project's standards, is:**

- **Voice-locked.** It sounds like the specific person who's posting it, not like a polished generic version of them. If your reference samples are casual, the output is casual. If your samples are precise, the output is precise.
- **Specific over general.** Real numbers, real names (when shareable), real timeframes, real situations. No "studies show," no "73% of companies," no invented client anecdotes.
- **Earned vulnerability over manufactured vulnerability.** Posts where the writer ends *worse* than they started (a real failure, a real cost, a real "still bothers me") outperform posts with tidy redemption arcs. The rulebook explicitly bans the naïve-past-self → wise-present-self pattern.
- **Dwell-time over reaction count.** A post that 200 people read fully and 5 save matters more than a post that 1,000 people scroll past and 50 react to. The system optimizes for the first.
- **Topical authority over 60-90 days.** LinkedIn rewards consistency. The system enforces pillar discipline so your account develops a recognizable topic identity, not a scattered feed.
- **Inbound DMs from your ICP** (if your goal is leads). The conversion gate is "would your ICP read this and self-identify with the situation?" If yes, the post is doing its job. Comments and likes are downstream signals.

**A "good" LinkedIn post, by this project's standards, is NOT:**

- **Viral.** Virality is a lottery. The system optimizes for *consistent* engagement from your *target* audience, not for one-off explosions in front of strangers.
- **Optimized for follower count.** Followers are a vanity metric. 600 followers in your ICP outperforms 60,000 random followers for every goal except "I'm an influencer who sells advertising."
- **The "thought leader" aesthetic.** Polished, perfectly-balanced paragraphs. Motivational poster lines as closings. "I quit my $400K job to follow my passion" arcs. The rulebook explicitly bans these patterns.
- **Engagement-bait optimized.** "Comment YES if you agree." "Tag a friend who needs this." "Agree or disagree?" These are now algorithmically suppressed by LinkedIn. The system bans them.
- **Designed to game the algorithm short-term.** The system trades short-term hacks for long-term compounding. If you want this week's growth hack, this is the wrong project.

**If your definition of "good" is different from ours, this project may not be the right tool for you.**

For example: if you measure success in raw follower growth, this system will frustrate you because it deliberately trades reach for voice authenticity. If you sell mass-market products and need viral hits, this system optimizes for the wrong audience size. If you're running corporate brand content for a Series B+ company, the rules around personal voice and earned vulnerability may not apply.

**Fork it, adjust it, or use a different tool.** That's a legitimate choice. We're naming our editorial position so you can make it consciously, not by accident.

The rest of the README assumes you're aligned with the definition above. The whole rest of the project — every rule, every gate, every workflow step — is built around it.

---

## Built on the LinkedIn playbook (without losing your voice)

We studied the actual mechanics of the platform — the 360Brew algorithm research, the engagement studies, the dwell time data, the format benchmarks, the 2M+ post analyses from independent researchers — and built every rule in this system around what LinkedIn actually rewards.

**Every post the workflow generates is optimized for:**

- **Hook engineering.** The first 210 characters earn the "see more" click or they don't. Every post is structured so the visible portion creates an open loop the reader has to expand to resolve. *(Rulebook §4.2)*
- **Closing types that drive comments.** Type A (genuine question), Type B (incomplete statement), Type C (practical nudge), each tied to your specific LinkedIn goal. Statement-only endings are banned because they close the conversation before it starts. *(Rulebook §4.1)*
- **Dwell time.** 200-350 word sweet spot, paragraph rhythm tuned for mobile readability, the strongest insight placed in the middle third of the post (not the end) to reward readers who stay past the fold. *(Rulebook §4.3)*
- **Format diversity.** Text + image, carousel, poll, video, multi-image — with batch-level variety enforced so your feed doesn't get repetitive. *(Rulebook §5.1)*
- **Hashtag strategy.** 0-2 in body, 2-4 in first comment, mid-volume range (10K-500K), no spam signals. *(Rulebook §7)*
- **Posting cadence and timing.** Data-driven day selection, target audience's timezone (not yours), no weekend posts unless your engagement data says otherwise. *(Rulebook §4.7)*
- **Pillar consistency over 60-90 days.** The LinkedIn algorithm builds topical authority signals that take weeks to compound. The system enforces it across every batch. *(Rulebook §4.8)*
- **Hook-to-close coherence, see-more engineering, conversation continuation, image strategy, first-comment design** — the full engagement architecture, not a single trick. *(Rulebook §4-§5)*

That's the playbook side. Most LinkedIn content tools stop here.

**The thing most tools miss:** every algorithmic best practice in the world is worthless if your post sounds like the same generic AI thought leader as 50,000 other accounts. The platform rewards consistency, but only consistency that's *recognizably yours*. Optimized content that all sounds the same is the trap most AI content tools fall into — and it's exactly what makes the algorithm flag it as low-quality.

So we built the second half of the system around protecting your voice while you optimize:

- **Voice-locked to your real writing.** You paste 5 things you've already written into your brand profile. The system calibrates word choice, sentence rhythm, formality, contractions, and signature phrases from your actual writing — not from a "professional LinkedIn tone" preset.
- **A 1,200-line rulebook of patterns to ban.** Tier 1 vocabulary (delve, leverage, harness, transformative), polished closing parallels, manufactured vulnerability arcs, two-word kickers, "Not because X. Because Y." constructs used more than once per post, 24 other AI sentence-level tells.
- **An independent critic loop.** Every batch is reviewed by a fresh agent (in Claude Code, this is a sub-agent spawn — the user does nothing) that checks against the rulebook AND your specific voice samples. Catches the things the generator misses or unconsciously defends.
- **Earned vulnerability over manufactured vulnerability.** Failures that still hurt, not failures with tidy redemption arcs. The single most important rule in the project — and the one that separates content people save from content people scroll past.
- **Per-brand "always avoid" lists.** Your custom banned words, separate from the universal rulebook. What "playbook" means to a SaaS founder is not what it means to a designer.

**Most LinkedIn tools optimize for the algorithm and lose the voice. A few optimize for voice and ignore the platform mechanics. We do both — because both matter, and they don't have to be in conflict.**

The whole point of the project is to refuse the trap of doing it like everybody else. Optimized AND genuine. Not one or the other.

---

## What you get

- **A canonical rulebook** at [`rulebook/linkedin-growth-engine-rulebook.md`](./rulebook/linkedin-growth-engine-rulebook.md) — every content rule the system enforces, with reasoning. 11 sections covering ground rules, anti-patterns, quality gates, engagement architecture, format rules, hashtags, performance feedback, competitive intelligence, and reshare strategy.
- **19 modules** at [`modules/`](./modules/) — 12 thin wrappers pointing back to the rulebook (load only what you need) plus 7 standalone modules covering polls, newsletters, profile alignment, DM conversion, connection growth, content recycling, and cultural profiles for non-US markets.
- **An executable workflow** at [`CONTENT-GENERATION-WORKFLOW.md`](./CONTENT-GENERATION-WORKFLOW.md) — 8 steps from "blank page" to "scheduled batch," with explicit First-Run Mode and Returning Mode branches.
- **A brand profile system** at [`templates/`](./templates/) — minimal (15-min setup, for your first batch) and full (30-min setup, for users committed to a weekly cadence), plus a fully filled-in fictional example.
- **An optional agent template** at [`agent/`](./agent/) — for users who want to wrap the skill in a persistent Claude Code agent identity. Skip on first run; build later if you commit to weekly batches.
- **Worked examples** at [`examples/`](./examples/) — a complete sample post batch with critic review notes, and 6 anti-pattern catches showing the system stopping bad content mid-generation.

---

## Honest time expectations

The first batch is real work. After that it gets fast.

| Phase | First batch ever | Steady state (Batch 4+) |
|-------|------------------|---|
| One-time brand profile setup (minimal) | 15-30 min | 0 min |
| Run workflow Steps 2-7 | 30-40 min | 15-20 min |
| Critic loop (Step 5b) | 10-15 min | 5-10 min |
| Your story input (Step 3) | 5-10 min | 5 min |
| Schedule (Step 8) | 5 min | 5 min |
| **Total** | **65-100 min** | **30-40 min** |

**Translation:** budget a Saturday morning for your first batch. Subsequent batches fit in a Monday morning ritual.

Anyone who tells you AI content takes 5 minutes a week is either lying or shipping content that reads like AI. The 30 minutes you spend each week is what makes the output sound like you instead of like every other LinkedIn account.

---

## Quickstart (10-minute trust test)

If you're skeptical, start here. Read these three files in this order:

1. **[Catch 5 in anti-pattern-catches](./examples/anti-pattern-catches/README.md)** (3 min) — start with the proof. The before/after above is just one example.
2. **[The example brand profile](./templates/example-brand-profile.md)** (4 min) — see what a well-formed input looks like for a fictional fractional CMO named Alex Hayes
3. **[The sample post batch README](./examples/sample-post-batch/README.md)** (3 min) — see the 4 posts the system generated for Alex, with quality check tables and critic notes

Total: 10 minutes. If after 10 minutes you don't believe the system works, close the tab. If you do, follow [`docs/quickstart-15-minute.md`](./docs/quickstart-15-minute.md) and ship your first batch this weekend.

---

## How it works (the 30-second version)

```
Your brand profile (positioning, voice samples, pillars, story bank)
            +
The rulebook (universal content rules, anti-patterns, quality gates)
            +
The workflow (8-step weekly batch process)
            ↓
A weekly batch of 4 LinkedIn posts that pass:
  • 12 per-post quality checks (vocabulary, voice, structure, fabrication, etc.)
  • An independent critic review (separate agent, fresh eyes — catches what the generator misses)
  • A batch-level variety audit (no two posts share the same shape)
  • A cross-batch sequence check (no rhythmic drift across weeks)
            ↓
You publish manually via LinkedIn's native scheduler.
```

The whole system is opinionated. The rulebook bans words. The workflow refuses to generate without voice samples. The critic sends posts back for rewrites. This is a feature, not a bug — the looser the rules, the more your output will read like every other AI-generated post on LinkedIn.

---

## Your first 4 weeks

The system compounds. Here's the curve to expect:

| Week | What you'll feel |
|------|-------------------|
| **Batch 1** | "OK, 3 of 4 are good. The fourth needs a rewrite." Critic loops 2-3 times per batch. |
| **Batch 2** | "I added 2 more voice samples and the posts sound more like me now." Critic loops 1-2 times per batch. |
| **Batch 3** | "The story bank is starting to pay off — Post 2 used a real situation I'd forgotten about." Most posts pass critic on first round. |
| **Batch 4** | "The agent knows my voice better than my last marketer did." Critic loops 0-1 times per batch. You're spending more time reviewing than rewriting. |

This is the difference between a content tool (one-shot value) and a content *system* (compounding value). The retention mechanic is real and it's mechanical: every batch, your brand profile gets sharper, your story bank gets deeper, and the agent's calibration to your voice improves.

---

## How to use it (the actually-easy version)

This project is a folder of markdown files. **Nothing installs. Nothing runs in the background. Nothing logs into LinkedIn for you.**

### Step 1 — Clone

**If you use Claude Code:**

```bash
git clone https://github.com/AdrienCastelain/linkedin-growth-engine.git ~/.claude/skills/linkedin-growth-engine
```

**If you use Claude Desktop, Claude.ai, ChatGPT, Cursor, or anything else:**

```bash
git clone https://github.com/AdrienCastelain/linkedin-growth-engine.git
cd linkedin-growth-engine
```

### Step 2 — Open Claude pointed at the folder

- **Claude Code:** open it in any project. The skill will be discoverable.
- **Claude Desktop:** add the folder as a project context source.
- **Claude.ai web / ChatGPT / Cursor:** open a chat in your IDE or browser. You'll paste files in Step 4 below.

### Step 3 — Type literally anything

*"hi"* — *"help"* — *"what is this"* — *"let's start"* — *"I want to ship LinkedIn posts"*

Claude reads [`CLAUDE.md`](./CLAUDE.md), detects what mode you're in (new user, returning user, mid-setup), and walks you through the right path. **You don't need to know which file to open, what command to type, or what "First-Run Mode" means.** The bootstrap file does the routing for you.

### Step 4 — Follow Claude's lead

If you're new, Claude runs you through brand profile setup (~15-20 min) by asking one question at a time and saving your answers to a `_user/` subfolder in your current directory. Then it runs your first content batch (~30-45 min) and produces 4 LinkedIn posts you'd actually publish.

If you're a returning user, Claude detects your existing brand profile in `_user/` and goes straight to "want to run this week's batch?"

That's the whole flow. There is no Step 5.

> **Where your files live:** Claude saves your brand profile, content audit, and industry research to `_user/` inside the folder you're working from. The `.gitignore` already excludes `_user/` so your data won't accidentally get committed if you push the repo somewhere. For multi-brand users, see the "Running this for multiple brands" section below.

> **Note for Claude.ai web / ChatGPT users:** Without local file system access, Claude can't auto-detect your state or write your brand profile to disk. You'll need to manually paste files and save outputs. The bootstrap will recognize the constraint and adapt — it'll give you the brand profile content as markdown for you to save manually, and walk you through the same flow with copy-paste handoffs. Slower than Claude Code but the same end result.

---

## What if I don't want Claude to drive?

If you prefer to read the docs and run the workflow manually instead of having Claude orchestrate, that path still exists. Read [`docs/quickstart-15-minute.md`](./docs/quickstart-15-minute.md) and follow the steps yourself. Both paths produce the same output — the bootstrap is a guided wrapper around the same underlying workflow.

---

## Running this for multiple brands (agencies & fractional CMOs)

If you manage LinkedIn content for multiple brands — your own plus 1-3 client retainers — the project supports it natively. There's no multi-tenancy mode; it's simpler than that.

**The pattern:** one folder per brand. Each brand folder has its own `_user/` subfolder containing that brand's profile, audit, research, and (optionally) agent definition. The LGE skill is installed once and shared across all brands.

```
my-clients/
├── my-own-brand/
│   └── _user/
│       ├── my-brand-profile.md
│       ├── my-content-audit.md
│       ├── my-industry-research.md
│       └── my-content-agent.md (optional)
├── client-a/
│   └── _user/
│       ├── my-brand-profile.md
│       ├── my-content-audit.md
│       └── my-industry-research.md
└── client-b/
    └── _user/
        └── ...
```

To run a batch for a specific brand, `cd` into that brand's folder and invoke Claude. The bootstrap (CLAUDE.md) detects that you're inside a brand folder, finds `_user/` in the current directory, loads the brand profile from there, and runs the workflow against it. Each brand gets its own voice, story bank, pillars, and avoid list — no cross-contamination.

**The hard rules:**

1. **Never share a brand profile across brands.** Voice drift is guaranteed.
2. **Never share a story bank across brands.** A story from Client A's work cannot show up in Client B's content.
3. **Never share an agent identity across brands.** If you're using the agent layer, build one agent per brand.
4. **Each brand's "always avoid" list is independent.** What "playbook" means to a SaaS founder is not what it means to a designer.

Real talk on time: managing 3 brands is roughly 3x the steady-state time, so ~1.5 hours per week. Compared to writing all of that content yourself, it's still a massive saving. Compared to a tool that generates fast and ignores voice, it's slower but produces work you'd actually publish.

**For agencies:** the maintenance moat (the rulebook updating monthly) compounds across all your clients simultaneously. Update once, every brand benefits.

---

## A few clarifications

Three things worth stating plainly so you have the right mental model from the start:

- **It's a draft generator, not an autopilot.** The workflow produces 4 polished posts per week. You review them, decide which to ship, and schedule them yourself in LinkedIn's native scheduler. There is no version of this that logs into LinkedIn for you. (Background on why: LinkedIn's posting API requires Marketing Developer Platform approval that takes weeks and isn't granted to individuals, and browser automation risks account suspension. See [`docs/scheduling-options.md`](./docs/scheduling-options.md).)
- **It's a markdown skill, not a SaaS.** Free, MIT licensed, no signups, no API keys, no telemetry. Clone the repo, point Claude at it, run it. We're not collecting anything and we're not charging for anything. The asset is the rulebook.
- **It's English-only for v1.0.** The banned vocabulary lists, em dash rules, and broetry patterns are English-specific. If you need another language, fork the rulebook and translate it (the workflow itself is language-agnostic). See [`docs/customizing-the-anti-patterns.md`](./docs/customizing-the-anti-patterns.md).

---

## Documentation

| Doc | Read this if you want to... |
|-----|------------------------------|
| [`docs/quickstart-15-minute.md`](./docs/quickstart-15-minute.md) | Ship your first batch as fast as possible |
| [`docs/running-the-workflow.md`](./docs/running-the-workflow.md) | Understand the 8-step weekly cadence |
| [`docs/creating-your-brand-profile.md`](./docs/creating-your-brand-profile.md) | Fill in the brand profile properly (especially the voice samples section) |
| [`docs/creating-your-content-agent.md`](./docs/creating-your-content-agent.md) | Wrap the skill in a persistent Claude Code agent |
| [`docs/troubleshooting.md`](./docs/troubleshooting.md) | Diagnose voice drift, repetitive batches, fabrication flags, critic loops |
| [`docs/scheduling-options.md`](./docs/scheduling-options.md) | Decide between native scheduler, API, or automation |
| [`docs/customizing-the-anti-patterns.md`](./docs/customizing-the-anti-patterns.md) | Add your own banned words or fork the rulebook for another language |
| [`docs/producing-your-content-audit.md`](./docs/producing-your-content-audit.md) | Pull last month's LinkedIn analytics into the audit template |
| [`docs/producing-your-industry-research.md`](./docs/producing-your-industry-research.md) | Refresh your monthly industry research |

---

## Who built this and why it's free

This system was built and refined inside an AI design studio that uses it for its own brand and for client work. The rulebook went through review by two independent LinkedIn experts (10 and 20 years of experience) and the anti-pattern catalogue was assembled from 25+ research sources on AI content detection.

It's free because the asset that matters — the rulebook — is more valuable as a reference document than as a paywalled SaaS feature. You're going to write LinkedIn posts whether you use this or not. You might as well write better ones.

**Maintenance commitment:** the rulebook will be updated monthly based on the new AI tells we observe in the wild. Static rule lists age out as model training advances. This one won't. See [`CHANGELOG.md`](./CHANGELOG.md) for what's new each month.

---

## Share it

If you use it and it works for you, the only thing we'd ask: send it to one other person who'd recognize the problem.

A copy-pasteable note for your DMs:

> Someone finally wrote down the rules the rest of the AI content tools are pretending don't exist. It's free, MIT licensed, takes ~30 min/week once you're past the first batch. Skip the README and read this one file: [link to anti-pattern-catches]. Catch 5 is the moment it clicked for me.

That's the whole growth model.

---

## License

MIT. See [`LICENSE`](./LICENSE). Use it commercially, fork it, modify it, redistribute it. Don't sell it back to us as a SaaS without saying where it came from.

---

## Contributing & feedback

Bug reports, rule additions, language forks, and worked examples all welcome. See [`CONTRIBUTING.md`](./CONTRIBUTING.md).

**Most useful contribution:** if your critic missed a pattern that should have been caught, or you noticed a new AI tell in the wild, file an issue in the "rulebook gaps" category. Your real-world catches become the next month's rulebook update. The maintenance is the moat — the more we hear from users about what's slipping through, the sharper the rulebook stays.

The one rule for contributions: **the rulebook stays opinionated.** If a proposed change softens a rule or adds hedging language, the answer is probably no. The whole project's value is that the rules have teeth.
