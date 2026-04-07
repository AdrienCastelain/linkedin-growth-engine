# Brand Profile (Minimal) — [FILL IN: Your Name or Brand Name]

> **What this is:** The 15-minute version of the brand profile. Just enough to run your first content batch and feel a real result. You'll expand into the [full template](./brand-profile-template.md) after you've shipped your first week.
>
> **Why minimal:** The full profile is 10 sections and ~30 minutes. That's the right amount for someone running this seriously. But it's the wrong amount for someone trying it for the first time. You don't need a story bank, benchmark accounts, or pillar weights to write your first post — you need positioning, ICP, voice, and a goal. Start here. Expand later.
>
> **What you'll skip for now:** Story bank (Section 7 of full template), benchmark accounts (Section 8), include/avoid topics (Section 10), hook & closing preferences per pillar (Section 6), and the content audit + industry research templates. The workflow will run in "First-Run Mode" without these.
>
> **Time to fill:** 15-20 minutes. Set a timer.

---

## 1. Positioning

One sentence. Who you help, what you help them do, what outcome they get.

> [FILL IN: I help [WHO] do [WHAT] so they can [OUTCOME].]

**Quality test:** Read this out loud. If it sounds like a job title or a list of services, rewrite. If your ICP would nod and say "that's exactly what I need," it works.

---

## 2. Ideal Customer Profile (ICP)

In one sentence, picture the person whose desk you want to land on.

> [FILL IN: Role + company stage + the specific thing they're stuck on. Example: "Solo founder, pre-Series A SaaS, can't tell which growth channel is actually working."]

**Why this matters:** the workflow's Step 5b critic checks "would your ICP self-identify with this post?" Without an ICP on record, the critic has to guess — and it usually guesses too generic. 60 seconds here saves the conversion check downstream.

---

## 3. LinkedIn Goal

Pick exactly ONE. This drives closing types, first comment types, and what success looks like.

- [ ] Inbound leads
- [ ] Thought leadership
- [ ] Grow audience
- [ ] Attract investment
- [ ] Employer brand
- [ ] Speaking / media
- [ ] Launch support
- [ ] Community growth

**Selected:** [FILL IN]

---

## 4. Content Pillars

3-4 topics you can credibly talk about for the next 12 months. Skip the weights for now — the workflow will use defaults (40/30/20/10) until you tune them.

| # | Pillar | One-line description |
|---|--------|---------------------|
| 1 | [FILL IN] | [FILL IN] |
| 2 | [FILL IN] | [FILL IN] |
| 3 | [FILL IN] | [FILL IN] |
| 4 | [FILL IN — optional] | [FILL IN] |

**Quality test:** Could you write 10 posts about each pillar from your own experience without making anything up? If not, the pillar is too narrow. Either widen it or replace it.

---

## 5. Voice Profile

The most important section. Skip the slider and the rhythm picker for now — the workflow will infer them from your reference samples.

### Reference samples

**Paste 5 things you've actually written.** Emails, Slack messages, blog post excerpts, podcast transcripts — anything you wrote in your natural voice. Aim for 100-300 words each.

These calibrate the entire system. If you only paste 2-3, the voice match will drift toward generic. If you skip this section, the workflow will refuse to generate. **This is the one section you cannot skip.**

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

### Always avoid

3-5 words or phrases you would never naturally use. The rulebook already bans the obvious AI tells (delve, leverage, harness, etc. — see rulebook §2.2 for the full list). Add anything specific to you.

> **Duplicates are fine.** If you instinctively write "leverage" on this list, leave it. Listing a rulebook-banned word here is harmless duplication, not wasted effort. The point is: list anything that flinches when you read it. Don't worry about overlap.

- [FILL IN]
- [FILL IN]
- [FILL IN]

---

## Done. Now run the workflow.

That's it for the minimal version. Save this file as `_user/my-brand-profile.md` in your working directory (create the `_user/` folder first with `mkdir -p _user/` if it doesn't exist), then:

1. Open [`../CONTENT-GENERATION-WORKFLOW.md`](../CONTENT-GENERATION-WORKFLOW.md)
2. Run it in **First-Run Mode** (the workflow will detect the missing audit and research and skip Step 1)
3. You'll have 4 draft posts in 30-45 minutes

**Or skip all of this:** open Claude pointed at this folder and type "hi". The bootstrap will detect that you have no brand profile yet, walk you through onboarding, save the file for you, and run the workflow automatically. See [`../CLAUDE.md`](../CLAUDE.md).

After you've published your first week and seen the system work, come back and expand into the [full brand profile template](./brand-profile-template.md). Add a story bank, benchmark accounts, and the topics you'll never touch. The full template is for users who already believe in the system. The minimal one is for users who haven't seen it work yet.

---

## What you're missing by using the minimal version

Honest list — so you know what you're trading away for the 15-minute setup:

- **No story bank.** The workflow will prompt you for a real story whenever a post needs one. Slower, but works.
- **No benchmark accounts.** The competitive intelligence module (10) and reshare scout (11) won't have inputs. Skip these modules until you upgrade.
- **No pillar weights.** Defaults will be used (40% expertise, 30% personal story, 20% engagement, 10% promotional). Tune later.
- **No hook/closing preferences per pillar.** The workflow will pick defaults and ask you to confirm.
- **No "topics I won't talk about" list.** The off-pillar gate (Gate 9) will be more permissive. Watch your batches for drift.
- **No detailed ICP profile** (the minimal one-line ICP above is enough for First-Run Mode, but the full template's 4-bullet ICP — role, stage, pain point, current state — gives the critic sharper conversion signal).

You can add any of these incrementally. The full template at [`./brand-profile-template.md`](./brand-profile-template.md) is the destination. This file is the runway.
