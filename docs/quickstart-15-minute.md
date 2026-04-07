# Quickstart — Your First Batch in 60-90 Minutes

> **Goal:** From `git clone` to a complete batch of 4 LinkedIn posts you'd actually publish, in 60-90 minutes of focused work.
>
> **Honest framing:** Anyone who tells you AI content takes 15 minutes a week is shipping content that reads like AI. The first batch is real work — gathering voice samples, filling in a brand profile, running the workflow, looping with the critic, scheduling. Subsequent batches drop to 30-40 minutes once your brand profile is set up. Block a Saturday morning for this. Set a timer.
>
> **Prerequisites:** A computer, an LLM you can run prompts in (Claude.ai, ChatGPT, Claude Code, Cursor, etc.), and 5 things you've already written.

---

## Before you start: gather your 5 voice samples

**This is the single highest-leverage thing you can do for your first batch.** The system uses these to calibrate everything: word choice, sentence rhythm, formality, contractions, signature phrases. Without them, the output drifts toward generic AI voice.

**What counts as a voice sample:**
- A LinkedIn post you wrote yourself (not a draft a contractor wrote for you)
- A long email or Slack message in your natural voice
- A blog post excerpt
- A podcast transcript
- A reply on Twitter/X, Reddit, or Hacker News
- A long comment you left on someone else's post

**What doesn't count:**
- Anything written by a marketer, ghostwriter, or AI on your behalf
- Job descriptions, product copy, or About pages (too polished)
- Direct messages in a register you wouldn't use professionally

**Goal:** 5 samples, 100-300 words each. Total ~1,000 words of *your actual writing*.

**Time:** 5-10 minutes if they're easy to find. 30+ minutes if you have to hunt.

> **Tip:** If you only have 2-3 samples on hand, paste those and proceed. The system works with 3 samples. It works better with 5. It refuses to run with 0.

---

## Step 1 — Clone the repo (1 minute)

### If you're using Claude Code (recommended)

Clone directly into your skills directory so Claude Code can load it:

```bash
git clone https://github.com/AdrienCastelain/linkedin-growth-engine.git ~/.claude/skills/linkedin-growth-engine
cd ~/.claude/skills/linkedin-growth-engine
```

Then in any Claude Code session:

```
Load the linkedin-growth-engine skill
```

### If you're using any other AI runtime (Claude.ai, ChatGPT, Cursor, etc.)

Clone anywhere convenient:

```bash
git clone https://github.com/AdrienCastelain/linkedin-growth-engine.git
cd linkedin-growth-engine
```

You'll paste files into your AI manually in Step 5. No installation, no dependencies, no API keys. The whole project is markdown.

---

## Step 2 — Copy the minimal brand profile (1 minute)

Create a `_user/` subfolder and copy the minimal template into it:

```bash
mkdir -p _user
cp templates/brand-profile-minimal.md _user/my-brand-profile.md
```

Open `_user/my-brand-profile.md` in your editor.

> **Why `_user/`?** It keeps your personal data (brand profile, voice samples, story bank) cleanly separated from the project's shared files. The `.gitignore` already excludes `_user/` so your data won't accidentally get committed if you push the repo somewhere. For multi-brand users, each brand folder has its own `_user/` subfolder.

---

## Step 3 — Fill in the minimal profile (15-25 minutes)

The minimal profile has 4 sections. Fill them in this order:

### 3a. Positioning (1 min)

One sentence: "I help [WHO] do [WHAT] so they can [OUTCOME]."

If you can't write this in 60 seconds, paste a placeholder and come back to it. Don't let positioning block the rest of the setup.

### 3b. LinkedIn Goal (30 sec)

Pick one. Inbound leads, thought leadership, or grow audience covers 80% of cases. Don't agonize.

### 3c. Content Pillars (3 min)

Three or four topics you can credibly talk about for the next 12 months. Don't worry about weights — defaults will be applied.

**Quality test:** Could you write 10 posts about each pillar from your own experience without making anything up? If not, the pillar is too narrow. Widen it.

### 3d. Voice Profile — Reference Samples (10-15 min)

This is the section you cannot skip. Paste your 5 samples directly into the file under Sample 1 through Sample 5. Don't edit them. Don't polish them. Paste verbatim.

### 3e. Always Avoid (30 sec)

3-5 words you would never naturally use. The rulebook already bans the obvious ones (delve, leverage, harness, etc.). Add anything specific to you — words you've noticed yourself flinching at when other people use them, or jargon from your field that sounds hollow.

**Save the file.**

> **The story bank trap:** The minimal profile skips the story bank to keep your first batch fast. That's fine — but the *best* output (like the example sample batch's Post 2) leans hard on the story bank. After Batch 1 you'll see what I mean. Plan to add a story bank before Batch 3 by upgrading to [`brand-profile-template.md`](../templates/brand-profile-template.md) (the full version). Until then, expect the workflow to occasionally pause and ask you for a story.

---

## Step 4 — Open the workflow (1 minute)

Open `CONTENT-GENERATION-WORKFLOW.md`.

