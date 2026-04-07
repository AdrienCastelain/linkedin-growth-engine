# LinkedIn Growth Engine — Content Generation Workflow

**Type:** Agent-executable workflow
**Version:** 1.0 (public release)
**Executes:** Weekly LinkedIn content generation (4 posts per batch)

---

## ⚠️ Pre-flight check (AI: read this before running anything)

Before running any step of this workflow, verify the following:

1. **A user brand profile exists at `_user/my-brand-profile.md` in the user's working directory.** (See `./CLAUDE.md` Step 2a for `USER_FILES_DIR` resolution — user files always live in a `_user/` subfolder.)
   - If it doesn't exist → STOP. Route the user to the onboarding flow at `./agent/onboarding-flow.md` (or follow the routing logic in `./CLAUDE.md`). Never run this workflow without a real brand profile.
   - **Never run this workflow against `templates/example-brand-profile.md`.** That's a documentation file showing what a finished profile looks like, not a user file. Generating content for the fictional Alex Hayes persona is the wrong outcome.

2. **The brand profile has reference voice samples (Section 5 in minimal, §5c in full).**
   - If samples are empty or fewer than 3 → STOP. Tell the user: *"Your brand profile is missing voice samples. Without them, the system produces generic AI output. Let's add at least 3 samples before continuing."*

