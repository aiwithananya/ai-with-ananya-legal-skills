---
name: legal-notice-drafter
description: >
  [OUTCOME]: Produces a send-ready pre-litigation legal notice under Indian law on
  advocate's letterhead — correct statutory basis, compliance period, mandatory
  recitals, relief claimed and signature block — delivered as .docx together with a
  service-and-limitation memo giving every operative date as a calendar date.
  [TRIGGER]: Activates on "draft a legal notice", "legal notice to", "demand notice",
  "cheque bounce notice", "notice to quit", "eviction notice", "cease and desist",
  "invoke arbitration", "Section 8 IBC notice", "Section 80 CPC notice",
  "Section 13(2) notice", or "/legal-notice".
  [ANTI-TRIGGER]: Does NOT activate for the complaint, plaint, petition or
  application that FOLLOWS a notice (use s138-complaint-drafter or
  writ-petition-drafter), for drafting a REPLY to a notice received, for contract
  drafting or review, or for non-Indian jurisdictions.
---

# Legal Notice Drafter — Indian Jurisdiction

Drafts pre-litigation legal notices issued by an advocate on behalf of a client.

## Assume nothing

This overrides every other instruction in this file.

Every fact in the notice must come from the user, or from a document the user has
supplied. Nothing else. If a fact is missing, **ask for it**. Do not:

- infer a date from surrounding context, or from what would be convenient
- estimate an amount, or guess a name, address, designation, capacity or constitution
- assume a transit time, a receipt date, or a date of service
- assume which of several possible statutes or provisions applies
- assume the client's instructions extend to proceedings not expressly mentioned
- fill a gap with a plausible-looking value because the draft reads better that way
- carry a fact forward from an earlier conversation or an earlier run
- treat a fact recited in a supplied document as verified — say where it came from

Where the user cannot supply something, leave a visible `[____]` in the draft and
list it under **Open items** in the delivery message. A blank the advocate can see
is safe. A plausible invention is not, and in a notice it can be fatal.

If a whole notice cannot be drafted without assumptions, draft what the facts
support and say plainly what is missing. Do not produce a complete-looking document
resting on invented particulars.

**Narrow exception — specimens.** If the user explicitly asks for a hypothetical,
specimen or test notice, invented facts are permitted, but the output must carry
`[SPECIMEN — HYPOTHETICAL FACTS]` above the draft header and the delivery message
must say so. Nothing short of an explicit request triggers this.

## Step 0: Load context

1. Read `learnings.md` in this skill's folder. Apply every rule under `## Rules`.
2. Read `references/firm-context.md` for practice, jurisdiction and formatting standards.
3. Check the working directory for a `claude.md`. If present, read it for matter
   context — parties, dates, amounts, prior correspondence — and pre-fill inputs
   from it. Skip any question it already answers.

## Step 1: Identify the notice type

Read `references/notice-types-index.md`. If the facts clearly point to one type,
name it and ask for confirmation. Otherwise offer the closest three or four.

**Do not proceed until the type is fixed.** Every downstream rule — limitation,
mandatory recitals, compliance window, who must be made a noticee — follows from it.

## Step 2: Load the statutory profile

The index names one of three profile files. Load only that file, and within it only
the section for the identified type:

- `references/statutory-commercial.md`
- `references/statutory-property-employment.md`
- `references/statutory-ip-govt-other.md`

From the profile extract: governing provision, whether notice is mandatory or
merely prudent, compliance period to be given, outer limit for issuing, mandatory
contents, and the consequence of a defect.

If the type is absent from all three files, say so plainly and draft under the
General Purpose structure, flagging that no statutory profile was applied.

## Step 3: House format and letterhead

Ask before collecting facts, because the answer changes the output and sometimes
what needs to be asked.

> "Do you want to upload your letterhead, or a previous notice in your house format,
> for me to match? Or should I use the default?"

Three options: upload a letterhead; upload a previous notice (better — it carries
the house voice as well as the look); or use the default.

**If a file is supplied**, read `references/house-format.md` and follow it. State
what was extracted and confirm before drafting. The uploaded format wins on form;
it does not win on statutory content.

**If not**, use the default and say so in the delivery message, so the user knows
the format was not matched to the firm.

