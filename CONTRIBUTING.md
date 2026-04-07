# Contributing to the LinkedIn Growth Engine

Thank you for considering a contribution. The whole project is built on the premise that the rules have teeth — and that means the contribution bar is high. Here's how to get changes merged.

## What we want

- **Bug reports** — anything that contradicts itself, breaks the workflow, or produces output that violates the rulebook
- **New banned vocabulary** — words with documented usage spikes since AI tools became common, with citations and a proposed tier (1, 2, or 3)
- **New worked examples** — anti-pattern catches you've encountered in real use, formatted to match [`examples/anti-pattern-catches/`](./examples/anti-pattern-catches/)
- **Language forks** — translations of the rulebook into other languages, with locally-identified anti-patterns (not just translated text)
- **Module additions** — niche-specific rules that don't fit the universal rulebook but would help users in your space
- **Documentation improvements** — fixes for ambiguity, missing context, broken links, outdated screenshots

## What we don't want

- **"Make the rulebook less strict" PRs.** The whole project's value is that the rules have teeth. Softening language is the opposite direction.
- **"Add my favorite LinkedIn growth hack" PRs.** The project is built around algorithm-aligned content, not engagement hacks. If your contribution is "post X to game the algorithm," it's not a fit.
- **"Make it work without voice samples" PRs.** Voice samples are the core mechanism. There is no meaningful workflow without them.
- **Blanket renames or restructures.** The architecture is intentional. If you want to propose a structural change, open an issue first to discuss before submitting a PR.
- **PRs that add hedging or qualifications to the rulebook.** "It depends" is the opposite of what this project does.

## How to propose a change

### For small fixes (typos, broken links, wording)

Open a PR directly. Keep the diff small. Include a one-line description of what the fix is and why it matters.

### For new rules or modules

Open an issue first. Use this template:

```
**Type of change:** new banned word / new module / new anti-pattern / other

**What you're proposing:** [one sentence]

**Why it matters:** [why this isn't already covered]

**Evidence:**
- [citations to studies, n-gram analysis, your own samples]
- [link to a real LinkedIn post that demonstrates the problem]
- [link to AI-generated content that uses the pattern]

**Proposed location:** [which section of the rulebook, or new module name]

**Plain-English alternative:** [if proposing a banned word, what should be used instead]
```

Maintainers will respond within 7 days. If the proposal is accepted, you can open the PR.

### For language forks

Open an issue first announcing your intent. Translation is the easy part — the actual work is identifying the language-specific anti-patterns (banned vocabulary, structural patterns, AI tells in your language). Don't submit a PR until you've done that work.

### For documentation improvements

Open a PR with the change. Maintainers will review for clarity and accuracy.

## Quality standards for contributions

### For rule additions
- Must have evidence (citations, studies, samples)
- Must have a plain-English alternative (for banned words)
- Must not contradict an existing rule
- Must be defensible against the question "is this a stylistic preference or a real failure mode?"

### For documentation
- Direct, specific, no hedge
- Match the existing voice (read [`docs/quickstart-15-minute.md`](./docs/quickstart-15-minute.md) for the reference voice)
- No marketing language
- No "ultimate guide" framing
- No "in today's fast-paced..." openings (we ban those in the rulebook — we're not going to write them in the docs)

### For examples
- Must use a fictional persona, not a real person
- Must be marked clearly as fictional at the top
- Must include the full Step 5 quality check results and Step 5b critic notes
- Must be reproducible — anyone running the workflow against the same brand profile should get similar output

## Code of conduct

This project is a content system, not a community. The contribution bar is high because the rules are opinionated. We're not building consensus — we're building a tool that takes positions.

That said:
- Be direct, not rude
- Push back with reasoning, not personality
- Cite evidence
- If your PR is rejected, the reason is in the comment thread — read it before re-submitting

## Maintainer commitment

- Issues get a first response within 7 days
- PRs get a first review within 14 days
- Accepted contributions get merged within 30 days
- We will not silently let your PR rot — if it doesn't fit, you'll get a clear "no" with reasoning

## License

By contributing, you agree that your contributions will be licensed under the MIT License (see [`LICENSE`](./LICENSE)).

---

The fastest way to get a contribution merged is to make it specific, evidence-backed, and aligned with the project's existing voice. If you've read this whole file and the rulebook before submitting, you're already ahead.
