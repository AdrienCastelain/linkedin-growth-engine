# Post 3 — Founder-led marketing isn't 3 posts a week

**Pillar:** Founder-led marketing
**Structure:** contrarian
**Hook style:** Contrarian
**Closing type:** Type A — genuine question
**Length:** 248 words
**Scheduled:** Week 1, Thursday, 8:00 AM ET

---

## The post (as it would publish)

> Most "founder-led marketing" advice is wrong about which part the founder has to lead.
>
> The dominant version: founders should post on LinkedIn three times a week. Build the personal brand. Be visible. The founder is the channel.
>
> That's a tactic. It's not what founder-led marketing actually is.
>
> Founder-led marketing means the founder is the source of truth for what the product does, who it's for, and why it matters. Everything the company says publicly traces back to that source. The CEO writes the homepage headline. The CEO records the demo video. The CEO answers the first 100 sales calls. The CEO writes the first 50 blog posts.
>
> Once those artifacts exist, you can hand them to a marketer and they have something to scale. Without them, every marketer you hire reinvents the company's story from scratch in their own voice. That's why the first marketing hire so often fails.
>
> The LinkedIn posts are downstream. They're optional. A founder who writes one good homepage and ten clarifying sales emails has done more founder-led marketing than a founder who posts three times a week and lets a contractor write the homepage.
>
> The question I'd push back on with anyone selling "founder content" packages right now: what artifacts is the founder actually going to make this quarter that everything else points back to?

---

## First comment

> Worth saying out loud: this isn't an argument against founders posting. I'm arguing for the right sequence. Write the homepage and the demo first. Then the posts will be easy because they have something to point at. Founders who try to post first and figure out positioning later are working in the wrong order.

---

## Reply template (for substantive comments)

> Yeah and the worst version is when a founder hires a content agency before the homepage is sharp. The agency produces "thought leadership" that doesn't tie back to anything the company actually sells, the founder feels productive, the leads don't materialize, and six months later they conclude that LinkedIn doesn't work. LinkedIn worked. The strategy was inverted.

---

## Step 5 quality check results

| Check | Result | Notes |
|-------|--------|-------|
| Vocabulary | PASS | 0 banned words. "Source of truth" is borderline jargon but it's in Alex's reference samples (Sample 4) so it's allowed |
| Punctuation | PASS | 0 em dashes |
| Structure | PASS | Different from Posts 1 and 2 (contrarian-led, not number or story) |
| Transitions | PASS | 8% (one "Once those artifacts exist...") |
| Voice | PASS | Strong opinion, no diplomatic hedge, no "most founders" generic frame |
| Specificity | PASS | "first 100 sales calls," "first 50 blog posts," "ten clarifying sales emails," "this quarter" |
| Fabrication | PASS | Sample 4 from brand profile §5c is the source — verbatim sentences ported with light editing |
| Opening | PASS | "Most 'founder-led marketing' advice is wrong" — observation, not "I" |
| Closing | PASS | Type A genuine question. Specific enough that a real founder can answer in 2-3 sentences. |
| LinkedIn-specific | PASS | One false-opposition use ("That's a tactic. It's not what founder-led marketing actually is.") which is allowed once per post |
| Honest limitation | PASS | First comment carries it: "this isn't an argument against founders posting. I'm arguing for the right sequence." |
| Voice match | PASS | Mixed rhythm, opinionated, no hedge |
| AI detection (3-detector cross-check) | **WARNING — single detector outlier** | GPTZero: **100% AI / "highly confident AI generated"** • QuillBot: **0% AI / 100% Human** • Copyleaks: **0% AI / "No AI Content Found"** • Cross-detector verdict per Gate 8b: WARNING (1 of 3 detectors flags with high confidence — does not meet the FAIL threshold of 2+ detector consensus, but the GPTZero score is the strongest single-detector signal in the entire example batch). See "What this post demonstrates" below for the interpretation. |

---

## Step 5b critic review notes

