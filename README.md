# Indian Legal Skills

Free Claude skills for Indian lawyers, by **AI with Ananya** ([@__ananya__10](https://www.instagram.com/__ananya__10/)).

Each folder is one skill. Type its name in Claude (for example `/s138-complaint-drafter`) and it takes over the task.

| Skill | What it does |
|---|---|
| [s138-complaint-drafter](s138-complaint-drafter/) | Drafts a ready-to-file Section 138 NI Act complaint with affidavit, list of witnesses and list of documents, formatted for the court you name, with the S.138 timeline checked. |
| [indian-doc-formatter](indian-doc-formatter/) | Turns any messy Indian legal draft into a properly formatted Word document: clause numbering, cross-references, schedules, signature blocks, page numbers. |
| [legal-notice-drafter](legal-notice-drafter/) | Drafts a send-ready pre-litigation legal notice under Indian law, with a service and limitation memo giving every date as a calendar date. |
| [writ-petition-drafter](writ-petition-drafter/) | Drafts a court-ready Article 226 and 227 writ petition in Word through a guided intake on facts, law and research points. |
| [judgment-analyser](judgment-analyser/) | Reads any Indian judgment and produces a case note with ratio separated from obiter and every point pin-cited to a paragraph. |

## How to install

**In the Claude app (web, desktop or mobile)**

1. Download this repo (green **Code** button, then **Download ZIP**) and unzip it.
2. Zip the folder of the skill you want, for example the `legal-notice-drafter` folder.
3. Upload that zip in Claude's Skills settings. Code execution needs to be on for skills that produce Word files.

**In Claude Code**

Copy the skill folder into `~/.claude/skills/`.

## Use your own samples

Every skill asks for a sample before it drafts or formats. Upload a previous complaint, petition, notice, case note or letterhead from your own court or chamber, and the skill matches its format: cause title, numbering, headings, annexure style and signature block. Your sample decides the format. The law still comes from the statute, so if your sample cites a repealed section or misses a required paragraph, the skill tells you what it changed.

No sample? Each skill has a sensible Indian default.

## Make it yours permanently

Each skill has a `references/firm-context.md` file. Fill in your practice area, court and formatting standards once, re-zip the skill and upload it again. After that, every draft follows your house style without you uploading a sample each time.

## Please read

These skills produce drafts for an advocate to review. They are not legal advice. AI can get facts, citations and dates wrong, so verify every fact, section, citation and date before you file or send anything.

## Licence

MIT. Free to use, change and share.
