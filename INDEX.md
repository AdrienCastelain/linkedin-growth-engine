# LinkedIn Growth Engine — Index

**Public release v1.0** — open-source LinkedIn content generation skill for Claude Code. MIT licensed.

**Source of truth:** [`./rulebook/linkedin-growth-engine-rulebook.md`](./rulebook/linkedin-growth-engine-rulebook.md)
**Skill entry point:** [`./SKILL.md`](./SKILL.md)
**Workflow:** [`./CONTENT-GENERATION-WORKFLOW.md`](./CONTENT-GENERATION-WORKFLOW.md)

---

## Purpose

A complete content system for generating LinkedIn posts that hold dwell time, match your voice, and don't read like AI. Built around 9 rulebook quality gates (expanded into 12 per-post operational checks in the workflow, plus an optional 13th AI-detection spot-check), an independent critic loop, and a batch variety audit you run with any Claude Code agent.

**Load order:**
1. Load [SKILL.md](./SKILL.md) — orientation
2. Load this skill, starting with the modules you need
3. Load your brand profile (cultural market profile from module 19 if non-US)
4. Run [CONTENT-GENERATION-WORKFLOW.md](./CONTENT-GENERATION-WORKFLOW.md)

---

## Module Map — Load Only What You Need

### Thin Wrappers (quick reference → Rulebook for full rules)

| # | Module | File | Rulebook § | Load When |
|---|--------|------|-----------|-----------|
| 01 | Ground Rules | [modules/01-ground-rules.md](./modules/01-ground-rules.md) | §1 | Always — non-negotiable integrity rules |
| 02 | Anti-Patterns | [modules/02-anti-patterns.md](./modules/02-anti-patterns.md) | §2 | Writing any content (posts, comments, reshares) |
| 03 | Quality Gates | [modules/03-quality-gates.md](./modules/03-quality-gates.md) | §3 | Validating posts before scheduling |
| 04 | Engagement Architecture | [modules/04-engagement.md](./modules/04-engagement.md) | §4 | Writing posts — closings, hooks, dwell time, cadence |
| 05 | Proactive Comments | [modules/05-comments.md](./modules/05-comments.md) | §4.11 | Writing comments on others' posts |
| 06 | Format & First Comment | [modules/06-format.md](./modules/06-format.md) | §5 | Choosing post format, writing first comments |
| 07 | What Good Looks Like | [modules/07-quality-signals.md](./modules/07-quality-signals.md) | §6 | Evaluating content quality |
| 08 | Hashtags | [modules/08-hashtags.md](./modules/08-hashtags.md) | §7 | Adding hashtags to posts |
| 09 | Performance Feedback | [modules/09-feedback-loop.md](./modules/09-feedback-loop.md) | §8 | Weekly/monthly reports, strategy adjustments |
| 10 | Competitive Intelligence | [modules/10-competitive.md](./modules/10-competitive.md) | §10 | Onboarding, monthly niche analysis |
| 11 | Reshare Strategy | [modules/11-reshares.md](./modules/11-reshares.md) | §11 | Finding and resharing content |
| 12 | Implementation | [modules/12-implementation.md](./modules/12-implementation.md) | §9 | System prompt structure, validation pipeline |

### Standalone Modules (full content, no Rulebook equivalent)

> **For your first month, you only need modules 13 and 19.** The rest (14-18) cover network growth, DM conversion, profile optimization, newsletter strategy, and content recycling. They're valuable but they solve problems you don't have on Day 1. Add them to your loaded module set after you've shipped 4-8 posts and started seeing real engagement.

**Core for first month:**

| # | Module | File | Load When |
|---|--------|------|-----------|
| 13 | Poll Strategy | [modules/13-polls.md](./modules/13-polls.md) | Creating polls, follow-up post pattern |
| 19 | Cultural Profiles | [modules/19-cultural-profiles.md](./modules/19-cultural-profiles.md) | US/UK/ANZ/APAC market-specific overrides |
| — | Workflow | [CONTENT-GENERATION-WORKFLOW.md](./CONTENT-GENERATION-WORKFLOW.md) | Weekly batch generation (4 posts/session) |

**Advanced — add after your first month:**

| # | Module | File | Load When |
|---|--------|------|-----------|
| 14 | Newsletter Strategy | [modules/14-newsletter.md](./modules/14-newsletter.md) | Launch criteria, structure, cross-promotion |
| 15 | Profile Alignment | [modules/15-profile-alignment.md](./modules/15-profile-alignment.md) | Headline, About, Featured section optimization |
| 16 | DM Conversion | [modules/16-dm-conversion.md](./modules/16-dm-conversion.md) | What happens when content generates DMs and leads |
| 17 | Connection Growth | [modules/17-connection-growth.md](./modules/17-connection-growth.md) | Strategic connection requests, network growth |
| 18 | Content Recycling | [modules/18-content-recycling.md](./modules/18-content-recycling.md) | Evergreen tagging, story bank management |

---

## Quick Reference — What to Load by Task

**First-Run Mode (your first batch):** Just the workflow + your minimal brand profile. Modules are optional deepening — skip them on the first run.

**Writing a post (Returning Mode):** 01 + 02 + 04 + 06 + 08 + 19 (if non-US market)
**Writing a poll:** 01 + 02 + 13
**Validating a post:** 03 + 19 (cultural override checklist)
**Writing a comment on someone's post:** 01 + 02 + 05
**Writing a reshare commentary:** 01 + 02 + 11
**Responding to a DM:** 16
**Growing network:** 17
**Weekly batch generation:** All modules via CONTENT-GENERATION-WORKFLOW.md
**Onboarding a new brand:** 10 + 09 + 15 + 17 + 19
**Weekly preview email:** 09
**Monthly performance review:** 09 + 10 + 15 + 18 (recycling check)
**Newsletter launch:** 14
**Profile optimization:** 15
**Content running low:** 18 (story bank, recycling)
**Cold streak:** 04

---

## Architecture — Single Source of Truth

**The Rulebook is canonical.** All rules live in one place:
[`./rulebook/linkedin-growth-engine-rulebook.md`](./rulebook/linkedin-growth-engine-rulebook.md)

### Module Types

**Thin wrappers (modules 01-12):** Quick-reference summaries pointing to Rulebook sections. Load these for working memory. If you need the full rule, read the Rulebook section directly.

**Standalone modules (modules 13-19):** Content that has no Rulebook equivalent. These are full modules, not wrappers.

**Workflow:** [CONTENT-GENERATION-WORKFLOW.md](./CONTENT-GENERATION-WORKFLOW.md) is standalone — the canonical 8-step weekly generation process.

### When to Read the Rulebook Directly
- Writing or reviewing a full batch of posts (load relevant Rulebook sections, not wrappers)
- Resolving a contradiction (Rulebook wins, always)
- Updating rules (update the Rulebook first, then regenerate affected wrappers)

### What Lives in Your Brand Profile (Per-Brand Customization)
- Positioning statement
- Voice profile (slider positions, reference samples)
- Content pillars and weights
- ICP definition
- Origin story and story bank
- Hook and closing preferences
- Include/avoid topics
- Benchmark accounts for competitive analysis
- Target market (determines cultural profile)
