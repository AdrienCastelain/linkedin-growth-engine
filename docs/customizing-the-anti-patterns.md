# Customizing the Anti-Patterns

> **What this is:** A guide to extending the rulebook with your own banned words, your own niche-specific anti-patterns, and (for non-English users) your own translated rulebook fork.
>
> **Who this is for:** Users who've shipped 4+ batches, started noticing patterns the universal rulebook misses, and want to harden the system against their specific failure modes. Or anyone whose audience speaks a language other than English.

---

## Two ways to customize

There are two different mechanisms for customization, and they serve different purposes.

### 1. Per-brand: your "always avoid" list

**Where it lives:** Brand profile §5d

**What it's for:** Words and phrases that *you* would never naturally use, but the universal rulebook doesn't cover. This is the lighter-weight option — you don't fork the rulebook, you just add to the brand-specific avoid list that the critic checks against (Step 5b, Lens 2).

**When to use it:**
- A common word in your industry that everyone overuses ("playbook" in SaaS, "delight" in design, "narrative arc" in writing)
- A phrase you've noticed yourself flinching at
- Words from a previous marketer who wrote in your voice and used phrases that aren't actually you
- Verbal tics from your own writing that you want to reduce

**How:**

Open your brand profile. Find Section 5d. Add words to the list:

```markdown
### 5d. "Always avoid" word list

- "playbook"
- "north star"
- "flywheel" (unless I'm actually describing one)
- "narrative arc"
- "thought leader"
- "circle back"
```

Add notes in italics if you want to explain when an exception is OK:

```markdown
- "GTM motion" *(only in the abstract — fine when describing an actual specific motion)*
```

**What happens at runtime:** The Step 5b critic loads your brand profile and includes your avoid list as part of Lens 2 (Voice Match). Any word from your list that appears in a draft gets flagged for replacement.

**Limit:** Don't go above 20 words. A list of 50+ words isn't a meaningful filter — it's noise. Pick the words that *actually* hurt when you see them.

---

### 2. Universal: forking the rulebook

**Where it lives:** `rulebook/linkedin-growth-engine-rulebook.md`

**What it's for:** Adding rules that should apply to *all* brands using your fork — not just yours. This is heavier-weight: you're creating a fork of the rulebook, maintaining it yourself, and (optionally) sharing it with other users in your niche or language.

**When to use it:**
- You're translating the rulebook into another language (the universal rulebook is English-only)
- You're building a niche-specific fork (e.g., "rulebook-medical-saas" with banned medical jargon, or "rulebook-german-b2b" with banned German marketing-speak)
- You're customizing the engagement architecture for a different platform (e.g., Threads, Bluesky)

**How:**

1. Fork the project
2. Edit `rulebook/linkedin-growth-engine-rulebook.md` directly
3. Update the modules in `modules/` to match (the modules are thin wrappers — they should stay aligned with whatever the rulebook says)
4. Update the version number at the top of the rulebook
5. Add a note in your fork's README explaining what's different

**Don't fork lightly.** Maintaining a rulebook fork means staying aligned with upstream changes. The universal rulebook will get updates as LinkedIn's algorithm evolves. If you fork, you're committing to merging those updates yourself.

---

## Adding a banned word to the universal rulebook (PR-worthy)

If you find a word that:
- Has seen a >500% usage spike since AI tools became common
- Appears in AI-generated content significantly more than human-written content
- Has a plain-English alternative
- Isn't already on the Tier 1, Tier 2, or Tier 3 list

...then it's a candidate for the universal rulebook. Open a GitHub issue or PR with:

1. The word
2. Evidence of the usage spike (citations to studies, n-gram analysis, your own samples)
3. The proposed tier (1, 2, or 3 — see rulebook §2.2)
4. The plain-English alternative

The maintainer reviews. If it's defensible, it goes in. If it's borderline, it stays in your brand-specific list.

**Words that have been considered and rejected:**
- "ecosystem" — too contextually variable, sometimes the right word
- "best practices" — overused but not specifically AI-flavored
- "moving forward" — corporate-speak but not an AI tell
- "synergy" — already on Tier 2

---

## Forking the rulebook for a non-English language

The current rulebook is English-only. The banned vocabulary, em dash rules, and broetry patterns are all English-specific. Other languages have their own AI tells.

### What translates directly

- Ground Rules (§1) — universal: never fabricate, never invent data, opinions OK, prompt for stories, never contradict positioning
- Quality Gates (§3) — mostly universal, except Gate 2 (Anti-Pattern Scan, which references English vocabulary)
- Engagement Architecture (§4) — closing types, see-more engineering, hook-to-close coherence, posting cadence — all universal
- Format & First Comment (§5) — mostly universal
- Performance Feedback Loop (§8) — universal
- Competitive Intelligence (§10) — universal
- Reshare Strategy (§11) — universal

### What needs translation

