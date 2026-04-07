---
name: linkedin-growth-engine
description: LinkedIn content generation workflow with 12 per-post quality gates, anti-AI pattern catcher, independent critic review, and batch variety audit. Use when generating LinkedIn posts, building a content calendar, running a weekly content batch, writing comments on others' posts, or reviewing existing content against LinkedIn quality standards.
---

# LinkedIn Growth Engine

A complete LinkedIn content system: a canonical rulebook, 19 modules (12 thin wrappers + 7 standalone), and an executable weekly workflow. Built to produce content that doesn't read like AI, holds dwell time, and consistently aligns with your positioning over the 60-90 days the LinkedIn algorithm rewards.

> **🤖 If you are an AI loading this skill: STOP. Read [`./CLAUDE.md`](./CLAUDE.md) first.** That file is your bootstrap runbook — it tells you how to detect what mode the user is in (new user, first-run ready, returning), how to greet them, how to run the onboarding flow, how to spawn a sub-agent for the Step 5b critic in Claude Code, and what hard constraints to honor. Don't dump documentation on the user. Walk them through it. The CLAUDE.md file is the single source of truth for AI behavior in this project; this SKILL.md file is metadata for skill discovery only.

> **Editorial position:** This system optimizes for voice-locked content, earned vulnerability, dwell time, and inbound DMs from your specific ICP. It does NOT optimize for virality, raw follower growth, "thought leader" aesthetics, or short-term algorithm hacks. If your definition of a good LinkedIn post is different from ours, the rules will frustrate you. Read the "What this rulebook is optimizing for" preamble in [`./rulebook/linkedin-growth-engine-rulebook.md`](./rulebook/linkedin-growth-engine-rulebook.md) and the "What we mean by good" section in [`./README.md`](./README.md) before you commit time.

## What this skill does

- Generates a week of 4 LinkedIn posts that match your voice and pillars
- Validates every post against 12 anti-AI quality gates (plus an optional 13th AI-detection spot-check)
- Catches the structural patterns that make AI-written content obvious
- Audits the batch for variety (hooks, closings, lengths, formats)
- Produces first comments and reply templates alongside each post
- Surfaces reshare candidates, polls, and proactive comment angles

## Load order

When you start a content session, load in this order:

1. **This file (SKILL.md)** — gives you the orientation
2. **[`./rulebook/linkedin-growth-engine-rulebook.md`](./rulebook/linkedin-growth-engine-rulebook.md)** — the canonical content rules. Read fully on first use, scan by section after.
3. **Your brand profile** — copy `templates/brand-profile-template.md` and fill it in with your positioning, voice, pillars, story bank, and LinkedIn goal. This is the per-brand customization layer.
4. **[`./modules/19-cultural-profiles.md`](./modules/19-cultural-profiles.md)** if your audience is non-US
5. **[`./CONTENT-GENERATION-WORKFLOW.md`](./CONTENT-GENERATION-WORKFLOW.md)** — execute the 8-step weekly batch process

## Module map

| # | Module | Load when |
|---|--------|-----------|
| 01 | [Ground Rules](./modules/01-ground-rules.md) | Always — non-negotiable integrity rules |
| 02 | [Anti-Patterns](./modules/02-anti-patterns.md) | Writing any content (posts, comments, reshares) |
| 03 | [Quality Gates](./modules/03-quality-gates.md) | Validating posts before scheduling |
| 04 | [Engagement Architecture](./modules/04-engagement.md) | Writing posts — closings, hooks, dwell time, cadence |
| 05 | [Proactive Comments](./modules/05-comments.md) | Writing comments on others' posts |
| 06 | [Format & First Comment](./modules/06-format.md) | Choosing post format, writing first comments |
| 07 | [What Good Looks Like](./modules/07-quality-signals.md) | Evaluating content quality |
| 08 | [Hashtags](./modules/08-hashtags.md) | Adding hashtags to posts |
| 09 | [Performance Feedback](./modules/09-feedback-loop.md) | Weekly/monthly reports, strategy adjustments |
| 10 | [Competitive Intelligence](./modules/10-competitive.md) | Onboarding, monthly niche analysis |
| 11 | [Reshare Strategy](./modules/11-reshares.md) | Finding and resharing content |
| 12 | [Implementation](./modules/12-implementation.md) | System prompt structure, validation pipeline |
| 13 | [Poll Strategy](./modules/13-polls.md) | Creating polls, follow-up post pattern |
| 14 | [Newsletter Strategy](./modules/14-newsletter.md) | Newsletter launch criteria, structure, cross-promotion |
| 15 | [Profile Alignment](./modules/15-profile-alignment.md) | Headline, About, Featured section optimization |
| 16 | [DM Conversion](./modules/16-dm-conversion.md) | Converting post engagement into DMs and leads |
| 17 | [Connection Growth](./modules/17-connection-growth.md) | Strategic connection requests, network growth |
| 18 | [Content Recycling](./modules/18-content-recycling.md) | Evergreen tagging, story bank management |
| 19 | [Cultural Profiles](./modules/19-cultural-profiles.md) | US/UK/ANZ/APAC market-specific overrides |

## Quick reference — what to load by task

- **Writing a post:** 01 + 02 + 04 + 06 + 08 + 19 (if non-US market)
- **Writing a poll:** 01 + 02 + 13
- **Validating a post:** 03 + 19 (cultural override checklist)
- **Writing a comment on someone's post:** 01 + 02 + 05
- **Writing reshare commentary:** 01 + 02 + 11
- **Responding to a DM:** 16
- **Growing your network:** 17
- **Weekly batch generation:** All modules via [CONTENT-GENERATION-WORKFLOW.md](./CONTENT-GENERATION-WORKFLOW.md)
- **Onboarding (new brand):** 10 + 09 + 15 + 17 + 19
- **Monthly performance review:** 09 + 10 + 15 + 18

## How to get started

See [`docs/quickstart-15-minute.md`](./docs/quickstart-15-minute.md) for the full setup walkthrough: filling in your brand profile, running your first content batch, and shipping it.

## Worked examples (highest-leverage proof)

The strongest demonstration of the system is in the `examples/` directory. Read these before committing time:

- [`examples/anti-pattern-catches/README.md`](./examples/anti-pattern-catches/README.md) — 6 worked before/after rewrites showing the system stopping bad content mid-generation. Catch 5 (manufactured vulnerability) is the single best demo.
- [`examples/sample-post-batch/`](./examples/sample-post-batch/) — a complete 4-post batch generated against the example brand profile, with full quality check tables and Step 5b critic review notes per post.

## Source of truth

The rulebook at [`./rulebook/linkedin-growth-engine-rulebook.md`](./rulebook/linkedin-growth-engine-rulebook.md) is canonical. Modules are thin wrappers pointing back to it. If a module and the rulebook ever disagree, the rulebook wins.
