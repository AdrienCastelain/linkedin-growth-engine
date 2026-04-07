# Anti-Pattern Catches

> **What this is:** Real before/after rewrites showing the LinkedIn Growth Engine catching banned patterns mid-generation. Each example shows the original AI draft, the specific gate or critic check that flagged it, the rule it violated (with rulebook section), and the rewritten version that passed.
>
> **Why this exists:** The rulebook lists rules. The sample post batch shows finished output. This file shows the *catching* — the moment a draft tries to ship a Tier 1 word, a polished parallel closing, or a manufactured-vulnerability arc, and the system stops it.
>
> **How to read it:** Each catch is a complete worked example. If you're skeptical that the rulebook actually catches AI tells, read 3-4 of these. If you want to teach yourself the rules, read all 6.

---

## Catch 1 — Tier 1 banned word (vocabulary check)

**Source:** Generation attempt for Post 1 of the [sample post batch](../sample-post-batch/), niche_problem about channel selection
**Caught by:** Step 5, Vocabulary Check
**Rule violated:** Rulebook §2.2, Tier 1 absolute ban — "harness"

### Original draft

> A founder asked me last week which growth channel she should pick. She had $8K to spend and a board meeting in 6 weeks. The right answer wasn't the channel with the highest theoretical ceiling. It was the channel she could **harness** fastest if it didn't work the first time.

### Why it failed

"Harness" is a Tier 1 absolute ban in the rulebook (§2.2). It's in the same word family as "leverage," "unlock," "transformative" — words whose usage spiked 1,000%+ since ChatGPT launched. They're near-certain AI signals to a careful reader. The check is not "does this word make sense in context?" The check is "is this word on the list?" If yes, replace.

### Rewritten

> A founder asked me last week which growth channel she should pick. She had $8K to spend and a board meeting in 6 weeks. The right answer wasn't the channel with the highest theoretical ceiling. It was the channel that could tell her *why* it was failing inside her timeline.

### Why the rewrite works

"Tell her why it was failing" is a plain-English replacement for "harness" that says the same thing better. The italics on "why" carry the emphasis the original was trying to load onto "harness." The sentence is shorter and more concrete. This is the typical pattern when you remove a Tier 1 word: the sentence gets sharper, not weaker.

---

## Catch 2 — Polished parallel closing (critic Lens 1)

**Source:** Generation attempt for Post 2 of the [sample post batch](../sample-post-batch/), failure_learning about a renewal pricing decision
**Caught by:** Step 5b, Critic Review, Lens 1 (AI Detection)
**Rule violated:** Rulebook §2.8, AI sentence-level tells — "Polished parallel closings"

### Original draft (closing only)

> ...I now run a 4-call willingness-to-pay check before any pricing change over 10%.
>
> **Pricing decisions should be grounded in customer research, not competitor benchmarks.**

### Why it failed

The bolded line is a polished parallel construction. The shape is "X, not Y" with both halves balanced for rhythm. The rulebook §2.8 specifically calls these out as a strong AI structural tell — they sound like they belong on a motivational poster, and AI models default to them because they create instant contrast with minimal effort.

The Step 5 self-check missed it because the line passes the vocabulary scan (no banned words), the transition check (it's not a transition), and the structural check (it's not broetry). The critic caught it because Lens 1 is specifically looking for "produced" rhythms.

### Rewritten

> ...I now run a 4-call willingness-to-pay check before any pricing change over 10%. Doesn't make me right. Makes me less anchored.
>
> Maybe the worst pricing mistakes are the ones where the consultant thought she was being careful.

### Why the rewrite works

Two changes:
1. "Doesn't make me right. Makes me less anchored." replaces the polished closing with two short sentences that admit the limit of the new process. This is voice-honest, not poster-clean.
2. The Type B closing ("Maybe the worst pricing mistakes are...") is an incomplete statement that invites disagreement instead of stating a maxim. It's specific to the post (about consultants being cautious) rather than a general pricing principle.

The critic specifically asked for Type B because the original Type A (the closing question that was buried earlier in the draft) wasn't pointed enough. Type B is the right closing for failure_learning posts because it leaves the reader sitting with the unresolved feeling.

---

## Catch 3 — Two-word kicker (critic Lens 1)

