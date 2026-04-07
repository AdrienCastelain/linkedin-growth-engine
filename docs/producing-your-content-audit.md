# Producing Your Content Audit

> **What this is:** A guide to filling in [`templates/content-audit-template.md`](../templates/content-audit-template.md) — a 30-day inventory of your published LinkedIn posts. The workflow uses this in Returning Mode to (a) avoid repeating topics you've already covered, (b) feed performance data into next week's batch, and (c) flag topic fatigue patterns before they hurt reach.
>
> **Who this is for:** Users moving from First-Run Mode to Returning Mode (typically month 2). First-time users skip this entirely.
>
> **Time:** 15-30 minutes for the first audit. ~10 minutes monthly to refresh.

---

## Why you need a content audit

Without an audit, the workflow can't know what you've already posted. This causes three failure modes:

1. **Topic repetition.** You post about the same thing every 3 weeks because the agent has no memory of what's gone live.
2. **Pattern blindness.** The agent can't see which hooks, closings, or structures performed best last month, so it can't bias toward what's working.
3. **No recovery from underperformance.** If a pillar tanked last month, the agent has no signal to reduce it.

The content audit is the structured input that turns the workflow from "generates posts in a vacuum" to "generates posts that learn from your actual track record."

---

## When you need it

**You don't need a content audit in First-Run Mode.** First-Run Mode skips Step 1 entirely and runs Step 2 from your pillars alone. If you're shipping your first batch, skip this doc and come back after 30 days.

**You need a content audit in Returning Mode.** Returning Mode is when you've published at least 4 posts and have 30+ days of LinkedIn analytics. The workflow's prerequisites block requires a content audit file that's <30 days old.

**Refresh cadence:** Monthly. Add your new posts to the audit at the end of each month. Re-calculate aggregates. Update the topic coverage list.

---

## How to pull the data from LinkedIn

LinkedIn does not expose post analytics via a public API for individual users. The MDP API requires approved access (see [`scheduling-options.md`](./scheduling-options.md)), which is rarely granted to individuals. Your only realistic path is the manual export route.

### The 5-minute manual export

1. **Open LinkedIn** → click your profile picture → "View profile"
2. **Click "Analytics"** at the top of your profile
3. **Click "Posts"** in the analytics dashboard
4. **Set the date range** to the last 30 days (or "Past month")
5. For each post, **note the metrics:**
   - Date published
   - Reactions count (the number next to the like icon)
   - Comments count
   - Reposts count
   - Impressions (if shown — only available for some accounts)

LinkedIn shows a list of every post you've published in the date range with engagement counts. You can also click each post to see a detailed breakdown.

**What to record:** date, pillar, structure, topic (5-10 word description), reactions, comments, reposts, and any notes (DMs received, screenshots, lead inquiries attributed).

### The slower but cleaner export

If you want a structured export:

1. **LinkedIn Sales Navigator users** — Sales Navigator shows post analytics with more detail and supports CSV export from the campaign analytics view (if you're using Sales Navigator's content tools).
2. **Third-party scheduling tools** — Buffer, Hootsuite, and similar tools that have API access often provide post-level analytics dashboards. If you've been using one of these to schedule, export from there.
3. **Browser screenshot + manual transcription** — slower but works. Take a screenshot of each post's analytics view and transcribe the numbers into the template.

**What you can't get:**
- Impressions (unless your account has the analytics tier that shows them)
- Click-through data on first comments
- Reach attribution beyond reactions/comments/reposts

The audit is good enough with what LinkedIn shows you. Don't wait for perfect data.

---

## Filling in the template

Open [`templates/content-audit-template.md`](../templates/content-audit-template.md). It has these sections:

### Audit Period

Set the date range. Should be ~30 days.

```markdown
**From:** 2026-03-08
**To:** 2026-04-07
**Total posts published:** 18
```

### Post Inventory

One row per post. Use the table format in the template:

```markdown
| Date | Pillar | Format | Hook | Close | Topic | Reactions | Comments | Reposts | Notes |
|------|--------|--------|------|-------|-------|-----------|----------|---------|-------|
| 2026-03-09 | GTM strategy | text | number | C | Channel debug loop | 47 | 8 | 2 | 1 DM, ICP fit |
| 2026-03-11 | Founder-led marketing | text | contrarian | A | Founders shouldn't post 3x/week | 71 | 14 | 5 | 2 DMs, 1 booked call |
```

**For pillar:** use the exact pillar names from your brand profile. Consistency matters.

