---
name: grill
description: Interrogate a plan, design or feature idea round by round until every decision is settled, and record the outcome in the docs/ vault (business rules, glossary terms, decisions). Use when the user says "grill me", "погоняй меня", "stress-test this", "poke holes in this plan", or before writing a PRD for anything non-trivial. Not for open exploration with no plan yet (use brainstorm).
---

# Grill

Interview the user relentlessly until you reach a shared understanding, then write the understanding down so the next session does not have to re-derive it.

> Interview method adapted from Matt Pocock's `grilling` and `grill-with-docs` skills (MIT). The docs half is Juz40-specific.

## Part 1 — The interview

Map the plan as a **design tree**: every decision branches into the decisions that hang off it.

Work the tree in **rounds**. The **frontier** is every decision whose prerequisites are already settled — the questions you can ask *now* without guessing at answers you have not heard yet. Ask the whole frontier in one round: number each question and give your recommended answer. Then wait for the user's answers before the next round.

Format a round like this:

```
❓ **Q1** — **<question title>**: <question body, may be several paragraphs, may offer choices>

➡️ <your recommended answer>

---

❓ **Q2** — **<question title>**: <question body>

➡️ <your recommended answer>
```

Each round of answers reshapes the tree: settled decisions push the frontier outward and unblock questions that depended on them. Recompute the frontier and ask the next round. A question whose answer depends on another question still open *in this round* belongs to a later round.

**Finding facts is your job, never the user's.** When a frontier question needs a fact from the environment, go get it — the `docs/` vault first, then `graphify query "<question>"`, then source. Dispatch a sub-agent for anything broad and do not block on it: only the questions downstream of that fact wait, so ask the rest of the frontier now. The **decisions** are the user's: put each to them and wait.

The interview is done when the frontier is empty — every branch visited, nothing silently assumed.

## What to grill about on Juz40

Push hardest where this codebase actually bleeds. At minimum, force an answer on:

- **Roles.** Which of `STUDENT`, `TEACHER`, `CURATOR`, `MANAGER`, `ADMIN`, `HEADTEACHER` sees this, and which of them must *not*?
- **Scope of the unit.** Per student, per group, per stream, per subject, per school, per region? Nearly every Juz40 bug lives in this question.
- **Time.** What happens for closed periods, transferred students, mid-month joins, retroactive changes? Backfills are a recurring source of incidents here.
- **Money.** If payments, discounts, promo codes or surcharges are touched: what is idempotent, and what happens on retry?
- **Notification blast radius.** How many parents/students get a push, SMS or WhatsApp message if this ships wrong?
- **Rollout.** Feature toggle or not? Who can turn it off at 22:00 without a deploy?
- **Migration.** What happens to rows that already exist and do not fit the new rule?

## Part 2 — Write it down

Once the frontier is empty, **and only then**, persist the outcome in the backend `docs/` vault. Follow the vault conventions in `CLAUDE.md`: frontmatter with `tags` and `updated` (absolute ISO date), English prose, domain identifiers verbatim from code, wiki links, no code dumps, ≤ 200 lines.

Write, in this order:

1. **New domain terms** → append to `docs/context/glossary.md`. One line each, in the team's wording.
2. **Business rules the user just decided** → `docs/context/business/<topic>.md`. A rule is a sentence that constrains behaviour ("a student transferred mid-month is billed by the group they left"), with its *why*. Never invent a rule the user did not state.
3. **The decision itself, with alternatives rejected** → a dated section in the same business note, or a new `docs/context/decisions/<slug>.md` if the choice was architectural. Record what you considered and why it lost — that is the part nobody can reconstruct later.

Show the user the diff of what you are about to write before writing it. Anything they did not actually decide goes in an **Open questions** list at the bottom of the note, not into the prose as fact.

## Closing

Report in three lines: what got settled, what got written where, what is still open. Then offer the hand-off to **`prd`** — a grilled plan is exactly the input that skill wants. Do not invoke it yourself, and do not start implementing: the user confirms shared understanding first.
