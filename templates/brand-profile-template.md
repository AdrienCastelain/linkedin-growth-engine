# Brand Profile — [FILL IN: Your Name or Brand Name]

> **What this is:** The per-brand customization layer for the LinkedIn Growth Engine. The rulebook handles universal content rules. This profile handles everything that varies across brands: your positioning, your voice, your pillars, your stories.
>
> **How to use it:** Copy this file to `_user/my-brand-profile.md` in your working directory and fill in every `[FILL IN: ...]` block. Create the `_user/` directory first if it doesn't exist (`mkdir -p _user/`). Don't skip fields — the workflow will tell you when something's missing. The example at `./example-brand-profile.md` shows what a finished profile looks like.
>
> **Or skip the manual copy:** open Claude pointed at this folder and type "hi". The bootstrap will walk you through filling in the brand profile interactively and save the file to `_user/` for you. See [`../CLAUDE.md`](../CLAUDE.md).
>
> **Time to fill:** 20-30 minutes if you already know your positioning. Longer if you're figuring it out as you go — and that's a feature, not a bug. The template forces the strategic thinking that makes good content possible.

---

## 1. Positioning

One sentence. Who you help, what you help them do, what outcome they get.

> [FILL IN: I help [WHO] do [WHAT] so they can [OUTCOME].]

**Quality test:** Read this out loud. If it sounds like a job title or a list of services, rewrite. If your ICP would nod and say "that's exactly what I need," it works.

---

## 2. Ideal Customer Profile (ICP)

Who you're writing for. Not a persona, not a buyer journey — just the specific kind of person who should read your content and feel seen.