**For format:** text / text+image / carousel / poll / video / multi-image

**For hook style:** number / story / contrarian / question / scene

**For close type:** A (question) / B (incomplete statement) / C (practical nudge)

**For topic:** 5-10 words. Specific enough that you'd recognize it later but short enough to scan.

**For Notes:** anything that doesn't fit a column. DMs received, screenshots taken, lead inquiries, comments from notable people.

### Aggregate Metrics

Calculate these after filling the inventory:

```markdown
| Metric | Value |
|--------|-------|
| Total posts | 18 |
| Total reactions | 642 |
| Total comments | 89 |
| Total reposts | 34 |
| Average reactions per post | 35.7 |
| Average comments per post | 4.9 |
| Best-performing post | "Channel debug loop" (47 reactions, 8 comments) |
| Worst-performing post | "On the importance of branding" (12 reactions, 1 comment) |
```

A quick formula in Google Sheets or Excel handles this in 30 seconds. Or just eyeball it.

### Pillar Distribution Check

Tally how many posts fell in each pillar. Compare against your target weights from your brand profile (Section 4).

```markdown
| Pillar | Posts in audit period | % of total | Target weight | Variance |
|--------|----------------------|------------|---------------|----------|
| GTM strategy | 8 | 44% | 40% | +4 |
| Founder-led marketing | 5 | 28% | 25% | +3 |
| Category positioning | 3 | 17% | 25% | -8 |
| Fractional CMO life | 2 | 11% | 10% | +1 |
| Off-pillar | 0 | 0% | <5% | OK |
```

**Flag:** Any pillar more than 10 percentage points off target. Either the content drifted or the target weights need updating.

### Topic Coverage

List every distinct topic/sub-topic covered in the audit period. The workflow uses this to avoid repeating topics in the next batch.

```markdown
- Channel selection by debug loop speed
- Founder-led marketing isn't 3 posts/week
- Pricing anchoring on competitor data
- The first month of fractional engagement is archaeology
- Why most marketing hires fail in first 90 days
- Cohort data hiding inside MRR data
- Enterprise sales calls and the silence test
- ...
```

**Topic fatigue check:** Has any sub-topic appeared more than twice in the last 14 days? If yes, flag it. Either delay the next post on that sub-topic or vary the angle significantly.

### Pattern Notes (free-form)

The most useful section for the workflow's Step 1 (Performance Review). Things you noticed that don't fit a column:

```markdown
**What's working:**
- Number-led hooks averaged 2x reactions vs story-led hooks
- Type B closings drove 3x more comments than Type A
- Posts under 200 words underperformed posts in the 250-350 range

**What's not working:**
- The "Fractional CMO life" pillar is 50% below target reach. Posts feel naval-gazing.
- Tuesday posts outperform Friday posts 2:1

**Surprises (good and bad):**
- The post about silence in sales calls got 4x normal DMs (wasn't expected)
- The carousel post got fewer reactions but 3x reposts
```

This is the section the agent reads to make next month's plan smarter.

### Audit Freshness

Make sure the file's "Last refreshed" date is within 30 days. The workflow rejects audits older than 30 days.

```markdown
**Last refreshed:** 2026-04-07
**Refresh due:** 2026-05-07
```

---

## Common mistakes

1. **Skipping topics with 0 engagement.** Don't. Low-engagement posts are signal too — they tell you what's not working. The audit needs every post, not just the wins.
2. **Using vague topic descriptions.** "Some thoughts on marketing" doesn't help the agent avoid duplicates. Be specific: "Why most B2B homepages fail to convert post-PMF."
3. **Letting the audit go stale.** A 60-day-old audit is worse than no audit because the workflow trusts it. Refresh monthly.
4. **Forgetting to recalculate aggregates after adding posts.** The aggregate table is what feeds Step 1's performance summary. If it's stale, Step 1 produces stale recommendations.
5. **Counting comments from your own replies.** Don't. You want the count of *external* comments, not the total thread count.

---

## Before you ship a Returning Mode batch

Quick checklist:

- [ ] Audit period covers the last 30 days
- [ ] Every post is in the inventory table
- [ ] Aggregate metrics are recalculated
- [ ] Pillar distribution is checked against your brand profile target weights
- [ ] Topic coverage list is updated
- [ ] Pattern notes section has at least 2-3 observations
- [ ] Last refreshed date is current

If any item is incomplete, fix it before running the workflow. Step 1 depends on this file being current and accurate.