Read the **Run Modes** section at the top. You're in **First-Run Mode** because you have no prior content audit, no industry research, and possibly no LinkedIn analytics yet. First-Run Mode skips Step 1 and runs Step 2 from your pillars alone.

You don't need to read the rulebook to run the workflow. The workflow references the rules; the rules execute themselves through the quality gates.

---

## Step 5 — Run the workflow against your profile (20-40 min agent time)

How you run this depends on your setup:

### Option A — Claude Code with skills (lowest friction)

If you cloned into `~/.claude/skills/linkedin-growth-engine` and the skill is loaded:

```
Load the linkedin-growth-engine skill.
My brand profile is at ./_user/my-brand-profile.md (relative to my current working directory).
Run the CONTENT-GENERATION-WORKFLOW in First-Run Mode.
```

Or, even simpler, just type "hi" and let the bootstrap (CLAUDE.md) detect the state and route you. The bootstrap will find `_user/my-brand-profile.md` automatically.

The skill will execute Steps 2-7, prompt you for any story input it needs (Step 3), and produce a complete content package at Step 7.

### Option B — Single chat (Claude.ai, ChatGPT, etc.)

> **Context-limit warning:** The full rulebook is ~1,200 lines (~30K tokens). Plus the workflow (~600 lines), plus your brand profile (~200 lines), plus the generated posts. This will work on Claude.ai Pro or ChatGPT Plus. Free-tier models may truncate mid-Step-5. If you're on a free tier, use the slimmer paste below.

**Standard paste (Pro-tier or larger context models):**

Open a new conversation. Paste this prompt:

```
You are running the LinkedIn Growth Engine workflow in First-Run Mode.

I'm pasting four things below:
1. The workflow file (CONTENT-GENERATION-WORKFLOW.md)
2. The rulebook (rulebook/linkedin-growth-engine-rulebook.md)
3. My brand profile (_user/my-brand-profile.md)
4. The cultural profile (modules/19-cultural-profiles.md) — only if my audience is non-US

Execute Steps 2 through 7. Skip Step 1 (First-Run Mode). When you reach Step 3 (Story Harvesting), pause and ask me for story input. When you reach Step 5b (Critic Review), tell me to spawn a fresh chat for the critic — I'll do it manually.

Produce the final content package at Step 7 in markdown format.

[paste workflow file]

[paste rulebook file]

[paste brand profile file]

[paste cultural profile if applicable]
```

**Slim paste (free-tier or context-constrained):**

Instead of the full rulebook, paste only modules 01, 02, 03, 04, and 06. They cover the rules the workflow's Step 5 actively checks. The other modules are for advanced use and aren't needed for first batch.

```
Execute Steps 2-7 of CONTENT-GENERATION-WORKFLOW in First-Run Mode against my brand profile. The relevant rules are in modules 01 (ground rules), 02 (anti-patterns), 03 (quality gates), 04 (engagement architecture), and 06 (format & first comment). Pause at Step 3 for story input.

[paste workflow file]
[paste modules 01, 02, 03, 04, 06]
[paste brand profile]
```

### Option C — Cursor or other IDE agents

Same as Option B, but use the chat panel in your IDE. Reference the file paths instead of pasting full file contents if your IDE supports it.

---

## Step 6 — Run the critic (5-10 minutes)

When the workflow reaches Step 5b, **open a new chat** (different conversation, different tab). The critic must be a fresh instance — same-conversation critics defend their earlier output instead of catching it.

**Copy and paste this prompt verbatim** into the new chat:

```
You are an independent critic reviewing 4 LinkedIn posts that were just generated by the LinkedIn Growth Engine workflow. You did NOT generate these posts. Your job is to flag issues, not rewrite them.

Read the following files:
1. The rulebook — pay especially close attention to §1 (Ground Rules), §2 (Anti-Patterns), §2.3 (banned structural patterns), §2.8 (AI sentence-level tells), §3 (Quality Gates).
2. The brand profile — pay especially close attention to §5 (Voice Profile, including the reference samples and the "always avoid" list).
3. The 4 generated posts.

Then review each post against three lenses:

LENS 1 — AI Detection: Does this read like a real person wrote it, or does it feel "produced"? Flag specific sentences. Look for: polished parallel closings, two-word kickers, manufactured vulnerability arcs, "Not because X. Because Y." patterns repeated more than once per post, residual banned vocabulary the self-check missed, templating across posts.

LENS 2 — Voice Match: Does it sound like the same person who wrote the reference samples in §5c? Flag any sentence where the register shifts. Cross-check against the "always avoid" list in §5d.

LENS 3 — Conversion: Will this work for the brand's stated LinkedIn goal? Does the hook earn the "see more" click in 210 characters? Does the closing match its declared type? Would the ICP self-identify with this?

For each post, output:
=== POST [N] ===
AI Detection: AUTHENTIC / NEEDS_REWORK
  - [specific flagged sentences with explanation]
Voice Match: VOICE_MATCH / VOICE_DRIFT
  - [specific drift points]
Conversion: EFFECTIVE / WEAK
  - [specific weakness]
Recommendation: PASS / REWRITE lines X-Y / RESTRUCTURE / REPLACE TOPIC

Now here are the files:

[paste rulebook]

[paste brand profile]

[paste the 4 posts from your generator chat]
```