- **Role:** [FILL IN: e.g., "Solo founder, pre-Series A SaaS"]
- **Company stage:** [FILL IN: e.g., "0-50 employees, $0-3M ARR"]
- **Primary pain point:** [FILL IN: The one thing they wake up worried about that you can help with]
- **Where they are right now:** [FILL IN: What they're trying and failing at — the specific situation that makes your help relevant]

---

## 3. LinkedIn Goal

Pick exactly ONE. This drives closing types, first comment types, reply guidance, and what success looks like. You can change it later, but you can't have two at once.

Options (from the rulebook, Section 4.1):
- [ ] Inbound leads
- [ ] Thought leadership
- [ ] Grow audience
- [ ] Attract investment
- [ ] Employer brand
- [ ] Speaking / media
- [ ] Launch support
- [ ] Community growth
- [ ] Custom goal: [FILL IN: describe]

**Selected:** [FILL IN]

**Why this goal right now:** [FILL IN: One sentence — what's happening in your business that makes this the right goal for the next 3-6 months. This is for you, not the algorithm. It keeps you honest if you're tempted to drift.]

---

## 4. Content Pillars

3-4 topics you can credibly talk about for the next 12 months without running out of things to say. Each pillar gets a target weight (must add to 100%).

| # | Pillar | One-line description | Target weight |
|---|--------|---------------------|---------------|
| 1 | [FILL IN] | [FILL IN: What this pillar is about and why you can speak to it] | [FILL IN: %] |
| 2 | [FILL IN] | [FILL IN] | [FILL IN: %] |
| 3 | [FILL IN] | [FILL IN] | [FILL IN: %] |
| 4 | [FILL IN — optional] | [FILL IN] | [FILL IN: %] |

**Default weights** (from the rulebook, Section 4.8) if you don't have a strong opinion:
- Expertise / Authority: 40%
- Personal story / Journey: 30%
- Engagement / Conversation: 20%
- Promotional / CTA: 10%

**Quality test:** Could you write 10 posts about each pillar from your own experience without making anything up? If not, the pillar is too narrow. Either widen it or replace it.

---

## 5. Voice Profile

The hardest section to fill in. Take the time. Voice is what makes the difference between content that sounds like you and content that sounds like AI.

### 5a. Formality slider (1-10)

1 = "yo what's up" / 10 = formal academic prose

**Your number:** [FILL IN]

**Where you sit on the spectrum:** [FILL IN: One sentence describing your natural register. Example: "Direct and conversational, but I use precise language when I'm making a technical point. I don't swear in posts but I do use 'honestly' and 'look' as conversational markers."]

### 5b. Sentence rhythm

Pick one:
- [ ] **Short** — Mostly fragments and short sentences. Punchy. Almost staccato.
- [ ] **Mixed** — Variation between short and long sentences. Most natural for most people.
- [ ] **Flowing** — Longer, more complex sentences with subordinate clauses and natural cadence.

**Selected:** [FILL IN]

### 5c. Reference samples

**Paste 5 things you've actually written.** They don't have to be LinkedIn posts. Emails, Slack messages, blog post excerpts, podcast transcripts — anything you wrote in your natural voice. Aim for 100-300 words each.

These are the most important field in this entire document. The system uses these to calibrate everything: word choice, em dash frequency, paragraph rhythm, contractions, formality, signature phrases.

**If you only have 2-3 samples, that's the priority gap to fix before generating content.** Bad samples = bad voice match = generic AI output.

---

**Sample 1:**
> [FILL IN]

**Sample 2:**
> [FILL IN]

**Sample 3:**
> [FILL IN]

**Sample 4:**
> [FILL IN]

**Sample 5:**
> [FILL IN]

---

### 5d. "Always avoid" word list

Words you would never naturally use. The rulebook already bans the obvious AI tells (delve, leverage, harness, etc. — see Section 2.2). Add anything else that's specific to you.

Example: "I never say 'journey,' 'unpack,' 'circle back,' or 'let's dive in.'"

> **Duplicates are fine.** Listing a rulebook-banned word here is harmless duplication, not wasted effort. The point is to capture anything that flinches when you read it. Don't worry about overlap with §2.2.

- [FILL IN]
- [FILL IN]
- [FILL IN]
- [FILL IN]
- [FILL IN]

### 5d-bis. "Always allow" word list (optional, advanced)

Words or phrases the universal rulebook treats as suspect (transition openers, "Here's the thing" patterns, soft hedges) that are *natural* to your voice and appear in 3+ of your reference samples. The workflow's transition check (Step 5) will give you a per-word override of up to 2 instances per post for anything on this list.

**Don't fill this in until your second or third batch.** First-Run Mode users should leave this empty. The override exists for users who notice the universal rules conflicting with their actual register after a few batches.

Example for a writer who naturally uses "honestly" and "look": list `honestly` and `look` here, with the note "appears in samples 1, 3, 4 — natural to my register, not a hedge."

- [FILL IN — leave empty for first batch]

### 5e. Em dash calibration

Count em dashes (—) in your 5 reference samples above. Average per 100 words.

- 0 per sample → enforce zero em dashes in generated content
- 1-2 per sample → default (max 2 per post)
- 3+ per sample → allow up to 3 per post

**Your average:** [FILL IN]
**Allowed per post:** [FILL IN: 0, 2, or 3]

---

## 6. Hook & Closing Preferences

Default styles per pillar. The system will override when a specific topic calls for something different, but these set the baseline.

**Hook styles** (from the rulebook, Section 4.2):
- **Story** — start with a specific scene from your work
- **Contrarian** — start with a position that pushes against common wisdom
- **Number** — start with a surprising statistic or count from your own data

**Closing types** (from the rulebook, Section 4.1):
- **Type A** — genuine question (drives comments)
- **Type B** — incomplete statement (invites disagreement, drives shares)
- **Type C** — practical nudge (drives saves, works for how-to posts)

| Pillar | Default hook style | Default closing type |
|--------|-------------------|---------------------|
| [Pillar 1 from above] | [FILL IN] | [FILL IN] |
| [Pillar 2] | [FILL IN] | [FILL IN] |
| [Pillar 3] | [FILL IN] | [FILL IN] |
| [Pillar 4] | [FILL IN] | [FILL IN] |

---

## 7. Story Bank

Real situations from your work that you can pull from when writing posts. You don't need to write the post — just capture enough that you'll remember the situation when you see it later.

**Format per story:**
- **Title:** Short label so you can find it later
- **Pillar:** Which content pillar this fits
- **Theme:** Failure / Success / Surprise / Lesson
- **2-3 sentence summary:** What happened, what was at stake, what was learned
- **Specific details:** Numbers, names (if shareable), timeframes — the things that pass the Colleague Test

Aim for **5-10 stories** to start. Add more as they happen.

---

**Story 1:**
- **Title:** [FILL IN]
- **Pillar:** [FILL IN]
- **Theme:** [FILL IN]
- **Summary:** [FILL IN]
- **Details:** [FILL IN]

**Story 2:**
- **Title:** [FILL IN]
- **Pillar:** [FILL IN]
- **Theme:** [FILL IN]
- **Summary:** [FILL IN]
- **Details:** [FILL IN]

**Story 3:**
- **Title:** [FILL IN]
- **Pillar:** [FILL IN]
- **Theme:** [FILL IN]
- **Summary:** [FILL IN]
- **Details:** [FILL IN]

**Story 4:**
- **Title:** [FILL IN]
- **Pillar:** [FILL IN]
- **Theme:** [FILL IN]
- **Summary:** [FILL IN]
- **Details:** [FILL IN]

**Story 5:**
- **Title:** [FILL IN]
- **Pillar:** [FILL IN]
- **Theme:** [FILL IN]
- **Summary:** [FILL IN]
- **Details:** [FILL IN]

*(Add more as needed.)*

---

## 8. Benchmark Accounts

5-10 LinkedIn profiles you learn from, compete with, or want to learn from. The skill uses these for competitive intelligence (Module 10) and reshare scouting (Module 11).

**Selection criteria** (from the rulebook, Section 10.1):
- Same industry or adjacent
- Mix of follower tiers: 2-3 peers (5K-50K), 2-3 aspirational (50K-500K), 1-2 pattern sources (500K+)
- Active posters (at least 3 posts/week)

| # | Name / Handle | Follower count (rough) | Why they're on this list |
|---|---------------|------------------------|--------------------------|
| 1 | [FILL IN] | [FILL IN] | [FILL IN] |
| 2 | [FILL IN] | [FILL IN] | [FILL IN] |
| 3 | [FILL IN] | [FILL IN] | [FILL IN] |
| 4 | [FILL IN] | [FILL IN] | [FILL IN] |
| 5 | [FILL IN] | [FILL IN] | [FILL IN] |

*(Add up to 10. Refresh quarterly.)*

---

## 9. Target Market

Where your audience lives. This loads the right cultural profile from Module 19.

Pick one (or "global mix" if multi-region):
- [ ] US (default)
- [ ] UK / EU
- [ ] Australia / New Zealand (ANZ)
- [ ] APAC (Singapore, HK, Japan, Korea)
- [ ] Global mix

**Selected:** [FILL IN]

**Why it matters:** Cultural profiles override the default US tone. ANZ posts, for example, need to pass the Tall Poppy Test before publishing. Get this wrong and your content will land flat in your actual audience's market.

---

## 10. Include / Avoid Topics

**Topics you WILL talk about** (your declared lane — anything outside this is off-pillar):
- [FILL IN]
- [FILL IN]
- [FILL IN]

**Topics you will NOT talk about** (politics, religion, competitors by name, anything that breaks your positioning):
- [FILL IN]
- [FILL IN]
- [FILL IN]

---

## Quality Check Before You Save

Before you save and start using this profile, run through this list:

- [ ] Section 1 (Positioning) — passes the "sounds like a job title" test
- [ ] Section 2 (ICP) — specific enough that you can picture one real person
- [ ] Section 3 (Goal) — exactly one selected, with a "why now" reason
- [ ] Section 4 (Pillars) — weights add to 100%, each pillar passes the "10 posts" test
- [ ] Section 5 (Voice) — at least 5 reference samples pasted, formality and rhythm picked, em dash calibrated
- [ ] Section 6 (Hook/Closing) — defaults set per pillar
- [ ] Section 7 (Story Bank) — at least 5 stories with specific details
- [ ] Section 8 (Benchmarks) — at least 5 accounts across follower tiers
- [ ] Section 9 (Market) — picked, cultural profile loaded if non-US
- [ ] Section 10 (Topics) — both lists filled in

**If any section is incomplete, the workflow's first step (Performance Review → Topic Selection) will flag it as a gap.** Don't skip fields hoping to fix them later. Fill in what you can, mark the rest as `[GAP — to fix by DATE]`, and address them within your first month.
