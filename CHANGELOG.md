# Changelog

All notable changes to the LinkedIn Growth Engine will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/), and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.0.0] — 2026-04-22

### Initial public release

The first public release of the LinkedIn Growth Engine. Adapted from an internal content system refined over multiple months of real use.

**Includes:**
- Canonical rulebook (`rulebook/linkedin-growth-engine-rulebook.md`) with 11 sections covering ground rules, anti-patterns, quality gates, engagement architecture, format rules, hashtag strategy, performance feedback, competitive intelligence, and reshare strategy
- 19 thin modules (`modules/01-19`) covering each part of the system as quick-reference wrappers pointing back to the rulebook
- 8-step executable workflow (`CONTENT-GENERATION-WORKFLOW.md`) with explicit First-Run Mode and Returning Mode branches
- Brand profile templates: minimal (4 sections, 15 minutes) and full (10 sections, 30 minutes)
- Filled-in fictional example brand profile (Alex Hayes)
- Content audit and industry research templates
- Optional content agent template with fully filled-in fictional example (Sage)
- Sample post batch with 4 posts, complete quality check results, and critic review notes
- 6 worked anti-pattern catches showing the system stopping bad content mid-generation
- 9 documentation files covering quickstart, workflow, brand profile, agent setup, troubleshooting, scheduling, anti-pattern customization, content audit production, and industry research
- MIT license
- Contributing guidelines

### Key design decisions
- Rulebook is canonical; modules are thin wrappers
- Brand profile is the per-brand customization layer (positioning, voice, pillars, story bank)
- First-Run Mode supports brand-new users with no prior data
- Returning Mode supports users with 30+ days of analytics
- Step 5b critic review uses a separate agent instance to catch what the generator misses
- Step 8 scheduling defaults to LinkedIn's native scheduler (manual) — automated paths are documented but not recommended for solo users
- Voice samples in the brand profile are the only HARD STOP gate

### Reviewers
The rulebook went through review by two independent LinkedIn experts (10 and 20 years of experience) prior to public release. The example brand profile and example outputs were reviewed by a fractional CMO and a senior product strategist before launch.

### What's not in v1.0
- Non-English language support (English-only — language forks welcome)
- Carousel PDF rendering pipeline (the workflow generates carousel content; rendering is manual or via your image tool of choice)
- Multi-image generation pipeline
- Automated performance data ingestion (manual export from LinkedIn analytics required)
- A/B testing framework
- Automated competitive intelligence (manual benchmark account analysis only)

These are tracked as v1.1+ candidates in the project issues.

---

[1.0.0]: https://github.com/AdrienCastelain/linkedin-growth-engine/releases/tag/v1.0.0