**Source:** Generation attempt for Post 3 of the [sample post batch](../sample-post-batch/), contrarian about founder-led marketing
**Caught by:** Step 5b, Critic Review, Lens 1 (AI Detection)
**Rule violated:** Rulebook §2.8, AI sentence-level tells — "Polished parallel closings" (the two-word kicker subtype)

### Original draft (closing only)

> ...A founder who writes one good homepage and ten clarifying sales emails has done more founder-led marketing than a founder who posts three times a week and lets a contractor write the homepage.
>
> **Stop posting. Start writing.**

### Why it failed

Two issues:
1. **Two-word kicker.** "Stop posting. Start writing." is a textbook AI closing pattern — symmetric, punchy, makes you feel like you've been served wisdom. The rulebook treats these as polished parallel closings.
2. **Misrepresents Alex's actual position.** Alex isn't against posting. She's against posting *first*, before the homepage and sales emails are written. The kicker simplified the argument into a louder, less accurate version. This is what the critic Lens 1 means by "produced" — the closing is optimized for shareability, not accuracy.

### Rewritten

> ...A founder who writes one good homepage and ten clarifying sales emails has done more founder-led marketing than a founder who posts three times a week and lets a contractor write the homepage.
>
> The question I'd push back on with anyone selling "founder content" packages right now: what artifacts is the founder actually going to make this quarter that everything else points back to?

### Why the rewrite works

The new closing is a Type A genuine question targeted at a specific audience (people selling founder content packages). It's longer, harder to share as a screenshot, and more accurate to Alex's actual position. The rulebook trades shareability for accuracy on purpose — content that misrepresents your view to get likes corrodes the trust that drives the inbound leads goal.

---

## Catch 4 — "Always avoid" word from brand profile (critic Lens 2)

**Source:** Same Post 3 generation as Catch 3
**Caught by:** Step 5b, Critic Review, Lens 2 (Voice Match)
**Rule violated:** Brand profile §5d, Alex's "always avoid" list — "playbook"

### Original draft (excerpt)

> The dominant version: founders should post on LinkedIn three times a week. **The founder content playbook is wrong about which artifacts come first.**

### Why it failed