3. **You know which run mode applies.**
   - **First-Run Mode** if: brand profile exists but no `my-content-audit.md`
   - **Returning Mode** if: brand profile + content audit + industry research all exist (or audit exists and research is <30 days old)
   - When in doubt, default to First-Run Mode (it's safer — skips Step 1 and runs Step 2 from pillars only).

If any of the above fails, do not proceed with the workflow. Route the user to the appropriate fix in `./CLAUDE.md`.

---

## Purpose

This workflow produces a week of LinkedIn posts following the LinkedIn Growth Engine rules. It runs weekly. You interact with it once a week to answer story prompts, review the batch, and approve before scheduling.

**Why weekly, not monthly:** Smaller batches mean better content quality, fresher context, and room to incorporate weekly trending topics. The rulebook section on cadence is canonical.

**Cadence:**
- **Weekly:** Generate 4 posts (Steps 1-8 below)
- **Monthly:** Deeper performance review and strategy adjustments

**Do not interpret. Follow the steps.**

---

## Run Modes

There are two modes. Pick the one that matches you.

### First-Run Mode (use this if any of the following are true)
- You're running this workflow for the first time
- You don't have a content audit yet
- You don't have monthly industry research yet
- Your LinkedIn account has no posts, or you don't have access to last month's analytics
- You've only filled in [`templates/brand-profile-minimal.md`](./templates/brand-profile-minimal.md)

**What First-Run Mode does:** Skips Step 1 (Performance Review), runs Step 2 from pillars only, treats Step 6's cross-week sequence check as informational. You get a complete 4-post batch on your first run, even with zero prior data. After your first batch publishes and you have a week of metrics, switch to Returning Mode.

### Returning Mode (use this once you have prior data)
- You've published at least 4 posts and have 30+ days of LinkedIn analytics
- You've filled in [`templates/brand-profile-template.md`](./templates/brand-profile-template.md) (the full version)
- You have a current `my-content-audit.md` (≤30 days old)
- You have a current `my-industry-research.md` (≤30 days old)

> **When to switch from First-Run to Returning Mode:** After your first month of published posts. Specifically: once you've shipped at least 4 posts, can pull engagement metrics from LinkedIn, and have filled in your content audit and industry research files. Most users hit this threshold around month 2.

---

## Prerequisites (Returning Mode only)

```
□ This skill is loaded: SKILL.md
□ Your brand profile is filled in: templates/brand-profile-template.md OR brand-profile-minimal.md
□ Your brand profile contains at minimum: Positioning, Voice Profile (with reference samples), Content Pillars
□ Optional but recommended: Story Bank, Benchmark Accounts, Topics include/avoid
□ Industry Research file exists and is <30 days old
□ Content Audit file exists and includes your posts from the last 30 days
□ If audit or research is stale → STOP. Refresh, then resume.
```

> **First-Run Mode users:** Skip the prerequisites block above. You only need a brand profile (minimal or full) with reference voice samples filled in. Proceed to Step 1.

---

## Step 1: Performance Review

> **First-Run Mode:** Skip this step entirely. Note "Week 1 — no performance data" and proceed to Step 2.

**Input:** Your published posts from the last 30 days
**How to pull the data:** Open LinkedIn → your profile → Analytics → Posts. Copy the table or take screenshots into [`templates/content-audit-template.md`](./templates/content-audit-template.md). LinkedIn does not expose this via a public API for individuals — manual export is the only path for solo users.

**Action:** Analyse and produce a performance summary

```
For each post from last month:
  - Record: date, pillar, structure, topic, reactions, comments, reposts
  - Flag: which posts got above-average engagement
  - Flag: which posts got below-average engagement
  - Note: any DMs, connection requests, or enquiries you received

Produce:
  BEST_PERFORMING_PILLAR: [pillar with highest avg engagement]
  WORST_PERFORMING_PILLAR: [pillar with lowest avg engagement]
  BEST_PERFORMING_STRUCTURE: [structure type with highest avg engagement]
  ENGAGEMENT_TREND: [up / flat / down vs previous month]
  REPORTED_OUTCOMES: [any leads, DMs, calls attributed to posts]
```

**Output:** Performance summary
**Gate:** Summary must be produced before proceeding (Returning Mode only). First-Run Mode skips this step.

---

## Step 2: Topic Selection

**Input:** Your content pillars (always required) + industry research, content audit, performance summary (Returning Mode only)

> **First-Run Mode:** Generate 6-8 topic candidates from your pillars alone. Skip the audit/research filters. Skip the performance-data tilt. Pick 4 candidates that span at least 2 pillars and 3 different structure types. Move to Step 3.

**Action:** Select 4 specific post topics for the week

```
For this week:
  1. Generate 6-8 candidate topics across your pillars
  2. Filter candidates against:
     - Content Audit: remove any topic already covered in the last 3 months
       (First-Run: skip this filter)
     - Industry Research: prefer topics with current context (tie-in to what's happening THIS week)
       (First-Run: skip this filter)
     - Performance data: lean toward the BEST_PERFORMING_PILLAR, reduce WORST unless there's a strategic reason to keep it
       (First-Run: skip this filter)
     - Trending topics: weekly batches can incorporate fresh trends — check industry news
  3. Pillars drive selection, trends inform framing only. A trending AI story is relevant for a designer who talks about AI. A trending sports story is not. (See rulebook §4.9 for the timely-content rule.)
  4. For each candidate, assign a Structure Type from the Conversion Framework below:

     CONVERSION FRAMEWORK — 7 structure types:

     - **niche_problem**: Names a specific problem your ICP has. 80% problem, 20% solution hint. Drives DMs from people with that exact problem.
     - **case_study**: Real situation with metrics. Before/after, what changed, what worked. Requires a story from your story bank.
     - **contrarian**: Pushes against a common belief in your niche. Requires you to actually hold the contrarian position.
     - **framework**: A reusable model or way of thinking about a problem. 3-5 named parts. Saves-worthy.
     - **process**: How you actually do something step by step. Tactical, immediately useful.
     - **transformation**: A client (or you) went from one state to another. Specific delta. Story-driven.
     - **failure_learning**: Something you got wrong + what you learned. The most-saved post type when done with real specificity.

     TARGET MIX per 4 posts/week (rotate across month to hit monthly targets):
     - Niche problem posts: 1-2/week
     - Case studies with metrics: 0-1/week (target 2-3/month)
     - Contrarian takes with evidence: 0-1/week (target 2-3/month)
     - Industry-specific frameworks: 0-1/week (target 1-2/month)
     - Process breakdowns: 0-1/week (target 1-2/month)
     - Transformation stories: 0-1/week (target 1-2/month)
     - Failure + learning posts: 0-1/month

  5. Flag any topics that require a real story from you (mark as NEEDS_INPUT)
```

> **A note on terminology:** This workflow uses three categorization systems for content. Don't let them confuse you:
> - **Structure types** (above): how the post is built — niche_problem, case_study, contrarian, framework, process, transformation, failure_learning
> - **Hook styles** (rulebook §4.2): how the post opens — story / contrarian / number
> - **Closing types** (rulebook §4.1): how the post ends — Type A (question), Type B (incomplete statement), Type C (practical nudge)
>
> Your brand profile sets default hook and closing types per pillar. The workflow assigns the structure type per post. They compose: e.g., "a niche_problem post with a number hook and a Type A closing."

**Output:** Topic plan — 4 entries, each with:
```
{
  post_number: 1-4,
  week_number: N (1-4 in the month),
  pillar: "string",
  structure: "niche_problem | case_study | contrarian | framework | process | transformation | failure_learning",
  topic: "specific angle in one sentence",
  length_target: "short | medium | long",
  needs_input: true/false,
  story_prompt: "string (only if needs_input = true)",
  industry_context: "relevant current data point or trend, if applicable",
  scheduled_date: "YYYY-MM-DD",
  scheduled_day: "data-driven (Tue-Thu + optional as fallback)"
}
```

**Length target definitions:**
- **short** = 80-180 words. Punchy. One observation, one detail, one closing.
- **medium** = 200-300 words. Standard post length. Hook + body + closing.
- **long** = 300-400 words. Multi-part argument or framework with named parts.

**Gate:** Topic plan must have:
- At least 2 different pillars represented per week (track monthly: all pillars get minimum 3 posts)
- No more than 2 posts with the same structure in a single week
- No topic duplicating a post from the last 3 months
- NEEDS_INPUT posts have a specific story_prompt written
- **Length variety:** at least 1 post assigned `length_target: short` AND at least 1 post assigned `length_target: long`. This ensures the batch passes Step 6's length-ratio variety audit (shortest:longest ≥ 1.5x). Without explicit assignment up front, the natural spread is too tight.

---

## Step 3: Story Harvesting

**Input:** Topic plan entries where needs_input = true
**Action:** Generate prompts for you to answer

```
For each NEEDS_INPUT post:
  Write a specific, easy-to-answer prompt:

  FORMAT:
  "Post [number] is about [topic], framed as a [structure].
  Have you had a situation where [specific scenario related to the topic]?
  Give me 2-3 sentences — the basics of what happened. I'll shape it into a full post."

  DO NOT:
  - Ask open-ended "tell me a story" questions
  - Ask for more than 2-3 sentences
  - Ask about topics unrelated to the assigned pillar
```

**Output:** List of story prompts to send to you
**Gate:** Each prompt must reference the specific post number, topic, and structure. No generic prompts.

**HOLD:** Wait for your responses before generating NEEDS_INPUT posts. Generate all other posts in parallel.

---

## Step 4: Post Generation

**Input:** Topic plan + your voice profile + your story bank + industry research
**Action:** Generate each post one at a time

For each post, construct this brief before writing:

```
=== POST BRIEF ===
Post number: [from topic plan]
Pillar: [from topic plan]
Structure: [from topic plan]
Topic: [from topic plan]
Industry context: [from topic plan]
Writing methodology: [from your brand profile, if selected]
Your story: [from story bank / your response, if NEEDS_INPUT. NULL otherwise]

> **🤖 AI: pick the right voice settings block based on the user's brand profile version.**
>
> - **First-Run Mode (minimal brand profile):** Use **Block A** below. Two fields. Everything else is inferred from the reference samples. Do NOT try to populate the Returning Mode fields — they don't exist in the minimal template and trying to fill them will stall the workflow.
> - **Returning Mode (full brand profile):** Use **Block B** below. All seven fields. The full profile has them populated.

**Block A — First-Run Mode voice settings (minimal profile, 2 fields):**

```
Voice settings:
  Reference samples: [from minimal profile §5 — paste verbatim, the generator infers register and rhythm from these]
  Always avoid list: [from minimal profile §5d — extends the rulebook's banned vocabulary]
  // Formality, rhythm, em dash limit, hook style, and closing style are all
  // inferred from the reference samples in First-Run Mode. Do not stall trying
  // to fill them — they're not in the minimal template.
```

**Block B — Returning Mode voice settings (full profile, 7 fields):**

```
Voice settings (from full brand profile):
  Reference samples: [from §5c — paste verbatim]
  Always avoid list: [from §5d]
  Formality slider (1-10): [from §5a]
  Sentence rhythm: [from §5b — short / mixed / flowing]
  Em dash limit per post: [from §5e — calibrated to 0, 1, 2, or 3]
  Hook style: [default for this pillar from §6 — story / contrarian / number]
  Closing style: [default for this pillar from §6 — Type A / Type B / Type C]
```

Constraints:
  Target length: 300-350 words (vary across batch: some 80-150, some 300-400)
  First 210 characters: must hook. This is all the reader sees before "see more."
  Ground rules: no fabrication, no invented data, opinions/frameworks OK (rulebook §1)
  Banned vocabulary: full list from rulebook §2.2 + your "always avoid" list from brand profile §5d
  Em dashes: max [N] per post per your brand profile §5e calibration. Never as comma substitutes.

Variation seed (randomly assigned per post, ensures no two generations are identical):
  Hook angle: [from options: lead with problem / lead with story / lead with statistic / lead with question / lead with scene]
  Emotional register: [from options: measured / bold / reflective / urgent / curious]
  Length target: [from options: short (80-150 words) / medium (200-300 words) / long (300-400 words)]
  Evidence approach: [from options: single example deep / multiple examples brief / no example, pure opinion / data point + interpretation]
  Closing approach: [from options: sharp line / practical nudge / open question / trail off / call back to opening]
=== END BRIEF ===

**Rule: No two posts in the same batch may share the same combination of hook angle + emotional register + length target.** If you detect overlap, reseed the variation dimensions before generating.
```

**Write the post following the brief.**

Then immediately run:

---

## Step 5: Per-Post Quality Check

**Input:** Generated post + post brief
**Action:** Run every check. This is not optional. Every check must pass.

```
VOCABULARY CHECK:
  □ Scan for every word in the banned vocabulary list (rulebook Section 2)
  □ If ANY found → replace with plain alternative and re-check
  □ Result: PASS (0 banned words) or FAIL (list violations)

PUNCTUATION CHECK:
  □ Scan for em dashes (—)
  □ If used as comma substitute → replace with comma
  □ Dashes OK only for genuine interruptions/asides
  □ Result: PASS or FAIL

STRUCTURE CHECK:
  □ Compare this post's arc to the previous 3 generated posts
  □ If same arc (e.g., all follow problem → insight → resolution) → restructure
  □ Result: PASS or RESTRUCTURE

TRANSITION CHECK:
  □ Count paragraphs that open with a transition word (But, However, So, And, Yet, Here's the thing, The truth is, etc.)
  □ Calculate percentage: transitions / total paragraphs
  □ If >30% → remove transitions until <30%
  □ Per-brand override: if the brand profile §5d "Always allow" list (Returning Mode only) explicitly permits a specific transition word as part of the natural voice (e.g., "Here's the" appears in 3+ reference samples), allow up to 2 instances per post of that specific word without counting toward the 30% threshold. The override is per-word, not per-category.
  □ Result: PASS (≤30%) or FAIL (>30%, list which to remove)

VOICE CHECK:
  □ Diplomatic hedges present? ("I'm not saying X. I'm saying Y.") → remove
  □ "Most founders/people/teams" as opening frame? → rewrite from personal experience
  □ Synthetic enthusiasm? (exclamation points, "game-changer", "incredible") → tone down
  □ Over-explaining? (defining terms reader knows) → cut
  □ Constant qualification? ("While this is generally true...") → state the opinion
  □ Register consistent throughout? → introduce variation if too uniform
  □ Result: PASS or REWRITE (list specific issues)

SPECIFICITY CHECK:
  □ Is there at least one concrete detail? (real name, number, timeframe)
  □ If not → add from story bank OR flag for your input
  □ Can any adjective be replaced with a number? → replace
  □ Result: PASS or ADD_DETAIL

FABRICATION CHECK:
  □ Does any story, conversation, or scenario describe something that didn't happen?
  □ Does any stat or data point lack a real source?
  □ Does the post contain "illustrative specifics" (e.g., "last Monday it was X. The week before it was Y") that sound real but were invented for rhythm?
  □ The rule: if it sounds specific, it must BE specific. Either pull a real example from the story bank, or generalize the language ("some weeks it's a pricing decision, other weeks a contractor problem") so the reader knows it's a pattern, not a claim.
  □ If YES to any of the above → remove fabricated element, generalize the language, OR flag for your input
  □ This is a HARD FAIL. No exceptions.
  □ Result: PASS or HARD_FAIL

OPENING CHECK:
  □ Does the post start with "I" or "We"?
  □ If yes → consider rewriting to lead with the reader's situation or an observation
  □ Not a hard fail per post, but at the batch level: no more than 2 of 4 posts may open with "I" or "We". Track this as you generate the batch. If post 3 wants to open with "I" and posts 1 and 2 already do, rewrite this one's opening.
  □ Result: PASS or CONSIDER_REWRITE

CLOSING CHECK:
  □ Is there a neat two-word kicker? ("Start there." "The order matters.")
  □ If yes AND the previous 2 posts also had kickers → remove or change
  □ Engagement bait? ("Thoughts? 👇" "Agree?") → remove unless your closing style explicitly includes this
  □ Result: PASS or REWRITE_CLOSE

LINKEDIN-SPECIFIC CHECK:
  □ "That's not a [X]. That's a [Y]." construct (false opposition, rulebook §2.3)? → max 1 per post, never in consecutive posts
  □ 4+ consecutive one-sentence paragraphs (broetry, rulebook §2.3)? → break up with a multi-sentence paragraph
  □ Hook-plus-line-break formula used? → vary (sometimes 2 sentences before first break)
  □ Story that perfectly illustrates exactly one lesson with clean moral? → add messiness or ambiguity
  □ Result: PASS or FIX

HONEST LIMITATION CHECK:
  □ Is there at least one genuine qualification, limitation, or "this doesn't always apply" moment?
  □ Not a hedge. A real honest acknowledgment.
  □ Result: PASS or ADD_LIMITATION

VOICE MATCH CHECK:
  □ Read the post out loud in your voice
  □ Would you say this sentence to someone over coffee?
  □ Does any sentence feel "LinkedIn-y" or corporate?
  □ If yes → rewrite those sentences
  □ Result: PASS or REWRITE_VOICE

AI DETECTION CHECK (recommended, pre-publish):
  □ Run final post text through GPTZero, Copyleaks, or QuillBot AI Detector
  □ >60% AI score → rewrite flagged sentences (break rhythm, roughen transitions)
  □ <40% AI score → PASS
  □ This is a sanity check, not a hard gate. If the other gates pass but the detector flags, use judgment.
  □ Result: PASS or REWRITE_FLAGGED
```

**Output:** Post with all checks passed, or post returned to Step 4 for rewrite with specific issues listed.

**Gate:** ALL checks must PASS before the post enters the batch. A post with any FAIL or HARD_FAIL cannot proceed. AI Detection Check is recommended but not a hard gate.

---

## Step 5b: Independent Critic Review

**Role:** A separate agent (or a fresh instance) specialised in LinkedIn content strategy, B2B thought leadership, and the LinkedIn algorithm. NOT the agent that generated the posts. The critic loads the rulebook, your brand profile, and reviews with fresh eyes.

> **🤖 AI: how to actually run the critic depends on your runtime.** Pick the right path below based on what tools you have available. The full prompt template and routing rules are in `./CLAUDE.md` Step 6 — read that section before running this step.
>
> **Claude Code (you have the Agent tool — preferred):**
> Spawn a fresh `general-purpose` sub-agent via the Agent tool. The sub-agent starts with zero shared context, which is exactly what the critic needs. Pass it the absolute paths to the rulebook and the user's brand profile, plus the 4 generated posts inlined. The sub-agent runs the critic logic in isolation and returns structured PASS/REWORK verdicts. The full prompt template is in `./CLAUDE.md` Step 6. **This is the recommended path. The user doesn't have to do anything — the sub-agent handoff is automatic.**
>
> **Claude Desktop with file access (no Agent tool):**
> You can read files but you can't spawn a sub-agent. Tell the user: *"Open a new conversation in Claude Desktop, paste the prompt below, and copy the verdicts back here."* Then output the full critic prompt block from `./CLAUDE.md` Step 6 with the rulebook section, the brand profile, and the 4 posts inlined for the user to copy.
>
> **Claude.ai web / ChatGPT / Cursor chat / other chat-only runtimes:**
> Same as Claude Desktop above. Tell the user to open a new chat tab, paste the critic prompt block, and bring the verdicts back to the current conversation.
>
> **Skip mode (not recommended, only if user explicitly waives the critic):**
> Run Step 5 self-checks twice with a 30-minute gap between passes. Less effective but better than nothing. Document that the user opted out so they can decide whether to add Step 5b in future batches.

**Expertise required:** The critic must understand:
- What makes LinkedIn content convert (niche problem structure, hook mechanics, dwell time)
- How the LinkedIn algorithm distributes content (depth score, engagement signals, AI detection penalties)
- The difference between content that gets likes and content that gets DMs
- What authentic B2B thought leadership sounds like vs. AI-generated "LinkedIn bro" content
- How voice consistency builds trust over months of posting

**Purpose:** The generating agent has blind spots. It wrote the posts and will unconsciously defend its own choices. The critic has no attachment to the output and catches what the generator misses. The critic also brings strategic awareness: not just "is this well-written?" but "will this actually work on LinkedIn for your goals?"

**Input:** All posts that passed Step 5's self-checks
**Action:** Review every post against three lenses

```
LENS 1 — AI DETECTION (the human reader test)
For each post:
  □ Read the post cold. Does it feel like a real person wrote it, or does it feel "produced"?
  □ Flag specific sentences that sound AI-generated (quote the sentence)
  □ Check for patterns across posts: are multiple posts using the same rhythm, the same sentence construction, the same emotional arc?
  □ Check for residual banned vocabulary that the self-check missed
  □ Check for subtle AI patterns: overly balanced paragraphs, too-clean narrative structure, synthetic transitions
  □ Check for templating: does this post read like a rewrite of another post in the batch or from a previous month? Same shape, same rhythm, same landing? If yes, flag as TEMPLATED.
  □ Verdict per post: AUTHENTIC / NEEDS_REWORK (with specific lines flagged)

LENS 2 — VOICE MATCH (the "would you say this?" test)
For each post:
  □ Compare against the brand profile reference samples (§5c) — does the generated post sound like the same person who wrote those?
  □ Compare against the formality slider (§5a) and sentence rhythm (§5b) if set — Returning Mode only
  □ Compare against the brand-specific "always avoid" list (§5d) — flag any usage the universal rulebook missed
  □ Compare against your actual published posts (from Content Audit) — Returning Mode only
  □ Flag any sentence where the register shifts away from the reference samples
  □ Flag any opinion that feels stronger or weaker than the samples suggest
  □ Verdict per post: VOICE_MATCH / VOICE_DRIFT (with specific drift points)

LENS 3 — CONVERSION EFFECTIVENESS (the "will this work?" test)
For each post:
  □ Does the hook earn the "see more" click? (first 210 characters)
  □ Does the structure match its assigned conversion type? (e.g., a niche problem post should be 80% problem, 20% solution)
  □ Would your ICP self-identify with this post? (does it describe THEIR situation specifically?)
  □ Is there a reason to remember this post tomorrow? (one sharp insight, one surprising detail, one useful takeaway)
  □ Verdict per post: EFFECTIVE / WEAK (with specific weakness identified)
```

**Output format — the critic produces a review sheet:**

```
=== CRITIC REVIEW ===
Post [number]: [PASS / REWORK]
  AI Detection: [AUTHENTIC / NEEDS_REWORK]
    - [specific flagged sentences with explanation]
  Voice Match: [VOICE_MATCH / VOICE_DRIFT]
    - [specific drift points]
  Conversion: [EFFECTIVE / WEAK]
    - [specific weakness]
  Recommendation: [PASS / REWRITE lines X-Y / RESTRUCTURE / REPLACE TOPIC]
=== END REVIEW ===
```

**Loop logic:**
- Posts marked PASS proceed to Step 6 (Batch Review)
- Posts marked REWORK return to Step 4 (Post Generation) with the critic's specific feedback attached as the rewrite brief
- The generator must address every flagged issue, not just acknowledge them
- Maximum 3 loop iterations per post. If a post fails 3 times, escalate to human review.

**Gate:** Every post must receive PASS from the critic before entering the batch. The critic does not rewrite — they only flag. The generator rewrites.

---

## Step 6: Batch Review

**Input:** All 4 posts that passed Step 5
**Action:** Review the weekly batch as a whole (track monthly variety across weeks)

```
VARIETY AUDIT (within this week's 4 posts):
  □ Count distinct hook types used → minimum 2 different types
  □ Count distinct closing types used → minimum 2 different types
  □ Count posts per structure type → no structure used >2 times
  □ Count posts per pillar → at least 2 different pillars
  □ Count "X-not-Y" / false-opposition constructs across all 4 posts → maximum 1 per batch (rulebook §2.3 allows 1 per post; at the batch level, more than 1 across 4 posts signals templating)
  □ Count "Not because X. Because Y." negation-reframe constructs across all 4 posts → maximum 1 per batch (rulebook §2.8 allows 1 per post; cap the batch the same way)
  □ Count "Here's the thing" / "Here's what" / "The truth is" transition openers across all 4 posts → maximum 2 per batch (these are voice-defensible per-post but cluster as templating across a batch)
  □ Measure post lengths → shortest and longest differ by at least 1.5x
  □ Count posts following problem → insight → resolution arc → max 2 of 4

SEQUENCE CHECK (within this week):
  □ No 2 consecutive posts share the same:
    - Structure
    - Pillar (exceptions OK if natural)
    - Hook type
    - Emotional tone
  □ Is there a sense of rhythm across the week?
  □ Would a follower reading all 4 posts in one week feel range and personality, not repetition?

CROSS-WEEK SEQUENCE CHECK (Returning Mode only — skip on first batch):
  □ Compare this week's batch against the previous 3 weeks of generated batches
  □ Same structure types repeating week over week? → vary
  □ Same pillar dominating multiple weeks? → rebalance
  □ Same hook angle 3 weeks in a row? → force a different opening pattern

MEASUREMENT:
  □ Calculate sentence length standard deviation across all posts → must be >5 words
  □ Calculate overall transition frequency → must be <30%
  □ Confirm banned vocabulary count = 0 across entire batch
  □ Confirm all NEEDS_INPUT posts have real stories (no fabrication)

DEDUPLICATION:
  □ Compare every post's core message against every other post in the batch
  □ Compare every post against your Content Audit (last 3 months of published posts)
  □ If any overlap found → reframe the angle or swap the topic
```

**Output:** Final batch of 4 posts, all passing variety and measurement thresholds

**Monthly tracking:** After week 4, run a cumulative variety audit across all 16 posts generated that month. If monthly variety thresholds fail (e.g., a pillar was underrepresented), adjust week 1 of the next month's plan to compensate.

**Gate:** If any variety metric fails, return to Step 4 to regenerate the weakest posts. Do not force a failing batch through.

---

## Step 7: Package and Deliver

**Input:** Final approved batch
**Action:** Prepare for scheduling and your review

```
For each post, produce:
{
  post_number: 1-4,
  week_number: N,
  scheduled_date: "YYYY-MM-DD",
  scheduled_day: "data-driven (Tue-Thu + optional as fallback)",
  scheduled_time: "HH:MM" (8:00 AM in your target audience's primary timezone, NOT yours),
  pillar: "string",
  structure: "string",
  topic: "one-sentence summary",
  full_text: "the complete post text",
  image_prompt: "prompt for your image generator using your brand visual style" (if applicable),
  hashtags: ["3-4 specific, relevant hashtags"],
  hashtag_placement: "body_end" (if follower count <5K) | "first_comment" (if >5K),
  needs_story: false (all should be false at this point),
  word_count: number,
  character_count: number,
  hook_type: "scene-setting | story-opener | bold-claim | question | etc.",
  closing_type: "sharp-line | practical-nudge | no-close | question | etc.",
  quality_checks_passed: ["vocabulary", "structure", "voice", "fabrication", "specificity", "linkedin", "limitation"]
}

Generate a weekly preview summary (informational, not a gate):
  Body:
    - Hook preview (first 120 chars) of each post scheduled that week
    - Topic Attribution: "Based on: [Pillar] · Audience pain point: [Y] · Trending in [Z]"
    - You approve, or request edits, or silence means autopilot.
```

**Output:** Complete content package ready for scheduling

---

## Step 8: Schedule

**Input:** Content package from Step 7
**Action:** Schedule all posts using LinkedIn's native scheduler (default), or via API if you have approved Marketing Developer Platform access.

> **Reality check on scheduling:** LinkedIn's posting API requires Marketing Developer Platform approval that takes weeks to obtain and is not granted to individuals. Browser automation against LinkedIn risks account suspension. **For 95% of users, LinkedIn's native post scheduler in the post composer is the only realistic path.** The workflow is designed to produce drafts you publish manually — that's a feature, not a limitation. Manual scheduling takes ~5 minutes for a week of 4 posts.

```
SCHEDULING LOGIC:

1. Determine publishing time:
   - Look up your target audience's primary geography (from your brand profile §9)
   - Set time to 8:00 AM in that timezone (see rulebook §4.7 for the per-region table)
   - If your audience spans multiple timezones, use the largest cluster
   - Your own timezone is irrelevant — posts publish in the audience's timezone

2. Determine publishing days:
   - Default per rulebook §4.7: data-driven day selection, with Tue-Thu + optional as fallback
   - Once you have 30+ days of data, shift to your audience's actual peak engagement days
   - Weekend posts disabled by default unless your engagement data shows weekend performance above weekday average

3. For each post:
   a. Open LinkedIn → Start a post → paste the post text
   b. Click the clock icon → set the scheduled date and time
   c. If image_prompt exists → generate the image → attach before scheduling
   d. Schedule the post
   e. (Optional) Schedule the first comment as a follow-up reminder for yourself, since LinkedIn's native scheduler does not support scheduling comments

4. After all scheduled:
   - Review the batch one last time before they go live
   - You can still edit or cancel any post up until its scheduled time via LinkedIn's "Scheduled posts" view
```

**Output:** All posts scheduled. Autopilot active.

> **For users with approved LinkedIn API access:** You can automate scheduling through the Marketing Developer Platform's posts endpoint. The `_workflow_outputs/` package format from Step 7 is structured to feed any scheduler. Roll your own integration — we don't ship one because the API approval gate makes it irrelevant for solo users.

---

## Error Handling

| Error | Action |
|-------|--------|
| First run, no audit or research file | Switch to **First-Run Mode** (top of this workflow). Skip Step 1, run Step 2 from pillars only, treat Step 6 cross-week check as informational. |
| Industry research is >30 days old (Returning Mode) | STOP. Run research refresh. Resume at Step 1. |
| Content audit missing recent posts (Returning Mode) | STOP. Pull latest posts from LinkedIn → Profile → Analytics → Posts. Resume at Step 1. |
| Brand profile missing reference voice samples | HARD STOP. Voice samples (brand profile §5c) are the one field that cannot be skipped. The workflow will refuse to generate without them. |
| No response to story prompts after 48 hours | Generate remaining autonomous posts. Reschedule NEEDS_INPUT posts to later in the month. |
| Post fails quality check 3 times | Flag for manual review. Do not force it through. |
| Batch fails variety audit | Identify the weakest posts (lowest variety contribution). Regenerate those only. Re-run batch review. |
| Scheduling fails | Use LinkedIn's native scheduler manually. The API path is not the recommended default for solo users — see Step 8. |
| You pause autopilot mid-batch | Respect immediately. Hold all remaining scheduled posts. Resume only on explicit instruction. |

---

## Workflow Metadata

| Field | Value |
|-------|-------|
| **Trigger:** | Weekly. Monthly review at the end of each month. |
| **Duration:** | ~15 minutes agent time per weekly batch (excluding your response wait) |
| **Agents authorised:** | Any agent with this skill and a brand profile loaded |
| **Human touchpoints:** | Your story responses (Step 3), your weekly batch review (optional) |
| **Quality standard:** | 100% of posts must pass all Step 5 checks. 100% of batch must pass Step 6 variety audit. |

---

## Version History

| Date | Version | Changes |
|------|---------|---------|
| 2026-04-07 | 1.0 | Initial public release. 8-step workflow with per-post quality checks, independent critic review, batch variety audit, error handling. Adapted from an internal workflow refined over multiple months of real use. |
