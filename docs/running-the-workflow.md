# Running the Workflow

> **What this is:** The operator's guide to the weekly content batch. The workflow file ([`CONTENT-GENERATION-WORKFLOW.md`](../CONTENT-GENERATION-WORKFLOW.md)) is the executable spec — short, terse, written for an LLM. This doc is the human-readable companion that explains what each step is doing, what to expect, and how to handle the common moments where the workflow needs your judgment.
>
> **Who this is for:** Anyone running the workflow more than once. If you're running it for the first time, start with [`quickstart-15-minute.md`](./quickstart-15-minute.md) instead.

---

## The shape of a weekly batch

You run the workflow once a week. Each run produces 4 posts scheduled across the next week. The total time from "start the workflow" to "all 4 posts scheduled" is roughly:

| Phase | First batch ever | Steady state |
|-------|------------------|---------------|
| Brand profile setup | 15-30 min (one-time) | 0 min |
| Run workflow Steps 2-7 | 30-40 min | 15-20 min |
| Critic loop (Step 5b) | 10-15 min | 5-10 min |
| Your story input (Step 3) | 5-10 min | 5 min |
| Schedule (Step 8) | 5 min | 5 min |
| **Total** | **65-100 min** | **30-40 min** |

The compounding effect is real: by Batch 4, the agent knows your voice well enough that critic loops drop to 1-2 issues instead of 4-5, and you spend more time on review than on rewrites.

---

## First-Run Mode vs Returning Mode

The workflow has two modes. The mode you use determines which steps run and which steps skip.

### First-Run Mode

**When:** Your first batch ever, or any batch where you don't have a content audit, monthly industry research, or LinkedIn analytics.

**What's different:**
- **Step 1 (Performance Review) is skipped entirely.** No analytics yet, nothing to review.
- **Step 2 (Topic Selection) runs from your pillars alone.** Skips the audit filter, the research filter, and the performance-data tilt.
- **Step 6 (Batch Review) skips the cross-week sequence check.** No prior batches to compare against.
- The Prerequisites block at the top of the workflow is bypassed.

**Required inputs:** A filled-in brand profile (minimal or full) with reference voice samples in §5c.

### Returning Mode

**When:** You've published at least 4 posts and have 30+ days of LinkedIn analytics, plus current content audit and industry research files.

**What's different:**
- All 8 steps run.
- Topic selection uses last month's performance data to bias toward your best-performing pillar.
- The cross-week sequence check makes sure this week's batch doesn't repeat patterns from the previous 3 weeks.

**Required inputs:** Filled-in full brand profile, current content audit (≤30 days old), current industry research (≤30 days old).

**How to switch:** After your first month of published posts. Specifically, once you've shipped at least 4 posts, can pull engagement metrics from LinkedIn, and have filled in your audit + research files. Most users hit this around month 2.

---

## Walking through each step

### Step 1 — Performance Review (Returning Mode only)

**What it does:** Looks at last month's engagement data and produces a summary identifying your best-performing pillar, structure, hook style, and any reported outcomes (DMs, leads, calls).

**What it needs from you:** Last month's LinkedIn analytics, ideally already pasted into [`templates/content-audit-template.md`](../templates/content-audit-template.md). If you don't have analytics, see [`producing-your-content-audit.md`](./producing-your-content-audit.md) for how to pull them.

**Common failure mode:** "I ran this in Returning Mode but the agent didn't have my audit file." → Either pass the audit file path to the agent explicitly, or paste the contents of your audit into the conversation before running the workflow.

**What good output looks like:** A 5-line summary at the top of the agent's response identifying which pillar to lean into this week and which to reduce.

---

### Step 2 — Topic Selection

**What it does:** Generates 6-8 candidate topics from your pillars, filters them, picks the best 4, and assigns each post a structure type (niche_problem, case_study, contrarian, framework, process, transformation, failure_learning).

**What it needs from you:** Nothing if your brand profile is filled in. The agent runs this autonomously.

**Common failure mode:** Topic candidates feel generic. → Your pillars are too broad. Tighten the one-line description for each pillar in your brand profile so the agent has sharper boundaries.

**What good output looks like:** 4 topics, each one specific enough that you could write the post yourself if you had to. If the topics read like "thoughts on leadership" or "the importance of branding" — they're not specific enough. Push back and ask for sharper angles.

**The variety check at this stage:** At least 2 different pillars represented, no more than 2 posts of the same structure type, no topic that duplicates a post from your last 3 months.

---

### Step 3 — Story Harvesting

**What it does:** Identifies posts that need a real story from you (the `needs_input: true` flag from Step 2) and produces specific, easy-to-answer prompts.

**What it needs from you:** 2-3 sentences per prompt. Not a polished story. Just the bones — what happened, what was at stake, what the punchline was.

