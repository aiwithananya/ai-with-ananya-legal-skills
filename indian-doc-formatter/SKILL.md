---
name: indian-doc-formatter
description: >
  [OUTCOME]: Produces a fully-formatted, ready-to-use .docx of any Indian legal
  document — contracts, pleadings, petitions, notices, agreements — with proper
  clause numbering, working cross-references, defined-term styling, schedules,
  signature blocks, TOC, page numbers, and Indian-jurisdiction conventions
  applied per user instructions.
  [TRIGGER]: Activates when the user says "format this document," "format this
  Word doc," "fix the formatting," "make this contract ready," "clean up
  formatting," "format this pleading," "format this agreement," "/format-doc,"
  or uploads a .docx / .pdf / raw text and asks for a formatted Word output.
  [ANTI-TRIGGER]: Does NOT activate for substantive drafting from scratch,
  contract review for legal risk (use review-contract), stamp duty assessment
  (use stamp-duty-calculator), or PDF/Excel formatting tasks.
---

# Indian Legal Document Formatter

Reformats any input (existing .docx, .pdf, or raw text) into a ready-to-use
Word document following Indian legal conventions and user-specified
instructions. Substantive content is preserved verbatim — only structure,
styling, numbering, and presentation are normalised.

## Step 0: Load Context

1. Read `references/firm-context.md`. If it is still the blank template, apply
   the default "Indian Corporate Contract Style" unless the document is a pleading.
2. Check the current directory for a matter `claude.md`. If present, read it
   for case context and use any formatting overrides it specifies.
3. Read `learnings.md` in this skill folder. Apply every entry under `## Rules`.

## Step 1: Receive Input and Detect Document Type

Locate the input. It usually arrives as an uploaded `.docx` or `.pdf`, or as
pasted text.

Auto-detect the document family by scanning the first 2 pages:
- **Contract / Agreement** → contains "WHEREAS", "AGREEMENT", numbered
  clauses, defined terms, schedules, signature blocks
- **Pleading / Petition** → contains "IN THE COURT OF", cause title, numbered
  averments, verification, "MOST RESPECTFULLY SHOWETH"
- **Notice / Legal Notice** → contains "Through:", "Subject:", "Without
  Prejudice", advocate's reference
- **Opinion / Memorandum** → contains "Re:", "Issues for Consideration",
  "Analysis", "Conclusion"

State the detected type and confirm with the user before proceeding if
ambiguous.

## Step 2: Collect Formatting Instructions

Ask the user. Skip any question already answered by `claude.md` or the
user's original request.

1. **Confirm document type** — Contract / Pleading / Notice / Opinion / Other
2. **Style profile** — Match my uploaded sample / Corporate Contract /
   Litigation Pleading / Legal Notice / Custom (free text). Always offer the
   sample option first: "Do you have a sample document in the format you want?
   Upload it and I'll match it." 
3. **Specific instructions** — free text: any deviations from defaults (e.g.,
   "use Arial 11," "double spacing," "no TOC," "renumber starting from 2.1")
4. **Output deliverables** — Formatted .docx only / .docx + clean PDF / .docx
   + redline against original

If the user already gave detailed formatting instructions in the prompt,
echo them back as a confirmed checklist instead of asking again.

## Step 3: Apply the Formatting Profile

**If the user uploaded a sample:** read it fully and extract font, size, line
spacing, margins, heading styles, numbering scheme, cause-title or parties
layout, annexure citation style, signature block and page numbering. List what
you extracted and ask the user to confirm before formatting. The sample wins on
every formatting point it covers; anything it does not cover falls back to the
matching profile below. Never copy the sample's text or facts into the output.

Otherwise, read the relevant profile reference before applying:
- Contract → `references/corporate-contract-style.md`
- Pleading → `references/litigation-pleading-style.md`
- Notice → `references/legal-notice-style.md`

Each profile defines: font, spacing, margins, heading styles, clause
numbering scheme, defined-term treatment, recital format, schedule
formatting, signature block, and page-number convention.

## Step 4: Build the Document

Use the `docx` skill (anthropic-skills:docx) for actual file generation. Read
its SKILL.md before writing the .docx so you use the correct python-docx
patterns for Word-native features.

Build in this order so cross-references and TOC resolve correctly:
1. Set page setup (margins, page size A4, orientation)
2. Define Word styles: Normal, Heading 1–4, Body, Recital, Definition,
   SignatureBlock, ScheduleTitle. Use built-in Heading styles so TOC works.
3. Insert cause title / parties block / cover page as applicable
4. Insert auto-TOC field (Word will populate on open) if user wants TOC
5. Insert recitals (WHEREAS clauses)
6. Insert numbered operative clauses using a single multi-level list — this
   is what makes cross-references work and auto-renumber
7. Bold-mark defined terms on first introduction; ensure all subsequent uses
   are consistent (case-sensitive find across the doc)
8. Insert schedules/annexures with page break + Schedule heading style
9. Insert signature block (two-column table is most robust)
10. Add footer with "Page X of Y" field
11. Replace any hardcoded clause cross-refs (e.g., "Clause 3.2") with Word
    REF fields pointing to bookmarks on each clause

## Step 5: Apply Legal Compliance Guardrails

These are mandatory in every output:

1. **Preserve original language** — Do not paraphrase, rewrite, "clean up,"
   or substantively edit clause text. Formatting only.
2. **Source-cite changes** — Maintain a brief change log of structural
   changes made (renumbering, heading promotions, term capitalisation).
3. **Flag uncertainty** — If a clause cannot be confidently classified (e.g.,
   ambiguous heading vs body), tag it `[REQUIRES VERIFICATION]` in the
   change log rather than guessing.
4. **No legal advice / no substantive edits** — If a defined term is used
   before it is defined, or a cross-reference points nowhere, log it; do
   not invent a definition or target.
5. **Attorney review required** — Output includes a `[REQUIRES ATTORNEY
   REVIEW BEFORE EXECUTION/FILING]` note at the top of the change log.

## Step 6: Quality Check (Ask First)

Unless `references/firm-context.md` sets a preference, ask:
"Run a formatting QC pass? (checks numbering integrity, broken
cross-references, defined-term consistency, TOC accuracy, signature block
completeness)"

If yes, follow `references/formatting-qc-checklist.md`. If a sub-agent QC is
warranted (court filing, executable contract), spawn a fresh agent with the
checklist and the output file.

## Step 7: Deliver

Save the final .docx and share it with the user. Provide a 3–5 line summary: document type, profile applied,
notable changes, anything flagged for review.

## Step 8: Capture Learnings

Ask the user: "Did the formatting meet your expectations? Anything to add to
the standing rules?"

If they identify a recurring preference (e.g., "always use 12pt for
shareholder agreements"), append to `learnings.md` under `## Rules`, or give
them the exact lines to paste into `references/firm-context.md` and re-upload
the skill, since the Claude app does not save files between chats. One-off
observations go under `## Observations`.

## References

- `references/corporate-contract-style.md` — full corporate contract profile
- `references/litigation-pleading-style.md` — pleading/petition profile
- `references/legal-notice-style.md` — legal notice profile
- `references/formatting-qc-checklist.md` — QC checklist for Step 6
- `references/word-mechanics-cheatsheet.md` — python-docx patterns for
  multi-level numbering, cross-refs, TOC, fields
- `references/firm-context.md` — your firm's default formatting standards
- `learnings.md` — accumulated rules and observations
