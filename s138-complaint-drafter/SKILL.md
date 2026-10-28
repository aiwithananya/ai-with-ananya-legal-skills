---
name: s138-complaint-drafter
description: >-
  [OUTCOME]: Produces a ready-to-file complaint under Section 138 (read with
  Section 141) of the Negotiable Instruments Act, 1881 for a dishonoured
  cheque — as a Word .docx filing set (complaint + affidavit + list of
  witnesses + list of documents), formatted to the specific court
  the user names, with the statutory S.138 timeline verified.
  [TRIGGER]: Activates when the user says "draft a 138 complaint", "cheque
  bounce complaint", "S.138 NI Act complaint", "cheque dishonour complaint",
  "file a case for a bounced cheque", or uploads cheque-return memos / a
  legal demand notice and asks for a complaint.
  [ANTI-TRIGGER]: Does NOT activate for drafting the S.138 legal demand
  notice itself (that precedes the complaint), civil recovery suits, S.25
  PSS Act matters, reviewing an opponent's complaint, or non-Indian
  jurisdictions.
---

# Section 138 NI Act Complaint Drafter

Drafts a cheque-bounce criminal complaint under S.138 r/w S.141 of the
Negotiable Instruments Act, 1881, adapted to any Indian Magistrate court's
format. The skill is court-format-agnostic by design: it always asks which
court, then how that court wants the cause-title/format, then whether a
sample is available, before drafting.

Read `references/firm-context.md` for house standards (if it is still the blank
template, use the defaults in `references/format-adaptation.md`). If a
matter-specific `claude.md` exists in the working directory, honour it.

## Workflow

### Step 1 — Ask the court, then the format, then for a sample
Ask these three, in order, before anything else (use one prompt with the
first two; the sample ask can follow):
1. **Which court** will this be filed in? (e.g., "Court of the Additional
   Chief Judicial Magistrate, Kashipur, U.S. Nagar" / "MM, Saket, Delhi" /
   "JMFC, Bengaluru"). Capture the exact cause-title wording.
2. **What format** does that court/bar expect? Options to offer: *Match my
   uploaded sample*, *Standard Magistrate format*, *I'll paste the court's
   format/rules*, *You choose a clean default*.
3. **Do you have a sample** complaint for this court or in this style? If yes,
   ask them to attach it — the skill mirrors its structure, headings, spacing
   and cause-title. If no, use the bundled template in `assets/`.

Do not guess the court or format. If the user is unsure of the exact
cause-title, offer the closest standard form and flag it for their review.

### Step 2 — Run intake
Collect the case facts using `references/intake-checklist.md`. Ask for missing
items in grouped batches, not one at a time. Never invent a fact: leave a
clearly marked `[TO BE CONFIRMED: …]` placeholder for anything not supplied.

### Step 3 — Verify the statutory timeline (always)
Using the dates from intake, apply the S.138 proviso timeline in
`references/statutory-framework.md`. Compute and state:
- cheque presented within validity (≤3 months / bank validity);
- demand notice issued within **30 days** of receipt of dishonour memo;
- **15-day** payment window from notice receipt (cause of action arises on
  its expiry);
- complaint filed within **one month** of cause of action (S.142(1)(b));
  note the court's condonation power for delay.
If any leg is missing, premature, or time-barred, **flag it prominently at
the top of the output** and still draft (with the issue noted) unless the
user says otherwise. Do not silently "fix" dates.

### Step 4 — Draft the filing set
Default output (per firm-context) is the full set as a single .docx:
1. **Complaint** under S.138 r/w S.141 NI Act, 1881 **read with S.223 of
   the BNSS, 2023** — the heading must cite all three (see the
   Citation Lock in `references/statutory-framework.md`); cause-title,
   parties, MOST RESPECTFULLY SHOWETH body, jurisdiction (S.142(2)),
   prayer, verification.
2. **Affidavit** of the complainant — title it simply **"Affidavit"**
   (or "Affidavit of the Complainant"). Do **not** cite "S.223 BSA" or any
   BSA section in the affidavit heading — that citation is wrong (see the
   Citation Lock).
3. **List of Witnesses.**
4. **List of Documents.**
Follow `references/format-adaptation.md` to bend the layout to the named
court / sample. Mirror the sample's structure when one is provided; otherwise
follow `assets/filing-set-template.md`. Company/firm accused ⇒ plead S.141
vicarious liability for each director/signatory.

### Step 5 — Quality review (always)
Run `references/qa-checklist.md` before delivering. Fix or flag every item.
Present the .docx and a short cover note listing any `[TO BE CONFIRMED]`
placeholders and any timeline flags.

## Building the .docx
Use the **docx skill** to generate the Word file. Preserve the sample's
formatting where given. Save to the outputs folder and share it.

## Legal compliance guardrails (mandatory)
- Cite specific sections of the NI Act / BSA / BNSS by number; do not
  paraphrase statutory language from memory — quote the operative words.
- Flag every uncertainty with a visible `[TO BE CONFIRMED: …]` marker rather
  than guessing names, dates, amounts, cheque numbers or addresses.
- Never present this draft as authoritative legal work product; it is a
  first draft for advocate review.
- Preserve the complainant's original wording of facts when supplied; do not
  embellish the narrative.
- End every deliverable with: *"Draft for advocate review — verify all facts,
  dates, annexures and statutory citations before filing."*

## Check learnings
Read `learnings.md` at start; apply its rules. After delivering, ask if the
draft met expectations and log useful feedback there.
