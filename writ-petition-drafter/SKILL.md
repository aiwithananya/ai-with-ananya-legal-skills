---
name: writ-petition-drafter
description: >
  [OUTCOME]: Produces a court-ready Civil Writ Petition under Articles 226 & 227
  of the Constitution of India (mandamus and certiorari focus) as a formatted
  Word (.docx), built through guided intake on facts, law, and research points
  and matched to the firm's house style, with a mandatory sub-agent quality
  review before delivery.
  [TRIGGER]: Activates when the user says "draft a writ petition", "Article 226
  petition", "CWP", "writ of mandamus", "writ of certiorari", "quash this
  order/notification by writ", "High Court writ", or uploads facts/an impugned
  order and asks for a writ petition.
  [ANTI-TRIGGER]: Does NOT activate for Supreme Court petitions under Article 32,
  SLPs, statutory appeals or replies, civil suits, criminal petitions, writ
  petitions outside India, reviewing an opponent's petition, or drafting a
  demand/legal notice.
---

# Writ Petition Drafter (Article 226/227)

Drafts a complete Civil Writ Petition for an Indian High Court, mandamus and
certiorari focus, matched to the firm's sample CWP. Guided intake on facts, law,
and research points; optional upload of a sample or matter documents. Output is a
Word (.docx). A sub-agent quality review runs before delivery (firm preference:
Always).

## Before starting
1. Read `references/firm-context.md` for practice area, jurisdiction, house
   style, and quality-check preference.
2. Check the current directory for a matter `claude.md`. If present, read it for
   case context (parties, court, impugned action, dates) and use it to pre-fill
   intake — skip questions it already answers.
3. Read `learnings.md`; apply any Rules listed there during this run.
4. Ask once: "Do you have a sample writ petition from your court or chamber?
   Upload it and I'll match its format." If the user uploads a sample petition or
   matter documents, read them first and extract everything usable before asking
   anything. The sample wins on form (cause title, numbering, grounds lettering,
   annexure style, signature block); it never overrides the law.

## Step 1 — Guided intake (facts, law, research)
Read `references/intake-guide.md` and run its three passes: FACTS, then LAW, then
RESEARCH POINTS. Confirm extracted values rather than re-asking. Batch related
questions; aim for 5-8 total. Produce a short intake summary and get the user's
confirmation before drafting.

Key decision to settle in intake: the relief mix — certiorari (quash an
order/notification), mandamus (direct an authority to act), declaration/ultra
vires, read-down, or a combination — since it drives the relief clause, grounds,
questions of law, and prayer.

## Step 2 — Assemble the petition
Read `references/writ-structure-guide.md` and build all twelve components in
order: cause title, synopsis, list of dates & events, memo of parties, petition
heading + relief clause (+ interim prayer), Respectfully Showeth (jurisdiction
para first, then facts with verbatim statutory blocks), lettered grounds,
questions of law, alternative-remedy/maintainability, no-similar-petition,
prayer, and verification/affidavit closers.

Read `references/drafting-conventions.md` and follow house style exactly:
"That ..." paragraph openers; grounds lettered A..Z, AA, BB ...; facts Arabic;
relief and questions roman; annexures cited "(Annexure P-__) (Page No. __-__)"
with consistent numbering; counsel/closing block.

## Step 3 — Generate the .docx
Read the `docx` skill's SKILL.md, then generate the Word file with proper
headings, indented statutory/quote blocks, and page breaks between the
preliminary components (synopsis, list of dates, memo of parties). Filename:
`<Petitioner short name> - CWP <year>.docx`. Save to the outputs folder.

## Step 4 — Mandatory quality review
Firm preference is Always. Spawn a FRESH sub-agent (Task tool) with clean
context. Give it only the draft, the intake summary, and
`references/quality-review.md`. Present its findings to the user alongside the
draft. If it returns NEEDS REVISION, fix the flagged items before delivery.

## Step 5 — Deliver
Present the .docx with a `[REQUIRES ATTORNEY REVIEW]` header and the quality
review summary. Then ask: "Did this meet your expectations? Anything to improve
for next time?" Log useful feedback to `learnings.md` (prune if it passes ~50
lines).

## Legal compliance guardrails (mandatory)
1. **Source citations** — cite specific provisions, orders, and annexures. Never
   summarize statutory text or an impugned order from memory.
2. **Uncertainty flagging** — anything not supplied or verifiable is a clearly
   marked placeholder: `[FACT TO BE CONFIRMED]`, `[CITATION TO BE VERIFIED]`,
   `[STATUTORY TEXT TO BE VERIFIED]`, `(Page No. ___)`. Never invent facts,
   dates, page ranges, or citations.
3. **Not legal research** — this skill drafts a pleading; it does not certify the
   state of the law. Case authorities come from the user or are flagged for
   verification.
4. **Preserve original language** — reproduce statutory provisions, notifications,
   and quoted passages from the impugned order verbatim.
5. **Attorney review required** — every output carries `[REQUIRES ATTORNEY
   REVIEW]` and must be settled by counsel before filing.
