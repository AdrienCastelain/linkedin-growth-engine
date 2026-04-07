# Module 03: Quality Gates

**Source of truth:** `../rulebook/linkedin-growth-engine-rulebook.md` — Section 3
**Load when:** Validating posts before scheduling

## Quick Reference

- **9 gates total.** Per-post gates (1-3, 5-6, 8) run on each post. Batch-level gates (4, 7, 9) run across the batch.
- **Gate 1 (Fabrication):** Flag any quoted dialogue, specific people/meetings/events, statistics, or "I was on a call..." unless you provided it.
- **Gate 2 (Anti-Pattern):** Scan for Tier 1/2 banned words, banned openers, broetry, banned CTAs, rocket emoji, em dash excess.
- **Gate 3 (Voice Match):** Formality, hook style, closing style, sentence rhythm must match your profile. "Could 100 other people have written this?" test.
- **Gate 5 (Algorithm):** No third-party links in body (25-40% penalty). Hashtags: 0-2 in body, 2-4 in first comment, never >5 total. Min 50 words. Flag engagement bait.
- **Gate 6 (Engagement Architecture):** Must have closing (Type A/B/C), first ~210 chars must create open loop, min 150 words, first comment required, 1 reply template required.
- **Gate 8 (Specificity):** Must score 2 of 3: proper noun, specific number with context, timeframe/temporal marker.
- **Gate 8b (AI Detection):** Run through external detector pre-publish. >60% AI score = rewrite. Not required for comments/reshares.
- **Gate 9 (Topic Consistency):** Flag off-pillar posts, hard fail if >20% off-pillar for the month, flag same sub-topic 2+ times in 14 days.
- **Batch gates (4, 7):** Vary hook patterns, pillar distribution across weeks, closing types, post lengths, formats.

**Full rules:** For complete rules, read the Rulebook, Section 3.