"Playbook" is on Alex's "always avoid" list in her brand profile (§5d). The note next to it says: "the single most-overused word in early-stage SaaS." It's not banned by the universal rulebook (§2.2 doesn't list it), so the Step 5 vocabulary check passed. But the critic Lens 2 explicitly compares against the brand-specific avoid list, and "playbook" was in it.

This is why the per-brand avoid list exists separately from the rulebook. The rulebook handles universal AI tells. The brand profile handles per-niche overuse. A SaaS GTM expert needs to ban "playbook" the way a designer needs to ban "synergy."

### Rewritten

> The dominant version: founders should post on LinkedIn three times a week. **Build the personal brand. Be visible. The founder is the channel.**
>
> That's a tactic. It's not what founder-led marketing actually is.

### Why the rewrite works

The single sentence with "playbook" was a weak summary anyway. Replacing it with three short sentences that *show* the dominant version (build the brand, be visible, be the channel) makes the reader recognize the position before Alex critiques it. The critique is sharper because the reader has already pictured the thing being criticized.

---

## Catch 5 — Manufactured vulnerability (critic Lens 1)

**Source:** Generation attempt for an alternative version of Post 2, before the renewal story was used
**Caught by:** Step 5b, Critic Review, Lens 1 (AI Detection)
**Rule violated:** Rulebook §2.3, banned structural patterns — "Manufactured vulnerability"

### Original draft (full post)

> Three years ago I was a junior consultant who thought I knew how to price.
>
> I told a founder client to keep her pricing flat at her first renewal. "Don't risk the relationship," I said. "Customer loyalty is everything."
>
> She did. They renewed. I felt good.
>
> Six months later she lost two of those accounts to a competitor who repriced. The "loyalty" I'd protected was actually a discount they were exploiting.
>
> That was the day I learned: real loyalty pays full price.
>
> Now I never recommend flat renewals.
>
> What's the lesson you learned the hard way about pricing?

### Why it failed

This is textbook manufactured vulnerability:
- Past failure is admitted ("I was a junior who thought I knew how to price")
- The failure has a tidy resolution ("Now I never recommend flat renewals")
- The writer comes out looking *more* competent at the end than at the beginning ("That was the day I learned")
- The closing is a generic question that invites stories without taking a position
- The maxim "real loyalty pays full price" is exactly the kind of poster line the rulebook bans
- The story pattern is "naïve past me → wise present me," which is the classic LinkedIn arc

The rulebook §2.3 says: "Manufactured vulnerability — admitting a past failure that has a tidy resolution where the writer comes out looking good." This post is the entire pattern.

### Rewritten

The post was *replaced*, not rewritten. The critic recommendation was: "This story has the failure-redemption arc the rulebook bans. Pull a real story from the story bank where the failure doesn't have a tidy resolution." The generator pulled Story 2 instead, which became the version you see in the [sample post batch](../sample-post-batch/post-2-renewal-i-talked-her-out-of.md).

### Why the rewrite works

The published version (Post 2) makes Alex look *worse* at the end than at the beginning, not better. She's a senior consultant who made a $180K mistake by anchoring on the wrong data. The mistake "still bothers her." The lesson she draws ("doesn't make me right, makes me less anchored") is honest about its limits.

This is the difference between manufactured vulnerability (which is a marketing pattern) and earned vulnerability (which is a credibility move). The rulebook is opinionated about this because the AI default is the manufactured version.

---

## Catch 6 — Fabrication check (Step 5 hard fail)

**Source:** Generation attempt for an alternative version of Post 4, the archaeology post
**Caught by:** Step 5, Fabrication Check (HARD FAIL)
**Rule violated:** Rulebook §1, Ground Rule 1 — "Never fabricate stories, quotes, or scenarios"

### Original draft (excerpt)

> Last month I onboarded a client who'd been using a dashboard her previous marketer built in 2022. **It had 23 metrics on it. Only 6 still mapped to decisions she was actually making. We killed 17 of them in week one. By month three her revenue per rep was up 40% — not because we changed the strategy, but because she was finally looking at the right numbers.**

### Why it failed

Every number in the bolded section was invented. There is no client with that scenario in Alex's story bank. The "23 metrics → 6 mapped → killed 17 → 40% revenue lift" arc is a plausible-sounding story the generator constructed because the section needed specific numbers.

The Fabrication Check is a HARD FAIL gate. There is no "rewrite to make it less fabricated" path — fabricated content is removed, not edited. The check works by comparing every concrete detail (numbers, names, timeframes, outcomes) against the story bank and the brand profile reference samples. Anything that doesn't trace back to a source is flagged.

### Rewritten

The post was returned to Step 4 with this rewrite brief:

> "The fabrication check failed on the metrics-killing scenario. The story bank has Sample 5 covering the 'first month is archaeology' insight but no client-specific outcome data. Either: (a) ask the user for a real scenario from their work, or (b) write the post around the *observation* without inventing a specific client outcome."

Option (b) was chosen. The published version (Post 4) tells the archaeology story without claiming any specific client metric. It uses the rule of thumb ("kill metrics nobody's used to make a decision in 60 days") instead of an invented outcome.

### Why this matters

The temptation when generating LinkedIn content is to invent credible-sounding numbers because numbers make posts feel grounded. The fabrication check exists because invented numbers always come back to bite you — a reader who's actually in the field will spot them, a prospect who asks about them will catch the contradiction, and the trust loss is permanent.

The rulebook trades the easy specificity of invented numbers for the harder specificity of real principles. Post 4 is less viral than the invented version would have been. It is also defensible if anyone asks Alex for the data behind it.

---

## What these catches teach you

The rules aren't aesthetic preferences. Each one prevents a specific failure mode:

| Catch | Failure mode prevented |
|-------|------------------------|
| 1 (Tier 1 word) | The reader recognizes you used AI within the first 100 words and discounts everything that follows |
| 2 (polished parallel closing) | The closing reads as a poster line, the reader screenshots it, but nobody DMs you because the post taught them nothing |
| 3 (two-word kicker) | Same failure mode as 2, plus you misrepresent your own position to get a sharper close |
| 4 (brand-specific banned word) | The post sounds like generic SaaS content from any of 1,000 consultants, and your unique voice gets washed out |
| 5 (manufactured vulnerability) | Readers stop trusting your stories because the redemption arcs feel too clean to be true |
| 6 (fabrication) | A real expert in your field spots the invented number, mentions it publicly, and the credibility loss is permanent |

If you read these and think "the rules are too strict," you're the person they're protecting. If you read them and think "I've made every one of these mistakes," you're the person they're for.
