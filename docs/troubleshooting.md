# Troubleshooting

> **Symptoms first.** Find the symptom that matches what you're seeing, then read the diagnosis and the fix. If your issue isn't here, open a GitHub issue with the step number and the exact error or output that surprised you.

---

## Voice and quality issues

### Symptom: Generated posts don't sound like me

**Most likely cause:** Your reference voice samples are too thin, too polished, or too narrow in register.

**Diagnosis:**
- How many samples did you paste? (Need 5 minimum, ideally 5 across different formats — LinkedIn, email, Slack, blog, Twitter)
- Are any of them ghostwritten or AI-assisted? (Those don't count and will pull the system toward the wrong voice)
- Are they all from the same context? (5 LinkedIn posts in the same register won't capture how you actually write outside LinkedIn)

**Fix:**
1. Audit your samples. Replace any that aren't 100% yours.
2. Add 2-3 samples from different formats — if you only have LinkedIn posts, add an email and a Slack message.
3. Re-run the workflow against the updated profile.
4. If the issue persists after 2 sample refreshes, the problem is probably positioning or pillar drift. See the next symptom.

### Symptom: All 4 posts feel like the same post on a loop

**Most likely cause:** Step 4's variation seed isn't being applied, or your pillars are too narrow.

**Diagnosis:**
- Read each post and note the hook angle, length, and structure type. Are 3+ posts using the same combination?
- Check the Step 6 batch variety audit output. Did it actually run? Did it pass?

**Fix:**
1. If Step 6 said "PASS" but the posts feel the same to you, the audit thresholds are too loose for your taste. Re-run the workflow with explicit instructions: "vary post lengths from 150 words to 350 words across the batch, use 3 different hook angles."
2. If your pillars are too narrow (e.g., "vertical SaaS pricing for fintech"), the agent has nowhere to vary. Widen your pillars in your brand profile.
3. If Step 6 didn't run, your agent probably stopped after Step 5. Re-prompt it to continue through Step 6.

### Symptom: Posts use a Tier 1 banned word

**Most likely cause:** Step 5's vocabulary check is being skipped, or the agent rationalized that the word "fits" in context.

**Diagnosis:**
- Open the post. Search for the banned word.
- Open the agent's Step 5 output. Did the vocabulary check actually run, or did the agent skip directly to Step 6?

**Fix:**
1. Re-prompt: "Re-run Step 5 vocabulary check on this post. The banned vocabulary list from rulebook §2.2 is non-negotiable. If you find any Tier 1 or Tier 2 word, replace it with a plain alternative and re-run."
2. If this happens repeatedly, the agent isn't loading the rulebook. Make sure the rulebook is in context (paste it explicitly if needed).

### Symptom: Posts have a "polished closing" feel

**Most likely cause:** Step 5b critic review didn't run, or didn't catch the polished closing pattern.

**Diagnosis:**
- Did Step 5b run with a fresh agent instance, or in the same conversation as Step 4?
- Does each post have a critic review note?

**Fix:**
1. Always run Step 5b in a fresh conversation. Same-conversation critics defend their earlier output.
2. Re-run Step 5b with explicit instructions: "Lens 1 — flag every closing line that uses a polished parallel construction or a two-word kicker. The rulebook §2.8 bans these."
3. See [`examples/anti-pattern-catches/`](../examples/anti-pattern-catches/) — Catches 2 and 3 are worked examples of the polished-closing fix.

### Symptom: Manufactured vulnerability — posts have tidy redemption arcs

**Most likely cause:** The agent is defaulting to LinkedIn-bro story shapes despite the rulebook ban.

**Diagnosis:**
- Read the failure post in your batch. Does the writer (you) come out looking *worse* at the end, or *wiser*?
- Is there a tidy "and now I always [X]" line at the end?

**Fix:**
1. Re-prompt the agent: "This post has the manufactured vulnerability pattern banned in rulebook §2.3. Rewrite it so the failure is messy or unresolved. The writer should look worse at the end, not wiser."
2. Pull a real failure story from your story bank. The example brand profile has 3 failure stories — model your story bank on that ratio.
3. See [`examples/anti-pattern-catches/`](../examples/anti-pattern-catches/) — Catch 5 is a worked example of this exact failure mode.

---

## Workflow execution issues

### Symptom: Workflow refuses to start ("missing voice samples")

**Most likely cause:** Section §5c of your brand profile is empty or has fewer than 1 sample.

**Diagnosis:**
- Open your brand profile. Does §5c have at least one sample?

**Fix:**
1. Paste at least 1 sample (5 is the target). The system will run with 1, but voice match will be weak.
2. If you have no samples available, see [`creating-your-brand-profile.md`](./creating-your-brand-profile.md) — the "what to do if you don't have samples" cold-start workaround.

### Symptom: Step 1 (Performance Review) hard-failed in First-Run Mode

**Most likely cause:** You're running in Returning Mode by accident.

**Diagnosis:**
- Did you tell the agent explicitly to run in First-Run Mode?
- Did you fill in a content audit file and pass it to the agent?

**Fix:**
1. Re-run with: "Run this in First-Run Mode. Skip Step 1 entirely. Run Step 2 from my pillars alone."
2. The Run Modes section at the top of the workflow file documents the difference. Make sure the agent reads it.

### Symptom: Critic loop won't converge — same issue flagged 3 times

**Most likely cause:** The structural issue can't be fixed by line edits — the post needs to be replaced.

**Diagnosis:**
- What did the critic flag? Is it a specific line, or a structural pattern (manufactured vulnerability, off-pillar, fabrication)?
- After 3 loops, the workflow says "escalate to human review." Did you?

**Fix:**
1. If the issue is a single line, ask the generator to rewrite that exact line with a specific alternative.
2. If the issue is structural, scrap the post and replace it. Generate a different topic from the same pillar.
3. If the same issue appears across multiple posts in the batch, your brand profile has a gap. Likely your "always avoid" list is too short or your reference samples don't show the pattern the critic is asking for.
4. After 3 loops, stop the workflow. Don't force a failing post through.

### Symptom: Story prompts in Step 3 feel generic ("tell me about a time you solved a hard problem")

**Most likely cause:** The generator isn't loading your story bank, or your topic plan from Step 2 is too vague.

**Diagnosis:**
- Did the agent reference your story bank in Step 3? Or did it just ask open-ended questions?
- Is your Step 2 topic plan specific enough?

**Fix:**
1. Make sure your story bank is in context (paste it explicitly if needed).
2. Re-run Step 3 with: "Step 3 prompts must reference the specific topic and structure from Step 2's topic plan. Don't ask open-ended 'tell me a story' questions. Ask scenario-specific questions following this format: 'Post [number] is about [topic], framed as [structure]. Have you had a situation where [specific scenario]? Give me 2-3 sentences.'"

### Symptom: Step 6 batch variety audit fails repeatedly

**Most likely cause:** Step 4's variation seed wasn't applied, so the regenerated posts come back with the same shape.

**Diagnosis:**
- What variety metric is failing? (Hook types? Closing types? Length variance? Sentence rhythm?)

**Fix:**
1. Re-run Step 4 for the failed posts with explicit constraints: "Vary the hook angle and length target. The current batch has 3 posts opening with a story. Make this one open with a number or a question. Make it 150 words instead of 300."
2. If variety keeps failing, your pillars or brand profile are too narrow. Step 4 has nowhere to vary into. Widen the brand profile.

---

## Critic-specific issues

### Symptom: Critic isn't catching the polished closings the rulebook bans

**Most likely cause:** Critic isn't loading the rulebook, or is loading only the brand profile.

**Diagnosis:**
- Did you paste the rulebook into the critic conversation?
- Did the critic prompt explicitly reference rulebook sections?

**Fix:**
1. Always paste the rulebook into the critic chat (or pass the file path if your runtime supports it).
2. Use this critic prompt: "You are reviewing 4 LinkedIn posts against the rulebook at [path]. Pay special attention to §2.3 (banned structural patterns), §2.8 (AI sentence-level tells), and §3 (quality gates). For each post, output PASS or REWORK with specific lines flagged."

### Symptom: Critic and generator disagree, generator wins

**Most likely cause:** You're running the critic in the same conversation as the generator.

**Fix:**
- Always spawn a fresh conversation/instance for the critic. The model defends its earlier output otherwise.

### Symptom: I don't have a way to spawn a fresh agent — what now?

**Skip-mode workaround:**
1. Run Step 5 self-checks twice with a 30-minute gap between runs. The second pass catches things the first missed.
2. Read each post yourself, out loud. Does any sentence feel "LinkedIn-y" or corporate? Does any closing sound like a poster line? Trust your instinct.
3. Use a free AI detection tool (GPTZero, Copyleaks, QuillBot) on each post. >60% AI = rewrite the flagged sentences.

This is meaningfully worse than a real critic loop. If you're committing to weekly batches, find a way to run a fresh instance.

---

## Brand profile issues

### Symptom: I filled in everything but the agent still produces generic content

**Most likely cause:** Your reference voice samples are too generic.

**Diagnosis:**
- Are your samples 100-300 words each, or shorter?
- Are they 5 different pieces, or 5 versions of the same thing?
- Are any of them ghostwritten?

**Fix:**
1. Replace any sample shorter than 100 words.
2. Replace any sample that wasn't unambiguously written by you.
3. Pick samples from 5 different contexts (LinkedIn, email, Slack, blog, comment thread) instead of 5 similar contexts.
4. Re-run the workflow.

### Symptom: My pillars feel right but the topics are still bad

**Most likely cause:** Pillars are too broad or the descriptions are too vague.

**Fix:**
1. Read your pillar one-line descriptions out loud. Could you write 10 distinct posts about each pillar from your own experience?
2. If not, the description is too narrow OR too vague. Tighten the boundary.
3. Replace any pillar where the answer is "I'd run out at 3 posts."

### Symptom: I don't know which goal to pick

**Fix:**
- If you want DMs from prospects → inbound leads
- If you want to be cited and invited to speak → thought leadership
- If you have <1,000 followers → grow audience
- If you want a job at a specific company → employer brand
- Anything else: pick the one that matches the question "what would success in 6 months look like?"

You can change it. It's not permanent. Just pick one.

---

## Scheduling issues

### Symptom: LinkedIn API scheduling won't work

**Most likely cause:** You don't have approved Marketing Developer Platform access.

**Fix:**
- Use LinkedIn's native scheduler instead. It's the recommended path for 95% of users. See [`scheduling-options.md`](./scheduling-options.md) for the full rationale.
- The MDP approval process takes weeks and isn't granted to individuals. Don't wait.

### Symptom: I scheduled a post and want to edit it

**Fix:**
- LinkedIn → "Scheduled posts" view → click the post → edit. You can edit until 1 hour before scheduled time.

---

## Output quality issues

### Symptom: First batch was great, fourth batch is going downhill

**Most likely cause:** Story bank is running dry, or the same patterns are being recycled.

**Diagnosis:**
- How many stories are in your story bank? Have you used most of them?
- Are recent batches reusing the same topics from earlier batches?

**Fix:**
1. Add 5-10 new stories to your story bank from the last 4 weeks of work.
2. Run a content audit and add it to your brand profile context. The agent will avoid topics from the last 90 days.
3. Refresh your industry research file. New trends → new angles.
4. If batches keep going downhill after the story bank refresh, your pillars are stale. Reconsider whether one of them needs to change.

### Symptom: My posts are getting low engagement after a few weeks

**Note:** This is a content strategy question, not a workflow question. Possible causes (in order of likelihood):

1. **Posting cadence is too low.** Algorithm rewards consistency. Drop to monthly = drop to invisible.
2. **You're not engaging with comments.** Reply chains drive reach. Posts with 0 author replies underperform posts with 5+ replies.
3. **Your audience is too small.** This system makes content better, not bigger. Audience growth is downstream of content + connections + replies. See modules 16, 17 (advanced — month 2+).
4. **Your topics are too inside-baseball.** If only 50 people in the world care about your niche, your engagement ceiling is hardcoded.
5. **The content actually is generic and the system isn't catching it.** Re-read the example brand profile and example post batch. Compare. Where are the gaps?

---

## When to give up and ask for help

Open a GitHub issue if:
- You hit the same symptom 3 times in a row and the fixes here didn't work
- You found a genuine bug in the workflow or rulebook
- You want a feature added (e.g., a new module, a new structure type, support for another language)
- You have a worked example of the system catching something cool — we want to add it to [`examples/anti-pattern-catches/`](../examples/anti-pattern-catches/)

Don't open an issue for:
- "Make the rulebook less strict" — the rules are opinionated by design
- "Add my favorite LinkedIn growth hack" — the project is built around algorithm-aligned content, not hacks
- "Make it work without voice samples" — voice samples are the core mechanism. There is no workflow without them.