The critic will return PASS or REWORK for each post. Take the REWORK feedback back to your generator chat and ask it to rewrite the flagged lines.

**Most common Round 1 issues you'll see:**
- A polished closing line that should be incomplete
- A two-word kicker the generator added at the end
- A banned word the generator missed
- A "manufactured vulnerability" arc with too tidy a resolution

These are the rules earning their keep. Apply the rewrites and re-run Step 5b until all 4 posts pass.

---

## Step 7 — Review the final batch (5 minutes)

Read the 4 posts in order. Ask yourself:

- Do they sound like you?
- Is there at least one post you'd be a little embarrassed by (in the good way — because it's vulnerable or contrarian)?
- Are they different from each other?
- Could you defend every number, name, and claim?

If yes to all four → ship them. If any are no → either rewrite or scrap that post.

---

## Step 8 — Schedule (5 minutes)

Open LinkedIn → Start a post → paste post 1 → click the clock icon → schedule for Tuesday 8:00 AM. Repeat for posts 2-4 across the rest of the week.

That's it. You just shipped a content batch.

See [`scheduling-options.md`](./scheduling-options.md) for the longer answer on why manual is the recommended path.

---

## Batch 1 common gotchas

If you hit any of these mid-flow, here's the quick fix:

| Symptom | Quick fix |
|---------|-----------|
| **"My critic keeps rewriting more than I'd expect"** | Normal for Batch 1. The critic is calibrating to your voice samples. Expect 2-3 loops for the first batch and 0-1 loops by Batch 4. |
| **"My posts don't sound like me"** | Your reference samples are too thin or too generic. Add 2-3 more samples from different formats (Slack, email, blog) and re-run Step 4. |
| **"I'm stuck at Step 5b — opening a new chat is annoying"** | This is the highest-friction moment in the whole workflow. It's also where the most value is added. Don't skip it. Use the copy-paste prompt block above so you don't have to assemble it from scratch each week. |
| **"Step 4 generated a post that needs a story I don't have"** | The workflow paused at Step 3 to ask you. Answer in 2-3 sentences with one specific number, name, or timeframe. Don't write more. |
| **"The agent says it can't find the rulebook"** | In Option A, make sure the skill is loaded. In Options B/C, you forgot to paste the rulebook. Re-paste. |
| **"Step 6 batch variety audit failed"** | Two of your posts are too similar. Re-run Step 4 for the weakest post with explicit variation: "make this one shorter (150 words) and use a different hook angle." |

For deeper failure modes, see [`troubleshooting.md`](./troubleshooting.md).

---

## What to do after your first batch

1. **Watch what happens.** Track which post got the most reactions, comments, and DMs over the next 5 days.
2. **Note what felt off.** Was any post too generic? Was any line not how you'd actually phrase it? Add the words you noticed to your "always avoid" list.
3. **Add 2-3 more voice samples.** Whatever wasn't quite right in Batch 1 will get corrected if you give the system more calibration data.
4. **Run Batch 2 next week.** The cadence is what compounds. One batch is a test. Eight batches in a row is a system.
5. **Add a story bank.** Open [`brand-profile-template.md`](../templates/brand-profile-template.md) (the full version), copy your minimal profile fields over, and start filling in Section 7. Five real stories with specific numbers and timeframes will measurably improve Batch 3 onward.
6. **After 30 days,** switch from First-Run Mode to Returning Mode. Produce your first content audit using [`templates/content-audit-template.md`](../templates/content-audit-template.md), and start the monthly industry research cycle.

---

## What you should expect to feel

**About 3 minutes into the brand profile:** "this is a lot of fields." Push through. The samples section is the only one that takes real time.

**When you read Batch 1:** "this sounds more like me than I expected." That's the system working. If it doesn't feel that way, your reference samples weren't the strongest 5 you could have picked. Replace 1-2 of them and regenerate.

**At Step 5b critic loop:** "the generator just produced 4 posts and now I'm being asked to break them?" Yes. The critic is the difference between "good drafts" and "drafts I'm willing to publish under my own name." Don't skip it.

**Two batches in:** "this is faster than I thought." Yes. The first batch has setup overhead. Subsequent batches reuse everything.

**Four batches in:** "the system is starting to know my voice better than my last marketer did." That's the compounding effect of voice samples + critic review + iteration. It's why this is built around weekly batches, not one-off generation.

---

## Help — something didn't work

| Symptom | Where to look |
|---------|---------------|
| Workflow refused to start (missing voice samples) | Re-paste samples into brand profile §5c (the only HARD STOP gate) |
| Generated posts don't sound like me | [`docs/troubleshooting.md`](./troubleshooting.md) — voice drift section |
| Critic flagged the same issue 3 times in a row | [`docs/troubleshooting.md`](./troubleshooting.md) — critic loops |
| Step 8 (scheduling) confusion | [`docs/scheduling-options.md`](./scheduling-options.md) |
| Story bank prompts feel off | [`docs/creating-your-brand-profile.md`](./creating-your-brand-profile.md) — story bank section |
| Anything else | Open a GitHub issue with the step number and what happened |
