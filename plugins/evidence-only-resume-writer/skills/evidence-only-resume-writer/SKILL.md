---
name: evidence-only-resume-writer
description: "Write resume and bio copy from real project evidence."
version: 1.0
license: MIT
author: "Zora"
---
# Career positioning documents

Write resume bullets, bios, cover-letter copy, and interview talking points
that are grounded in what the user actually built — not what they remember
building.

## When to Use

- "Write me a bio" / "short bio for a job application" / "resume content"
- "Help me fill out this application" / "what should I put on this form"
- "What should I say about X for a [role type] position"
- "Turn this project into resume bullets"
- "Do I have enough to apply for [role]?"
- A live job application with a text field and a character limit

Do NOT use for: client-facing brand positioning (that's `brand-context`),
product marketing decks (`master-product-deck`), or a full job description
from scratch.

## The core rule: source from artifacts, not from the user's summary

**The user will describe their work in the way they remember it — which is
almost always less specific and more generous than reality.** Your job is to
find the actual artifacts and pull the real numbers out.

**The source ladder — go down until you find real numbers:**

1. **The project's own reference doc** — `the client org.md`, `README.md`, `ARCHITECTURE.md`,
   `SKILL.md`, `CLAUDE.md`. These usually contain the feature inventory,
   stack table, team roster, and known state. Read them first.
2. **Audit reports** — `*-audit-report.md`, `*-feature-study.html`, schema-audit
   outputs. These are where the *hardest* evidence lives (counts of bugs found,
   columns mismatched, rows cleaned).
3. **Session logs / memory files** — `memory/*.md`, `notes/*.md`. These record
   *what actually got built and when*.
4. **The repo itself** — `git log --oneline --author=<user>`, route manifests,
   `package.json` dependency versions, migration filenames.
5. **The canonical knowledge library** — a `trading-skills.md`-style file
   that indexes the codebase by use-case. Read it; it is usually the single
   densest source of quantified accomplishments.

**Then verify against the code before quoting anything.** Every number you
write goes back to a file. If you can't find the artifact, don't claim the
number.

## What actually differentiates a strong bio (and what doesn't)

**Does NOT differentiate:**
- "Passionate about technology" / "results-driven" / "team player"
- Listing frameworks. Everyone lists frameworks.
- "I have experience with X" where X is the job title you applied for.
- Years of experience with no scale attached.

**DO differentiate — in descending order of power:**

1. **A hard technical decision with a specific mechanism.** "One simulator
   backs both the backtest API and the live alert cron, so backtest math
   can't drift from production" is worth more than three bullet points of
   feature lists.
2. **A silent-failure class you diagnosed and fixed at the storage layer.**
   This is the single strongest signal for a *specialist* role vs a
   *generalist* role, and it is rarer than it should be.
3. **A specific number that is not round.** "32+ columns referenced in code
   but absent from the database" beats "we did a schema audit."
4. **A quantified scale artifact.** "50+ badges across 7 categories,"
   "9-rank XP ladder," "45KB canonical reference," "317 skills."
5. **An architecture constraint you worked around.** "Credential encryption at
   rest with Fernet; URL normalization for legacy stored endpoints."

**The framing device that works:** lead the *unglamorous* work. "Most of my
work is the unglamorous kind — fixing silent failures at the storage layer,
adding idempotency, making correctness measurable." A hiring manager reads
that as "this person has seen things break." It also filters out applicants
who only want to demo the AI features.

## Document structure — always produce variants

One request ("write me a bio") has several plausible destinations. Produce a
**menu**, not a single answer:

| Variant | Length | Where it goes |
|---|---|---|
| **A — short** | ~150-165 words | Application form "about you" field |
| **B — long** | ~400 words | Cover letter opener, "tell us about yourself" |
| **C — one-liner** | 1 sentence | Header, tagline, LinkedIn headline |
| **D — bullets** | 8-15 STAR bullets | Resume body |
| **E — keywords** | 25-40 terms | ATS parsing, recruiter search |
| **F — interview pitch** | 60 seconds spoken | Phone screen |

Also always include a **"what I cut and why"** section — it shows the user
what was dropped and lets them redirect.

**Word/character counts must be MEASURED, not estimated.** Write a small
script that strips markdown and counts. Then report the exact number and the
headroom.

```python
import re
def wc(t):
    t = re.sub(r'\*\*|##.*|#.*|---', ' ', t)
    return len([w for w in t.split() if any(c.isalnum() for c in w)])
```

## Character-limit discipline

When the user gives a hard limit (a form field's max), treat it as a hard
constraint:

1. **Aim for ~10% under the limit**, not exactly at it. Headroom lets the
   user paste it without trimming.
2. **Never drop the claim that carries the most weight.** Rank the sentences
   by what a hiring manager needs, then cut from the bottom.
3. **Show the character count in the reply**, with headroom.
4. **Offer optional additions that fit the remaining budget** rather than
   silently using it all. The user decides what to prioritize.

**When the user asks for two additions at once,** produce ONE combined
version that includes both and still fits — don't present them separately and
make them merge it themselves.

## "Fill this out for me" on a platform you cannot write to

When the ask is to populate a third-party field and the agent has no
authenticated write path, the deliverable is **the text plus the exact paste
target**, not an auth investigation. Do not burn the session on credential
archaeology across browser profiles, cookie stores, session files, and API
shapes before delivering something the user could paste in ten seconds.

Order of operations:
1. Read the field's real constraint (max length, whether it counts) from the
   platform — a live `<textarea>` attribute or the update call in the app
   bundle, not a guess.
2. Write the copy and put it in the reply, fenced, with the target named.
3. Only then offer the write path, and name what it needs: a browser session
   the agent can drive, or a one-time approval. If a credential is missing,
   say which one and stop.

The one thing worth a short investigation is the field's **constraint**,
because that shapes the copy. Everything else about getting in is the user's
call.

## Respect the user's actual role title

If the source material says "Senior Developer (contractor)" with a named CEO
who owns the business, write that. Do not upgrade it to "Lead Engineer" or
"Founding Engineer" because it sounds better for a job application.

**Flag the distinction instead of deciding it.** Say: *"I kept your role title accurate as `Senior Developer (Contractor)` — if you want to pitch `Lead` or `Principal` for a future role, that's a framing choice you should make deliberately, not something I should inflate on your behalf."*

The same rule for numbers: if you can't find a user-count or revenue metric,
say so explicitly and name what would strengthen the document. The user
often has it in their head.

## Self-reported credentials go in when he asks for them

A credential the user asserts about his own career — years of experience,
years in a domain — is his to claim. When he asks for it, put it in the
document and flag it in one sentence as the one claim a reader cannot verify
from public work. Do not drop it (it is his), and do not inflate around it
(add "decades" or "industry veteran" as padding).

The flag matters more than it looks: if the rest of the document is
artifact-backed, one unbacked number reads as the weak link, and naming it
first removes the ambush. State it as *his* claim and point at the artifact
that would close it — an old repo, work history, a certification.

## Copy must not restate what the page already shows

A profile page renders its own counts. If the header says "40 skills" and
"Joined Nov 2026", a bio spending characters on "40 published here" is
wasted space a reader reads as filler.

Before delivering, list the facts the target surface already displays
visibly, and remove them from the copy. The freed characters go to
something the page cannot say for itself: what domain the work came from,
what the method is, what the buyer should expect.

This is the same discipline as cutting frameworks from a skill description:
the obvious fact is obvious *because* of where the text sits, not because it
is unimportant.

## Deliverable placement

**Lead with the copy itself, in the chat.** A request that arrives over chat
(iMessage, Telegram, Photon) usually means "I need text I can paste." Put the
recommended version in the reply as a fenced code block — fenced, so it is
literally copy-pasteable with no markdown artifacts — and name the exact
target field and where it lives ("Dashboard → Settings → Profile → Bio").

Files are a supplement, not the deliverable. Write them to the Desktop too
when there is more than one variant to keep, but never make the user open a
file to get the thing they asked for.

```
~/Desktop/<Topic>-Resume-Content.md
~/Desktop/<Topic>-Bio.md
```

Naming convention observed: `<SUBJECT>-<Artifact>.md` — e.g.
`the client org-Resume-Content.md`, `AI-Workflow-Automation-Bio.md`. For a
character-limited variant, also write a plain `.txt` so it's copy-pasteable.

**After writing, mirror the final version back into the main document** so
the two don't drift. If the user later edits one, they're consistent.

## Sourcing gap checklist — name what's missing

Before delivering, check for these and mention the ones that are absent:

- **Scale metrics** — users, revenue, hours saved, volume handled. Absent
  metrics are the single biggest upgrade available to the document.
- **Named employer** — if the bio doesn't say who, recruiters can't route on
  it. Offer to add it.
- **Target-role tailoring** — the same work reads differently for a trading
  role vs a full-stack role vs an AI/product role. Offer to reframe.

## Pitfalls

- **Don't inflate.** "Led" for work where the user was one of several
  contributors, "architected" for work that followed an existing pattern,
  "designed" for work that was mostly integration. The user's credibility is
  the asset; an inflated resume that gets probed in the interview is a net
  negative.
- **Don't write a generic bio with the user's name swapped in.** If the
  bullets would fit any AI engineer, they carry no signal. Every bullet
  should contain something only this person could claim.
- **Don't bury the strongest claim.** The best 1-2 sentences belong in the
  first third, not in a supporting-bullet pile.
- **Don't produce only the format asked for.** "Under 600 characters" means
  deliver the 600-char version AND note what was cut, because the user often
  wants to know what they'd lose.
- **Don't guess a metric that would make the claim stronger.** If you can't
  find it in an artifact, leave a `[GAP: ...]` marker in the deliverable so
  the user fills it in.

## Reference

- `[removed: internal file]` — where the maintainer's career
  evidence lives on disk (the client org docs, the trading-skills library, the schema
  audit), the specific numbers that are verifiable, and the three flags
  (no scale metrics, role-title accuracy, self-reported years of experience).

## Related skills

- `code-audit` — the read-only structured audit of a *project*, which is the
  same evidence-gathering discipline applied to code instead of a career.
- `master-product-deck` — for product/platform narratives, not personal ones.
- `brand-context` — for a client's brand, not the user's own positioning.
