---
name: judgment-analyser
description: >
  [OUTCOME]: Reads any Indian judgment or order the way a senior lawyer reads it and
  produces a formatted .docx case note structured as Facts, Issues, Rule, Arguments,
  Conclusion — with the ratio decidendi separated from obiter dicta, the precedential
  weight assessed under Article 141 and bench-strength rules, and every proposition
  pin-cited to a paragraph number.
  [TRIGGER]: Activates when the user says "analyse this judgment", "read this
  judgement", "case note", "brief this case", "what is the ratio", "FIRAC this",
  "summarise this order", "digest this judgment", or "/judgment-analyser", or
  uploads a judgment, order or award and asks what it holds.
  [ANTI-TRIGGER]: Does NOT activate for contract or NDA review, drafting pleadings,
  petitions or notices, statutory research with no judgment in hand, headnote-only
  summaries where the full text is unavailable, or non-adjudicatory documents.
---

# Judgment Analyser

## Purpose

Read a judgment the way a senior lawyer reads it — not to summarise what the court
said, but to work out what it decided, how much of that binds anyone, and how it can
be used or resisted in the next matter.

A junior reads a judgment front to back and reports the conclusion. A senior reads the
disposition first, works backwards to the reasoning that was necessary to reach it,
and treats everything else as commentary. This skill enforces the second approach.

## Before You Start

1. Read `references/firm-context.md` for jurisdiction, formatting standards and
   quality-review preference. If it is still the blank template, ask for the
   jurisdiction and proceed with Indian defaults.
2. Check whether the current directory contains a `claude.md`. If it does, read it for
   matter context — parties, claims, the issue the judgment is being read for — and
   use it to pre-fill inputs and skip questions it already answers.
3. Read `learnings.md` in this skill's folder and apply every rule listed there.
4. Ask once: "Do you have a sample case note in the format you like? Upload it and
   I'll match its headings and layout." If one is uploaded, mirror its structure,
   headings and layout. Keep the Ratio and Obiter table, the Weight and Use section
   and the paragraph pin-cites even if the sample has none: those are the substance
   of this skill, not formatting.

## Step 1: Locate and Verify the Source

Confirm you have the full text, not a headnote, digest or news report.

- Headnotes are written by reporters, not judges. They are not the judgment and are
  not binding. Never build an analysis on a headnote alone. If only a headnote is
  available, say so and stop.
- Identify: court, coram (names and number of judges), date of judgment, case number,
  neutral citation, and reported citations if visible.
- Note whether the text is a judgment, an interim order, a consent order, or an
  award. Interim and consent orders carry little or no precedential value; say so
  early rather than at the end.

If the judgment is not in context, read it from disk. See
`references/indian-judgment-anatomy.md` for what to look for in each section.

## Step 2: Confirm the Reading Brief

Ask the user (skip anything `claude.md` already answers):

1. **Why are you reading this judgment?** Options: understanding the law on a point /
   supporting a position in a live matter / resisting the other side's reliance on it /
   advising a client / content or teaching / general awareness
2. **Is there a specific issue or provision you care about?** Free text. If given,
   the analysis foregrounds that issue and treats the rest in short form.
3. **Depth?** Options: full case note (default) / one-page brief / ratio only

## Step 3: Read It Like a Senior

Read `references/senior-reading-method.md` and follow the sequence in it. In short:

1. Read the disposition or operative order **first**.
2. Work backwards to identify what the court actually had to decide to reach it.
3. Separate the issues the court decided from the issues it merely discussed.
4. Note what the court did *not* decide, and what it expressly left open.
5. Only then read the arguments — knowing the outcome tells you which arguments
   mattered and which the court ignored.

Then read `references/extraction-accuracy-rules.md` and apply all three rules to
every proposition you record:

- Leave a field **[BLANK]** with a stated reason where the judgment is ambiguous,
  silent or internally inconsistent (Rule 1).
- A wrong reading is worse than a blank one. When in doubt, blank it (Rule 2).
- Label every proposition **EXTRACTED** (appears in the text, with paragraph number)
  or **INFERRED** (derived, interpreted or calculated — with the basis stated) (Rule 3).

