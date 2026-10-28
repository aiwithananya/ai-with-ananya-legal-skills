# Extraction Accuracy Rules

Mandatory for this skill (Case Analysis template). Load during Step 3 and apply to
every proposition recorded in the case note.

**Why this matters here:** a case note is read by someone who will not re-read the
judgment. If the note says the court held X and the court did not hold X, that error
travels into an opinion, a pleading, or a client email, and nobody catches it until
the other side does.

---

## Rule 1: Force Blank Answers When Uncertain

```
EXTRACTION RULE - BLANK ANSWERS:
Only record propositions explicitly stated in the judgment.
If a holding is ambiguous, missing, unclear, or contradicted elsewhere
in the judgment, leave that field BLANK.
For every blank field, add a "Reason" note explaining:
- Why the field was left blank
- Where in the judgment the ambiguity or conflict lies
- What the advocate should read to resolve it
```

**Judgment example — the issue framed:**
Without the rule: "Issue: Whether the arbitration clause survives termination."
With the rule: "Issue: [BLANK] — Reason: the court does not frame the questions
expressly. ¶14 suggests the issue is survival of the clause; ¶31 proceeds as though
the issue is the arbitrator's jurisdiction to decide it. These are different
questions. Advocate should read ¶14 and ¶31 together before relying on either framing."

**Judgment example — the holding:**
Without the rule: "Held: Section 29A timelines are mandatory."
With the rule: "Held: [BLANK] — Reason: ¶52 describes the timeline as mandatory but
¶57 permits extension on sufficient cause. Whether the court treated it as mandatory
with a statutory carve-out, or as directory, is not resolved on the face of the text."

**Judgment example — bench strength:**
Without the rule: "Coram: two judges."
With the rule: "Coram: [BLANK] — Reason: the copy supplied does not carry the coram
line. Bench strength determines precedential weight and must be confirmed from the
official copy before this judgment is cited."

---

## Rule 2: Penalise Wrong Answers Over Blank Answers

```
EXTRACTION RULE - INCENTIVES:
A wrong reading of a judgment is significantly worse than a blank field.
When in doubt, leave it blank and explain why. It is always better to flag
uncertainty than to present an unverified holding as settled.
```

The instinct is to produce a clean, complete case note. Resist it. A case note with
four confident holdings and one honest blank is more useful than five confident
holdings where one is invented. Every advocate knows the difference; only one of the
two versions survives the other side reading the judgment.

---

## Rule 3: Label Every Value as Extracted or Inferred

```
EXTRACTION RULE - SOURCE LABELING:
For each recorded item, indicate whether it was:
- EXTRACTED: appears in the judgment. Cite the paragraph number.
- INFERRED: derived, interpreted, classified or calculated. State the basis.

The advocate will verify all INFERRED items. EXTRACTED items with
paragraph cites can be trusted with normal review.
```

**Worked example:**

| Field | Value | Source | Evidence |
|---|---|---|---|
| Court | Supreme Court of India | EXTRACTED | Cause title |
| Coram | 3 judges | EXTRACTED | Coram line, p.1 |
| Date | 14 March 2024 | EXTRACTED | Cause title |
| Disposition | Appeal allowed, matter remanded | EXTRACTED | ¶94 |
| Issue framed | Whether s.34 permits modification of an award | EXTRACTED | ¶11, numbered by the court |
| Second issue | Whether the delay was condonable | INFERRED | Not framed by the court, but ¶38–44 decide it. Treating it as an issue is an interpretation |
| Ratio | ¶61 proposition | INFERRED | Classification as ratio is analytical, applying the necessity test. The proposition itself is EXTRACTED from ¶61 |
| Precedential weight | STRONG | INFERRED | Based on bench strength and ratio classification, without subsequent-history verification |
| Still good law | [BLANK] | — | Cannot be determined from the judgment text |

Note the pattern: the court's words are EXTRACTED; every classification this skill
applies to them is INFERRED. Keep that distinction visible. It lets the reader trust
the citations at a glance and spend their review time on the analysis, which is where
the errors will be.
