# Implementation Notes

**Source of truth:** `../rulebook/linkedin-growth-engine-rulebook.md` — Section 9
**Load when:** System prompt structure, validation pipeline
**Full rules:** For complete rules, read the Rulebook, Section 9.

---

## Quick Reference

- **System prompt structure:** Base instructions + Ground Rules (01) + Anti-Patterns (02) + Engagement Architecture (04) + Format (06) + Hashtags (08) + Brand Profile + Voice Profile + Content calendar + Reference samples + Performance feedback (09)
- **Validation Pass 1 (per-post):** quality gates 1-3, 5-6, 8 + voice profile + LinkedIn Goal + hook-to-close coherence + hashtag validation
- **Validation Pass 2 (batch-level):** gates 4, 7, 9 + pillar distribution + format diversity + closing type variety
- **Weekly batch generation:** generate posts sequentially passing previous as context, rotate pillars (min 2 per week), vary length (150-500+ words, max 1 at 500+ per week), never below 150-word minimum
- **Canonical workflow:** see CONTENT-GENERATION-WORKFLOW.md for the 8-step process