## Step 4: Separate Ratio from Obiter

This is the analytical core of the skill. Read
`references/ratio-and-obiter.md` and apply the tests in it.

Record for each proposition of law in the judgment:

| Proposition | Para | Classification | Basis |
|---|---|---|---|
| ... | ¶47 | RATIO / OBITER / [BLANK] | Necessary to the disposition because... |

Where the classification is genuinely arguable, mark it **CONTESTABLE** and set out
both readings. Do not resolve a hard ratio question silently.

## Step 5: Assess Precedential Weight

Read `references/precedential-weight-india.md` and complete the weight assessment:
bench strength, Article 141 status, binding vs persuasive on which courts,
per incuriam or sub silentio concerns, and subsequent history.

Use this three-band flag on the overall weight of the judgment:

- **STRONG** — larger bench or settled position, squarely on the point, no adverse
  subsequent history visible on the face of the record.
- **QUALIFIED** — binding or persuasive but limited: distinguishable facts, narrow
  issue, split or concurring reasoning, or a coordinate-bench conflict.
- **FRAGILE** — per incuriam risk, sub silentio, obiter being relied on as ratio,
  interim or consent order, or a pending reference to a larger bench.

**Mandatory caveat on every weight assessment:** subsequent history cannot be
verified from the four corners of the judgment. State expressly that the judgment
must be checked on SCC OnLine, Manupatra or the court's own site for later
overruling, doubting, or a pending reference before it is cited.

## Step 6: Build the Case Note

Structure the output as Facts, Issues, Rule, Arguments, Conclusion — in the order and
form set out in `assets/case-note-template.md`. Every substantive line carries a
paragraph pin-cite (¶ numbers, not page numbers).

Two sections sit outside FIRAC and are always included:

- **Ratio and Obiter** — the table from Step 4, placed after Rule.
- **Weight and Use** — the assessment from Step 5, plus how the judgment cuts for and
  against the position identified in Step 2.

## Step 7: Produce the .docx

Read the docx skill before generating the file. Apply the uploaded sample's
format if there is one, otherwise the formatting standards in
`references/firm-context.md`. If the `indian-doc-formatter` skill is
available, hand the draft to it for final formatting rather than formatting by hand.

Filename: `Case Note - [Short Case Name] - [Court] - [YYYY-MM-DD].docx`

## Step 8: Quality Review (mandatory)

Firm preference is **Always**. Spawn a fresh sub-agent with no prior context. Give it
only the case note, the source judgment, and `references/quality-review.md`. Present
its findings to the user alongside the case note — do not silently absorb them.

## Step 9: Log Learnings

Ask: "Did the case note meet your expectations? Anything to improve for next time?"
Write anything useful to `learnings.md` under `## Rules` or `## Observations`.

---

## Legal Compliance Guardrails (mandatory, never omit)

1. **Cite the source.** Every proposition carries a paragraph number from the
   judgment. Never state what a judgment holds from memory or from a headnote.
2. **Flag uncertainty.** Where the reading is not confident, mark it
   `[REQUIRES VERIFICATION]` and say what would resolve it.
3. **This is not legal research.** The skill reads one judgment placed in front of
   it. It does not confirm whether that judgment is still good law, does not search
   for later authority, and must never present itself as having done either.
4. **Preserve the court's words.** Quote key holdings verbatim with paragraph
   numbers. Do not paraphrase operative language into a cleaner sentence.
5. **Attorney review required.** Every output opens with:
   `[REQUIRES ADVOCATE REVIEW — not to be cited or relied upon without verifying
   current status of the judgment]`

## Reference Files

- `references/senior-reading-method.md` — the reading sequence and what to look for
- `references/indian-judgment-anatomy.md` — structure of Indian judgments, citation
  conventions, headnote warnings, concurring and dissenting opinions
- `references/ratio-and-obiter.md` — the tests for separating ratio from obiter
- `references/precedential-weight-india.md` — Article 141, bench strength, per
  incuriam, sub silentio, binding scope
- `references/extraction-accuracy-rules.md` — blank answers, incentives, source labels
- `references/quality-review.md` — sub-agent checklist
- `assets/case-note-template.md` — the output structure
