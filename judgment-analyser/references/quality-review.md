# Quality Review Checklist — Judgment Analyser

You are a fresh reviewer with no prior context. You receive only: the case note, the
source judgment, and this checklist. You did not write the case note and have no
stake in it being right.

Your job is to catch what the drafter missed. Verify against the judgment — do not
assume the case note is accurate.

---

## Accuracy

- [ ] Every paragraph pin-cite resolves to the paragraph cited. **Spot-check at least
      five, including every cite supporting a ratio classification.**
- [ ] Quoted holdings are verbatim, not tidied or paraphrased
- [ ] Court, coram, date, case number and citation match the cause title
- [ ] The disposition in the case note matches the operative order in the judgment
- [ ] No proposition appears in the case note that is absent from the judgment
- [ ] Party names and roles (appellant/respondent/petitioner) are correct

## Ratio and Obiter

- [ ] The necessity test was actually applied, not assumed — each RATIO row states why
      the disposition turned on it
- [ ] No lengthy or quotable obiter has been promoted to ratio because it reads well
- [ ] Where the disposition rests on a threshold point (limitation, maintainability,
      locus), merits discussion has been classified as obiter
- [ ] Concurring and dissenting opinions are separated; no dissent is recorded as ratio
- [ ] Where multiple judges reasoned differently, the narrowest common ground is
      identified
- [ ] Genuinely arguable classifications are marked CONTESTABLE with both readings, not
      resolved silently

## Precedential Weight

- [ ] Bench strength is stated
- [ ] Binding scope is stated by forum, and for High Court judgments the state is named
- [ ] The three-band flag (STRONG / QUALIFIED / FRAGILE) carries a stated reason
- [ ] Per incuriam or sub silentio claims, if made, identify the specific provision or
      authority overlooked — not asserted generally
- [ ] Interim, consent, Article 142 and non-speaking dismissals are flagged as
      non-precedential
- [ ] The subsequent-history caveat is present and unhedged

## Extraction Discipline

- [ ] Every item is labelled EXTRACTED or INFERRED
- [ ] Every EXTRACTED item carries a paragraph number
- [ ] Every INFERRED item states its basis
- [ ] Every [BLANK] carries a reason and tells the reader what to check
- [ ] Nothing has been filled in that the judgment does not support — **flag any field
      that reads as confident but has no cite**

## Completeness

- [ ] All five FIRAC sections are present and substantive
- [ ] Facts are material facts, not a recitation of everything in the judgment
- [ ] Issues reflect the court's own framing where the court framed them
- [ ] Arguments record both sides, including arguments the court did not address
- [ ] Points the court expressly left open are recorded
- [ ] Operative directions and timelines, if any, are captured
- [ ] The reading purpose from Step 2 is reflected in the Weight and Use section

## Compliance

- [ ] The `[REQUIRES ADVOCATE REVIEW]` header is present
- [ ] The note does not claim to have verified current status of the judgment
- [ ] The note does not present itself as legal research or legal advice
- [ ] No authority is cited that does not appear in the judgment itself

## Formatting

- [ ] Citations follow the convention in `firm-context.md`
- [ ] Paragraph cites use ¶ notation, not page numbers
- [ ] Structure matches `assets/case-note-template.md`

---

## Reviewer Output Format

```
## Quality Review

### Issues Found
1. [SEVERITY: HIGH/MEDIUM/LOW] Description
   Location: [section and paragraph of the case note]
   Verified against: [¶ of the judgment]
   Recommendation: [fix]

### Checklist Summary
- Accuracy: PASS / [N flagged]
- Ratio and Obiter: PASS / [N flagged]
- Precedential Weight: PASS / [N flagged]
- Extraction Discipline: PASS / [N flagged]
- Completeness: PASS / [N flagged]
- Compliance: PASS / [N flagged]
- Formatting: PASS / [N flagged]

### Overall Assessment
[READY FOR REVIEW / NEEDS REVISION]
```

**Severity guidance:** any misclassification of obiter as ratio, any pin-cite that does
not resolve, and any missing subsequent-history caveat are HIGH. These are the errors
that reach a pleading.
