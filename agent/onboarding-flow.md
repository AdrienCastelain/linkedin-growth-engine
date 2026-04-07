# Onboarding Flow — Interactive Brand Profile Setup

> **You are an AI following this script** to walk a new user through filling in their brand profile. This is the file `CLAUDE.md` routes you to when a user is in NEW USER mode.
>
> **Goal:** Take the user from "I just installed this" to "I have a complete `_user/my-brand-profile.md` and I'm ready to run the workflow," in 15-25 minutes of guided dialogue.
>
> **Format:** Ask one question at a time. Wait for the answer. Capture it. Move to the next question. **Never dump the whole template on the user and ask them to fill it in themselves.**

---

## Pre-flight (do this before asking any questions)

1. **Resolve `USER_FILES_DIR`.** Per `CLAUDE.md` Step 2a, user files live in a `_user/` subfolder:
   - If your CWD is the cloned LGE repo (CLAUDE.md present in CWD), `USER_FILES_DIR = ./_user/`
   - If your CWD is somewhere else (skill installed at `~/.claude/skills/linkedin-growth-engine/`, user is in their own project folder), `USER_FILES_DIR = ./_user/` (still the user's CWD, just a different absolute path)
   - Multi-brand users have one `_user/` per brand folder; always use the current CWD's `_user/`

2. **Confirm runtime capability.** Can you write files directly?
   - Yes (Read/Write tools available) → You will write the brand profile to `USER_FILES_DIR/my-brand-profile.md` as you go. Create the `_user/` directory first if it doesn't exist (`mkdir -p _user/` or equivalent). Tell the user: *"I'll save your answers to `_user/my-brand-profile.md` as we go. You don't need to copy anything. The `.gitignore` already excludes the `_user/` folder so your data won't accidentally get committed."*
   - No (chat-only runtime) → You will build the brand profile content in your head and present it at the end. Tell the user: *"At the end I'll give you the full brand profile as markdown. Save it as `_user/my-brand-profile.md` in whatever folder you're working from. Create the `_user/` folder if it doesn't exist."*

2. **Set expectations on time and the hardest section.**
   > "This takes about 15-20 minutes if you have 5 things you've already written somewhere accessible (LinkedIn posts, emails, Slack messages, blog excerpts — anything in your real voice). If you have to hunt for them, expect 30-45 minutes. The voice samples section is the most important. Want to grab them now before we start, or work through the other sections first while you think about it?"

3. **Wait for their answer.** Then proceed to Question 1.

---

## Question 1 — Positioning

**Ask:**
> "First question: in one sentence, who do you help and what do you help them do? The format I'd suggest is 'I help [WHO] do [WHAT] so they can [OUTCOME].' Don't overthink it — we can refine later."

**Examples to give if they're stuck:**
- *"I help pre-Series A SaaS founders build their first repeatable GTM motion so they can stop guessing what's working."*
- *"I help senior engineers transition into engineering management so they can lead the teams they were tired of complaining about."*
- *"I help indie game developers ship their first paid title so they can get out of side-project purgatory."*

**Push back on weak answers:**
- If they say something like *"I'm a fractional CMO"* → that's a job title, not positioning. Ask: *"What specific outcome do your clients hire you for? What changes for them after working with you?"*
- If they say *"I help businesses grow"* → too vague. Ask: *"What kind of businesses, and what's the specific bottleneck you solve?"*
- If they hedge with *"It depends..."* → tell them: *"Pick the version that's true 80% of the time. We can refine later. The point is to have something specific for the system to work with."*

**Capture:** Write their final answer to Section 1 of the brand profile file.

---

## Question 2 — ICP

**Ask:**
> "Now picture the specific person whose desk you want to land on. Not a market segment — one real person you've helped before, or one you wish you could help. Who are they? Role, company stage, and the specific thing they're stuck on."

**Examples to give:**
- *"Solo founder, pre-Series A SaaS, can't tell which growth channel is actually working."*
- *"Senior engineer at a 50-person startup who just got promoted to manager and is drowning in 1:1s."*
- *"Indie developer who's shipped 3 free projects and is too scared to charge for the fourth."*

**Push back if they're vague:**
- If they say *"founders and operators"* → too broad. Ask: *"At what stage? And what's the one thing keeping them up at night that you can fix?"*
- If they say *"anyone who needs help with X"* → unhelpful. Ask: *"Pick one. The most common version of your client. Describe them."*

**Capture:** Write to Section 2 of the brand profile file.

---

## Question 3 — LinkedIn Goal

**Ask:**
> "What do you want LinkedIn to do for you? Pick exactly one — I know that's hard, but the system needs one primary goal to optimize for. Your options:
>
> - **Inbound leads** (you want DMs from prospects asking to work with you)
> - **Thought leadership** (you want to be cited, invited to speak, recognized as a name in your space)
> - **Grow audience** (you want followers — usually because you're starting from a low base)
> - **Attract investment** (you want investors to find you)
> - **Employer brand** (you want candidates to want to work with you)
> - **Speaking / media** (you want to get on stages and podcasts)
> - **Launch support** (you have a product launching and want pre-launch attention)
> - **Community growth** (you're building a community and want members)
>
> Which one matches what you want from LinkedIn over the next 6 months?"

**If they hesitate or pick multiple:**
- *"Pick the one that matters most for the next 6 months. You can change it later. Two goals at once means the system can't optimize for either."*

**Capture:** Write to Section 3.

---

## Question 4 — Content Pillars

**Ask:**
> "Now the topics. What 3-4 things could you talk about for the next 12 months without running out of stuff to say from your own experience? These become your content pillars — every post you generate will fit one of them."

**Quality test to share:**
> "Here's the test: for each pillar, ask yourself — could I write 10 distinct LinkedIn posts about this from my own experience without making anything up? If not, the pillar is too narrow. Either widen it or replace it."

**Push back on generic answers:**
- *"Marketing"* → too broad. Ask: *"What kind of marketing, and what's your specific angle on it?"*
- *"Leadership"* → too broad. Ask: *"Leadership in what context? For whom? Based on what experience?"*
- *"AI"* → too broad and too crowded. Ask: *"AI applied to what? Your angle has to be specific or you'll be lost in the noise."*

**Examples to give of well-formed pillars:**
- *"Pricing and packaging for early-stage vertical SaaS — the actual mechanics of charging more without losing customers."*
- *"Founder-led marketing for technical founders — what works specifically when the founder is the one writing."*
- *"The fractional engineering manager life — pricing, scope, what works, what doesn't, the boring honest version."*

**Capture all 3-4 pillars** to Section 4 with one-line descriptions for each.

---

## Question 5 — Voice samples (the hardest section)

**Set the stage:**
> "OK, this is the most important section. The system is going to use the voice samples you give me to calibrate everything: word choice, sentence rhythm, formality, contractions, your signature phrases. Without good samples, the output drifts toward generic AI voice — which is exactly what we're trying to avoid.
>
> I need 5 things you've actually written. 100-300 words each, ideally from different formats (LinkedIn posts, emails, Slack messages, blog excerpts, X replies). They have to be 100% you — not ghostwritten, not edited by a marketer, not 'helped' by ChatGPT. Anything written by someone else in your voice doesn't count.
>
> Take a few minutes to find them. Tell me when you have at least 3 ready (we can start with 3 and add more later)."

**Wait for the user to confirm they have samples ready.**

**Then ask for them one at a time:**

> "Paste me the first one. Don't edit it. Don't polish it. Just paste it verbatim — even if it's casual, has typos, or feels rough. The roughness is the signal."

**After each sample, acknowledge briefly and ask for the next:**

> "Got it. Sample [N]. Next one when you're ready."

**Push back gently if a sample looks ghostwritten or AI-generated:**
- If a sample reads as polished marketing copy → ask: *"Did you write this yourself, or did a marketer / ghostwriter / AI help with it? I need samples that are 100% your raw voice for the calibration to work."*
- If a sample has obvious AI tells (delve, leverage, "in today's landscape") → ask: *"This one has some patterns the system bans. Was it AI-assisted? If yes, give me a different one."*

**When you have at least 3 samples** (5 is the target):
> "We have [N] samples. The system can run with 3 but works better with 5. Can you find [5-N] more, or should we proceed with what we have? Up to you."

**Capture all samples** to Section 5 of the brand profile file, verbatim.

---

## Question 6 — Always avoid

**Ask:**
> "Last section. What words or phrases would you never naturally use? The rulebook already bans the obvious AI tells (delve, leverage, harness, etc.) but I want to know what's specific to *you*. Words that make you flinch when other people use them. Industry jargon you've sworn off. Old marketing-speak from a previous job.
>
> Give me 3-5. They can be single words, phrases, or whole patterns."

**Examples to give:**
- *"I never say 'journey' or 'unpack' or 'circle back.'"*
- *"'Best practices' and 'thought leader' and 'value-add' are all banned for me."*
- *"I won't say 'crushing it' or 'playbook' — both feel hollow."*

**Reassure them on duplication:**
- *"Don't worry if you list a word the rulebook already bans. Duplicates are harmless. The point is to capture anything that flinches when you read it."*

**Capture** to Section 5d of the brand profile file.

---

## Wrap-up — Confirm and route to workflow

**Summarize the brand profile back to them:**

> "Here's what I've captured:
>
> **Positioning:** [their answer]
> **ICP:** [their answer]
> **LinkedIn Goal:** [their answer]
> **Pillars:** [list]
> **Voice samples:** [N] samples saved
> **Always avoid:** [list]
>
> Look right? Anything you want to change before we move on?"

**Wait for confirmation.**

**If they want to change something** → ask which section, update it, re-summarize.

**If they confirm:**

> "Great. Your brand profile is saved at `_user/my-brand-profile.md` in your working directory. [If you wrote the file directly, confirm the path. If not, give them the markdown content to save manually.]
>
> Now — want to run your first content batch? It'll take about 30-45 minutes. I'll generate 4 LinkedIn posts based on your pillars, walk through quality checks, run an independent critic review, and give you the final batch ready to schedule. I'll pause once or twice along the way to ask you for input — like a real story to ground a post in.
>
> Ready?"

**If yes** → route to **Workflow execution** (CLAUDE.md Step 5). Load `./CONTENT-GENERATION-WORKFLOW.md` and run it in First-Run Mode.

**If no** → respect it. *"No worries. When you're ready, just say 'let's run the workflow' and we'll pick up here."*

---

## Edge cases

### User has fewer than 3 voice samples and can't find more
- Tell them: *"We can do a cold-start workaround. I'll ask you to write 3 short pieces (200 words each) on a topic from each of your pillars, in your natural voice. Don't polish them. They become your starting samples. After your first batch, swap them for real published content."*
- Walk them through it: one prompt per piece, capturing the output as samples.

### User says "just fill it in for me"
- Refuse politely. *"I can't fill in your voice samples for you — they have to be your actual writing or the calibration won't work. For the other sections, I can suggest defaults if you're stuck, but the voice samples are non-negotiable."*

### User abandons mid-onboarding
- Save what you have so far. Tell them: *"I've saved your progress at `_user/my-brand-profile.md`. When you come back, we can pick up where we left off."*
- If you're chat-only and can't write files, give them the partial markdown and tell them to save it.

### User says they've used the project before but no `_user/my-brand-profile.md` exists
- They might be in a different working directory than last time. Ask: *"Are you in the same folder you used last time? Your brand profile is saved per-directory. If you're somewhere else, navigate back or we can rebuild it here."*

### User wants to skip sections
- Positioning, LinkedIn Goal, Pillars, and Voice samples are all required. Voice samples is a HARD STOP. The others are technically possible to skip but the output quality will degrade. Tell them: *"You can skip [section X] but it'll affect [specific downstream behavior]. Want to skip anyway?"*

---

## After onboarding

The user now has a brand profile and is in **FIRST-RUN READY** mode. Route them to workflow execution per CLAUDE.md Step 5. The workflow will run in First-Run Mode automatically because they have a brand profile but no content audit.

After Batch 1 ships, they should come back next week. At that point, encourage them to: (1) add 2-3 more voice samples based on what felt off in Batch 1, (2) start a story bank using the full template, (3) note any words they want to add to the avoid list. Iteration is the compounding mechanism.
