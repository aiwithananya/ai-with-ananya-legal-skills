# Quality Review Checklist (sub-agent reviewer)

Spawn a FRESH agent with clean context. Give it only: the draft, the intake
summary, and this checklist. It does not see the drafter's reasoning. It reports
issues by severity and location; it does not rewrite the petition.

## Accuracy
- [ ] Every fact, date, amount, and party name matches the intake summary.
- [ ] No fact, citation, annexure number, or page range appears that was not
      supplied or verified. Fabrications are HIGH severity.
- [ ] Statutory text quoted verbatim (not paraphrased).
- [ ] Case citations correctly formatted; unverified ones marked
      "[CITATION TO BE VERIFIED]" rather than presented as settled.

## Completeness
- [ ] All twelve structural components present (cause title, synopsis, list of
      dates, memo of parties, relief clause + interim prayer, Respectfully
      Showeth, grounds, questions of law, alternative remedy, no-similar-petition,
      prayer, verification/affidavit closers).
- [ ] Relief clause (Section 5) and Prayer (Section 11) are consistent with each
      other and with the intake.
- [ ] Jurisdiction paragraph (para 1) present and cites Articles 226 & 227.
- [ ] Every annexure referenced in the body appears in the List of Dates and the
      annexure numbering is consistent throughout.
- [ ] No section left blank except clearly-marked placeholders.

## Compliance
- [ ] Uncertainty flagged, not hidden.
- [ ] Draft carries the [REQUIRES ATTORNEY REVIEW] header.
- [ ] Nothing presented as authoritative legal research; the petition argues, it
      does not certify the law.

## Formatting (house style)
- [ ] Substantive paragraphs open with "That ...".
- [ ] Grounds lettered A..Z, AA, BB ...; facts Arabic; relief/questions roman.
- [ ] Annexures cited as "(Annexure P-__) (Page No. __-__)".
- [ ] Cause-title header repeated on Synopsis, List of Dates, Memo of Parties.
- [ ] Counsel block, Place, Date present where required.

## Reviewer output format
```
## Quality Review
### Issues Found
1. [SEVERITY: HIGH/MEDIUM/LOW] <issue>
   Location: <component / paragraph>
   Recommendation: <fix>
### Checklist Summary
- Accuracy: PASS / [N flagged]
- Completeness: PASS / [N flagged]
- Compliance: PASS / [N flagged]
- Formatting: PASS / [N flagged]
### Overall Assessment
[READY FOR REVIEW / NEEDS REVISION] — <one-line summary>
```