**Common failure mode:** "I gave it 2 sentences and the post the agent wrote feels thin." → The agent needs the *specific* details: a number, a name, a timeframe. "I had a client who was frustrated" isn't enough. "A founder in Q4 last year was about to drop her price 35% on a sales call to fill the silence" is enough.

**What good output looks like:** A short prompt for each `needs_input: true` post, with the specific scenario the agent wants you to fill in. You answer in 2-3 sentences. The agent generates the post from your input plus the brand profile context.

> **Important:** Step 3 references your story bank if you have one. If a topic matches an existing story bank entry, the agent will use that entry instead of asking you. This is why the story bank is the second-highest-leverage thing in your brand profile after voice samples.

---

### Step 4 — Post Generation

**What it does:** Generates each post using the brief from Step 2 + your voice profile + your story (if any) + the variation seed (which prevents two posts in the same batch from sharing the same shape).

**What it needs from you:** Nothing. The agent runs this autonomously.

**Common failure mode:** All 4 posts open with "I." → Your reference samples in the brand profile probably all open with "I." The agent learned that pattern. Add 1-2 samples that open with a situation, an observation, or a number, and re-run.

**What good output looks like:** 4 drafts that pass into Step 5 immediately. If a draft fails Step 5, the agent automatically returns it to Step 4 with the failed checks listed as the rewrite brief.

---

### Step 5 — Per-Post Quality Check

**What it does:** Runs every quality gate against every post. Vocabulary, punctuation, structure, transitions, voice, specificity, fabrication, opening, closing, LinkedIn-specific patterns, honest limitation, voice match. Plus the optional AI detection check.

**What it needs from you:** Nothing. This is the first line of defense, run automatically.

**Common failure mode:** Vocabulary check passes but the post still sounds generic. → The vocabulary check only catches the universal banned words. The brand-specific avoid list (your §5d) is checked at Step 5b by the critic. Make sure your avoid list isn't empty.

**What good output looks like:** A check table per post showing PASS on every line. If anything fails, the post returns to Step 4 with the failed gate as the rewrite brief.

> **The Fabrication Check is the only HARD FAIL gate.** Fabricated stories, invented data, and made-up quotes are removed, not edited. The post is returned to Step 3 (Story Harvesting) for real input, or replaced with a different topic.

---

### Step 5b — Independent Critic Review

**What it does:** A separate agent (NOT the one that generated the posts) reviews every post against three lenses: AI Detection, Voice Match, Conversion Effectiveness. Returns PASS or REWORK for each post.

**What it needs from you:** Either set up a fresh agent instance or paste the critic prompt into a brand-new chat. **The critic must not be the same agent that generated the posts.** Same-conversation critics defend their earlier output instead of catching it.

**Setup options:**
- **Claude Code with subagents:** Use the Agent tool to spawn a fresh general-purpose agent. Pass it the rulebook, brand profile, and the 4 posts.
- **Single chat (Claude.ai or ChatGPT):** Open a new conversation. Paste the critic prompt + the rulebook + brand profile + posts.
- **Cursor or other IDE:** Spawn a new chat panel. Same as single chat.
- **Skip mode (not recommended):** Re-run Step 5 self-checks twice with a 30-minute gap. Less effective but better than nothing.

**Common failure mode:** "The critic keeps flagging the same issue and the generator keeps not fixing it." → After 3 rewrite loops, the workflow escalates to human review. Read the critic's flag carefully — usually the issue is structural and the generator needs a different post entirely, not a line edit.

**What good output looks like:** A critic review sheet listing PASS or REWORK per post with specific lines flagged. Most batches have 0-2 REWORK posts in Round 1. By Batch 4, most batches pass cleanly.

---

### Step 6 — Batch Review

**What it does:** Audits the whole batch for variety: hook types, closing types, structures, pillars, lengths, sentence rhythm, and (in Returning Mode) cross-week sequence patterns.

**What it needs from you:** Nothing. Runs automatically.

**Common failure mode:** Variety audit fails because all 4 posts have similar lengths. → Step 4 should have varied this with the variation seed. If it didn't, the seed wasn't applied — re-run Step 4 with explicit length targets.

**What good output looks like:** A variety table showing PASS on every metric. If anything fails, the workflow returns the weakest 1-2 posts to Step 4 for regeneration.

---

### Step 7 — Package and Deliver

**What it does:** Bundles the 4 final posts into a structured package with first comments, reply templates, image prompts, hashtag placement, scheduling metadata, and a weekly preview summary.

**What it needs from you:** Nothing. The agent assembles this.

**What good output looks like:** A complete content package you can read top-to-bottom in 3 minutes. Each post has its full text, first comment, reply template, scheduled date/time, and metadata.

---

### Step 8 — Schedule

