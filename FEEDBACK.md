# Feedback

The most useful thing you can do for this project is tell us what slipped past the rules.

The rulebook is updated monthly based on the new AI tells we observe in the wild. **You are the distributed test suite.** If your critic missed a pattern that should have been caught, or you noticed a new AI tell creeping into your feed, we want to know.

---

## What kind of feedback we want

### "My critic missed this" — highest value
You ran the workflow. The critic passed a post. You read it and noticed it sounded AI-generated in a way the rulebook should have caught. Send us:

- The post (or the relevant lines)
- Which rulebook section *should* have caught it
- What the pattern is, in your own words
- (Bonus) A plain-English alternative the system should have used instead

This is the single highest-value contribution. Every "the critic missed this" report is a candidate for the next monthly rulebook update.

### "I noticed a new AI tell in the wild" — also high value
You're scrolling LinkedIn. A post jumps out as obviously AI. You can name *exactly* what's wrong with it but the rulebook doesn't have a rule for it yet. Send us:

- A description of the pattern (anonymize the specific post)
- 2-3 example phrasings that demonstrate the pattern
- Why it's an AI tell (overuse since GPT-4? Specific to one model? Detectable by humans?)
- A proposed plain-English alternative

### "The brand profile field X confused me" — medium value
A field in the brand profile template was unclear. You filled it in wrong, or you didn't fill it in at all because you couldn't figure out what it was asking for. Tell us which field, and what would have made it clearer.

### "The workflow got stuck at step X" — medium value
A specific step in the workflow didn't run cleanly. You had to improvise. Tell us which step, what your AI runtime was, and what the error was.

### "The output was great" — low value but appreciated
We're glad. Mention the project to one other person who'd recognize the problem.

### "I disagree with rule X" — depends
Sometimes useful, sometimes not. The rulebook is opinionated by design and "I disagree" is not enough on its own. To make a useful case for changing a rule:
- Show evidence (a study, an n-gram, your own published posts performing differently than the rulebook predicted)
- Describe the specific failure mode the current rule is causing
- Propose a defensible alternative

Without evidence, the answer is probably no. With evidence, we'll engage seriously.

---

## How to submit feedback

### GitHub issues (preferred)
Open an issue in this repo. Use these labels:
- `rulebook-gap` — for "my critic missed this" or "new AI tell in the wild"
- `template-confusion` — for brand profile or workflow file issues
- `workflow-bug` — for steps that didn't run cleanly
- `disagreement` — for "I disagree with rule X"

Keep issues focused. One pattern, one report.

### GitHub Discussions
For longer-form questions, conversations about strategy, or "is this how I should be using it?" — use the Discussions tab instead of issues.

---

## What happens to your feedback

1. **Rulebook gaps** are reviewed monthly and either added to the rulebook or rejected with reasoning. If your report leads to a new rule, you'll be credited in the CHANGELOG.
2. **Template confusion** reports are batched and used to refine the templates and docs in the next minor release.
3. **Workflow bugs** are triaged within 7 days. Critical bugs get patched immediately.
4. **Disagreements** are debated openly. The rulebook stays opinionated, but opinions can change with evidence.

---

## What we won't do with your feedback

- We won't add a "configurable strictness mode" so users can soften individual rules. The whole project's value is the strict default. If you need looser rules for a specific use case, fork.
- We won't add UI, configuration files, or YAML setup. The project is markdown-only by design.
- We won't add features that automate publishing to LinkedIn. See [`docs/scheduling-options.md`](./docs/scheduling-options.md).
- We won't add telemetry, sign-ups, or "how was this generation?" prompts. Feedback is opt-in via GitHub.

---

## The maintenance commitment

The rulebook is updated **monthly** based on user reports, observed model drift, and platform changes. Stale rulebooks lose their teeth as model training advances and the AI tells of 2025 stop being the AI tells of 2026. **Maintenance is the moat** — the more you tell us what's slipping through, the sharper the rulebook stays for everyone.

See the [`CHANGELOG.md`](./CHANGELOG.md) for what's new each month.

---

## A note on tone

This file is short on purpose. Long contribution guides discourage contribution. The bar is: "is this useful evidence?" If yes, send it. If no, save us both the time. Thank you for caring enough to file the issue.