```
=== CRITIC REVIEW ===
Post 3: PASS (after one rewrite loop)

  Round 1 — flagged:
    - Original draft closed with "Stop posting. Start writing." 
      → CRITIC FLAG: Two-word kicker (rulebook §2.8 polished parallel closings). Also, this isn't what Alex is actually arguing — it's a louder version that misrepresents her position. She's not against posting. She's against posting *first*.
    - Original draft used "playbook" once: "the founder content playbook is wrong about which artifacts come first."
      → CRITIC FLAG: "playbook" is on Alex's "always avoid" list (brand profile §5d).
  
  Round 1 — recommendation: REWRITE closing (replace kicker with a Type A question that pushes against the package-sellers explicitly), REPLACE "playbook" with another word
  
  Round 2 — re-evaluation:
    AI Detection: AUTHENTIC by 2 of 3 detectors (QuillBot, Copyleaks). GPTZero outlier flag noted — see post documentation.
    Voice Match: VOICE_MATCH
      - The reply template's "the strategy was inverted" landing is voice-consistent
      - The first comment as nuance carrier is the right move — keeps the post pointed without becoming a strawman
    Conversion: EFFECTIVE
      - First 210 chars: "Most 'founder-led marketing' advice is wrong about which part the founder has to lead. The dominant version: founders should post on LinkedIn three times a week. Build the personal brand. Be visible." (~196 chars — sets up the contrarian frame without resolving it)
      - This is a debate-invitation post and the "I'd push back on anyone selling 'founder content' packages" phrasing will likely draw comments from people who sell those packages. That's the engagement mechanism for thought-leadership goal.
      - Note: Alex's actual goal is inbound leads, not thought leadership. This post will work for both because it identifies a problem her ICP (founders) is actively spending money on the wrong solution to.
    Recommendation: PASS with note about GPTZero outlier
=== END REVIEW ===
```

---

## What this post demonstrates

**The strongest single-detector outlier in the example batch.** GPTZero classifies this post at 100% AI with high confidence. QuillBot and Copyleaks both classify it at 100% human. Per the rulebook's cross-detector consensus rule (Gate 8b), this is a **WARNING**, not a FAIL — one detector flagging high confidence does not override two detectors flagging zero. The post is publishable for the typical LinkedIn audience because LinkedIn's algorithm doesn't run GPTZero, and human readers are the actual audience for the post.

**Why GPTZero flags this post specifically.** The structural patterns the rulebook §2.9 catalogues (parallel anaphora in "The CEO writes... The CEO records... The CEO answers... The CEO writes...", abstract argumentation about "the dominant version", definitional argumentation in "Founder-led marketing means...") are exactly the patterns GPTZero is trained to flag. GPTZero was built and benchmarked for academic integrity — its training data weights heavily toward catching student essays, and the structural features it learned to recognize overlap with well-formed marketing rhetoric. That's why it over-flags well-structured marketing copy.

**Why the other two detectors don't flag it.** QuillBot is trained more leniently on assistive editing tools and is less aggressive on rhetorical structure. Copyleaks weights linguistic and frequency patterns more heavily than structural ones. Neither sees this post as AI.

**Why this post stays in the example batch.** It demonstrates the cross-detector pattern users will actually encounter. Real users running this workflow will hit GPTZero outliers regularly, especially on contrarian and framework posts. The example batch is more honest with this post in it (showing the WARNING case) than without it (showing only clean PASS cases that misrepresent the system's typical output). See `docs/troubleshooting.md` for what to do when you hit a GPTZero WARNING — short answer: review the flagged sentences, consider revising them, but don't auto-rewrite the post unless your specific audience runs strict detection.

**A user choosing to rewrite anyway** would target the patterns rulebook §2.9 catalogues: replace the parallel anaphora with varied sentence openings, replace the definitional argumentation with a specific scenario, anchor abstract claims in real client examples. This is good craft regardless of whether it changes the GPTZero score.