**What it does:** Walks you through scheduling the 4 posts via LinkedIn's native scheduler.

**What it needs from you:** ~5 minutes of clicking through LinkedIn's UI to schedule each post manually.

**Why manual:** LinkedIn's posting API requires Marketing Developer Platform approval that takes weeks and isn't granted to individuals. Browser automation against LinkedIn risks suspension. Manual scheduling via LinkedIn's native scheduler is the only realistic path for solo users. See [`scheduling-options.md`](./scheduling-options.md) for the full rationale.

---

## The weekly cadence

Pick a day. Run the workflow. The most common cadence:

- **Monday morning, 30-40 minutes:** Run the workflow, review the batch, schedule across Tue-Fri.
- **Throughout the week:** Reply to comments and DMs as posts go live.
- **End of month:** Pull the month's analytics, update your content audit, refresh your industry research, run a monthly performance review.

The reason it's weekly and not monthly: smaller batches mean fresher context, room to incorporate trends from this week, and smaller blast radius if a batch is bad. Monthly batches lock in 16 posts based on stale context. Weekly batches can adapt.

---

## What good looks like at the inbound-lead level

The docs spend most of their time on drafting. Drafting is the visible part. The harder question is: what should you actually expect to *happen* once you start shipping batches?

Honest expectations by month, for a typical solo expert brand starting from <2K followers and inbound leads as the goal:

| Period | What to expect |
|--------|----------------|
| **Batches 1-2** | 0-1 DMs per batch. Maybe 1-2 substantive comments per post. Probably no booked calls. The system is calibrating to your voice; the audience is still calibrating to your topic mix. |
| **Batches 3-4** | 1-2 DMs per batch. Some are warm leads, most are peers and curious people. First booked call from a post is realistic in this window. |
| **Batches 5-8** | 2-4 DMs per batch as your topical authority signal compounds (the LinkedIn algorithm rewards 60-90 day consistency). Reactions roughly double from Batch 1. The first inbound lead that becomes paid work usually lands here. |
| **Batches 8+** | The system starts feeling like a flywheel. Engagement compounds. Voice match is dialed in. The critic loop is mostly clean. You're spending more time on review than rewrites. |

**What this means:** if you're running this for inbound leads and you don't see DMs in Batch 1, the system isn't broken. Inbound is downstream of consistency, voice, and topic depth — and those are downstream of running the workflow weekly without skipping.

**What it doesn't mean:** if you've shipped 8 batches and you're getting zero DMs, *something* is wrong. Most likely culprits: positioning is too generic, pillars don't match what your ICP actually wants to read, or your profile (headline + About) isn't aligned with your post topics. See [Module 15 (Profile Alignment)](../modules/15-profile-alignment.md) and [`docs/troubleshooting.md`](./troubleshooting.md).

**The thing nobody else will tell you:** content isn't a magic conversion machine. It builds awareness, recognition, and trust over months. The DMs come from people who've seen 4-8 of your posts and decided you might be the right person for a problem they have. Be patient on the conversion side; be ruthless on the consistency side.

---

## When to break the workflow

The workflow is opinionated. You can break it sometimes:

**Skip Step 5b (critic review) when:**
- It's a true emergency timeline and you genuinely can't spin up a fresh agent
- You're running Batch 8+ and the generator has been clean for 3+ batches in a row
- (Never skip it for your first 3 batches.)

**Skip Step 6 (batch variety audit) when:**
- You're running 1-2 posts ad-hoc, not a full batch
- A timely event requires a one-off post outside the planned batch (this is what Rulebook §4.9 covers)

**Skip Step 8 (scheduling) when:**
- You're storing drafts for future use rather than publishing immediately
- You publish manually in real-time rather than scheduling

**Don't skip:**
- Step 5 (per-post quality check) — this is what catches Tier 1 banned words. There's no version of "shipping good content" without this.
- The Fabrication Check (inside Step 5) — never. Fabricated content is a HARD FAIL. No exceptions.
- The brand profile reference samples requirement — the workflow refuses to run without §5c filled in. This is a feature.

---

## What changes in Returning Mode

Once you switch from First-Run to Returning Mode (typically month 2):

- **Step 1 starts running.** You'll get a performance summary at the top of every batch identifying what worked last month.
- **Step 2 gets sharper.** Topic selection biases toward your best-performing pillar and reduces your worst.
- **Step 6 adds the cross-week check.** No more accidentally posting 3 contrarian posts in a row across consecutive weeks.
- **Your batches start feeling like a season, not a series of one-offs.** This is the compounding effect the rulebook is designed for — topic consistency over 60-90 days is what the LinkedIn algorithm rewards.

Read [`producing-your-content-audit.md`](./producing-your-content-audit.md) and [`producing-your-industry-research.md`](./producing-your-industry-research.md) before your first Returning Mode batch.