Do not reconstruct a letterhead from memory. Ask each run.

## Step 4: Collect inputs

Ask only for what `claude.md` and the profile have not supplied. One round:

1. **Client** — full legal name, constitution, address, authorised signatory
2. **Noticee(s)** — full legal name, address for service; for a company, whether
   directors or officers are also arrayed in their own right
3. **Facts** — the transaction, the default, the dates. Ask for the underlying
   documents; never work from a summary where the document exists.
4. **Amount** — principal, interest with its contractual or statutory basis, other heads
5. **Relief** — payment, performance, cessation, vacation, restoration
6. **Compliance period** — statutory default, or the client's choice where discretionary
7. **Advocate** — name, enrolment number, office address, contact

## Step 5: Timing and limitation check (mandatory, before drafting)

Compute and present as a table:

- Date the cause of action arose
- Statutory deadline to issue this notice, if any, and days remaining
- Date the compliance period expires, assuming service on dispatch plus reasonable
  transit
- Date by which the follow-on proceeding must be filed
- Limitation for the underlying claim under the Limitation Act, 1963

Give every date as an absolute calendar date. Never write "within 30 days".

If any deadline has lapsed, or lapses within seven days, stop and flag it before
drafting anything.

Where a calculation depends on a fact not supplied — the actual date of receipt of
a bank memo, say — mark it `[REQUIRES VERIFICATION]` and show it computed both ways.

## Step 6: Draft

Read `references/drafting-conventions.md` and follow the advocate's-letterhead
structure set out there. Apply the house format captured at Step 3; where none was
supplied, apply the formatting standards from `references/firm-context.md`.

Three rules that are easy to get wrong:

- **No section headings.** The notice runs as continuous numbered paragraphs from the
  salutation to the signature block. No "DEMAND", no "FACTS", no "STATUTORY BASIS".
  The demand is simply the next numbered paragraph in sequence.
- **No annexures.** A notice is not a pleading. Identify each document in the recital
  itself by nature, date, number and parties. Never "annexed hereto and marked
  Annexure A", and no enclosures line after the signature block.
- **Quote, don't paraphrase.** Contracts, cheques, invoices and correspondence are
  reproduced verbatim.

## Step 7: Self-review

Read `references/quality-review.md` and run the checklist against the draft.
Present the findings above the draft, in the format that file specifies. Fix every
HIGH severity item before delivering.

## Step 8: Deliver

Write two files to `/mnt/user-data/outputs/`:

1. The notice as `.docx`, formatted per firm standards, headed
   `[DRAFT — REQUIRES ADVOCATE REVIEW BEFORE ISSUE]`
2. A service and limitation memo (`.md`) carrying the Step 5 date table and the
   service instructions from `references/service-and-proof.md`

## Step 9: Log

Ask: "Did this meet expectations? Anything to change for next time?" Append useful
feedback to `learnings.md` — under `## Rules` if it should always apply, under
`## Observations` otherwise.

---

## Guardrails — every run, without exception

1. **Cite the provision, do not recall it.** Every statutory reference in the notice
   comes from a profile file. If a provision is needed that is not in one, say it
   requires verification rather than citing from memory.
2. **Flag uncertainty inline.** Limitation computations turning on unsupplied facts,
   state-specific rent control rules, and anything the profile marks as unsettled
   get `[REQUIRES VERIFICATION]` in the draft itself.
3. **This is not legal research.** Do not cite a judgment in the notice unless the
   user supplies it. Authorities in the profile files are practice notes for the
   advocate, not citations for the draft.
4. **Preserve source language.** Verbatim quotation of every source document.
5. **Advocate review before issue.** Every output carries the draft header. A notice
   fixes the client's position, can start limitation running, and in IP matters can
   itself found a cause of action against the sender.
6. **Assume nothing.** See the rule at the head of this file; it overrides all of
   these. Every delivery message ends with an **Open items** list, or the words
   "No open items" — never silence on the point.

## Statutory currency warning

BNS, BNSS and BSA, 2023 replaced the IPC, CrPC and Evidence Act from 1 July 2024. A
notice threatening criminal proceedings cites BNS and BNSS, never IPC and CrPC.
Matters pending before that date stay under the old Code — BNSS s.531.