- **§2.1 Banned Opening Phrases** — these are English-language clichés. You'll need to identify the equivalent clichés in your language. (E.g., German LinkedIn has its own "Liebe Community..." opening cliché.)
- **§2.2 Banned Vocabulary** — identify the words that have spiked in your language since AI tools became common. (E.g., French AI content overuses "approfondir," "dynamique," "écosystème.")
- **§2.3 Banned Structural Patterns** — broetry exists in other languages but the threshold may differ. False opposition exists. Snappy triads exist. Therapist mode exists. Adapt the examples.
- **§2.6 Banned Formatting** — the rocket emoji rule is universal. The em dash rule may not be (some languages use em dashes more naturally).
- **§2.7 Em Dash Rule** — language-dependent. German uses long dashes more freely than English.
- **§2.8 AI Sentence-Level Tells** — identify the equivalent constructions in your language. The "Not because X. Because Y." pattern probably exists in some form.

### How to do the translation

1. Fork the project
2. Create `rulebook/linkedin-growth-engine-rulebook-LANG.md` (e.g., `-de.md` for German)
3. Translate Sections 1, 3, 4, 5, 6, 8, 9, 10, 11 directly
4. **Rewrite** (don't translate) Sections 2 and 2.7 — these need native-language anti-patterns identified by someone fluent in the language and the local LinkedIn ecosystem
5. Update the modules in `modules/` to reference the new rulebook file
6. Add a note in the README about your language fork
7. Open a PR if you want it merged upstream as an official translation

**The translation isn't a 1:1 swap.** Different languages have different AI tells. Identifying them is the actual work — the translation itself is the easy part.

---

## Adding a niche-specific anti-pattern (without forking)

If you've found a pattern that's specific to your industry (not just your personal voice), but you don't want to maintain a full rulebook fork, you have a middle option: a custom module.

### How to add a custom module

1. Create a new file in `modules/`: e.g., `modules/20-medical-saas-niche.md`
2. Use the same structure as the existing modules (purpose, load when, quick reference, full rules pointer)
3. Add an entry in `INDEX.md` under "Standalone Modules" pointing to your new module
4. Reference the module in your brand profile or your agent's "Skills Bundle" so it gets loaded

The module is now part of the workflow's context whenever you load the skill. The Step 5b critic will pick up your custom rules if you write them in the same format as the universal rulebook's anti-patterns.

**Example custom module structure:**

```markdown
# Module 20: Medical SaaS Niche Anti-Patterns

**Source of truth:** This file (no upstream rulebook section)
**Load when:** Writing content for medical SaaS audiences

## Quick Reference

- **Banned vocabulary specific to medical SaaS:**
  - "patient journey" (overused, vague — name the specific transition)
  - "clinical-grade" (marketing-speak unless you're FDA-cleared)
  - "evidence-based" (use only when citing actual evidence)
  - "stakeholder alignment" (consultant-speak)
  - "value-based care" (jargon — use plain language unless your ICP is a payer)

- **Banned structural patterns specific to medical SaaS:**
  - The "physicians are burned out" hook (cliché — most posts about this audience use it)
  - The "we're improving outcomes" closing (vague — name the specific outcome)
  - The "our AI is HIPAA-compliant" credibility line as a hook (HIPAA compliance is table stakes, not a value prop)

- **Things to do instead:**
  - Name the specific clinical workflow you're improving
  - Cite the actual study, not "research shows"
  - Quote the actual physician you talked to (with permission), not a composite
```

This module is yours. You maintain it. You can share it with peers in your niche. If the pattern catches on, propose it as an official module via PR.

---

## When not to customize

**Don't add words to your avoid list just to feel rigorous.** A 50-word avoid list isn't twice as effective as a 10-word list. It's noise. Pick the words that actually hurt when you see them.

**Don't fork the rulebook because you disagree with one rule.** If you disagree with, say, the em dash rule, just override it in your brand profile (set "Allowed per post: 5"). Forking creates maintenance burden.

**Don't add a custom module for one-off observations.** If you noticed your agent used a specific phrase you didn't like in one post, that's a brand profile fix, not a custom module. Custom modules are for patterns that recur across many posts.

**Don't translate the rulebook unless you actually speak the target language fluently AND know that language's LinkedIn ecosystem.** A bad translation is worse than no translation — it teaches users to follow rules that don't apply.

---

## How to know if your customization is working

After 2-3 batches with your customization in place:

- **Are the words you added to your avoid list showing up in drafts?** If yes, the critic isn't reading the brand profile correctly. Make sure §5d is in the loaded context.
- **Are the words you added still being caught and replaced?** If yes, customization is working. The drafts you see should have the alternative wording.
- **Is the post quality measurably better than before?** If yes, the customization is paying off. If not, the words you banned weren't the actual problem — look for structural patterns instead.

**Iterate.** Customization isn't a one-time setup. Every 30-60 days, review your avoid list and your custom modules. Add new ones based on what you've noticed. Remove ones that turned out not to matter.
