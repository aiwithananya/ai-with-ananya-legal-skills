# Notice Types Index

Router. Identify the type, then load only the profile file named in the last column.

| # | Notice type | Governing provision | Period to give | Mandatory? | Profile file |
|---|---|---|---|---|---|
| 1 | Cheque dishonour demand | NI Act 1881, s.138 proviso (b) | 15 days | Yes — condition precedent | commercial |
| 2 | Breach of contract / recovery | Contract Act 1872; contractual notice clause | Per contract, else 15 days | No | commercial |
| 3 | Operational creditor demand | IBC 2016, s.8; Rule 5, AA Rules 2016 | 10 days | Yes | commercial |
| 4 | Invocation of arbitration | A&C Act 1996, s.21 | Per clause, else 30 days | Yes — commences arbitration | commercial |
| 5 | MSME delayed payment | MSMED Act 2006, ss.15–18 | 15 days | No — but precedes s.18 reference | commercial |
| 6 | Secured creditor demand | SARFAESI Act 2002, s.13(2) | 60 days | Yes | commercial |
| 7 | Termination of lease / notice to quit | TP Act 1882, s.106 | 15 days or 6 months | Yes | property-employment |
| 8 | Eviction under State rent control | State Rent Act — varies | State-specific | Usually yes | property-employment |
| 9 | Employment — termination / show cause | Contract; State S&E Act; ID Act 1947 s.25F | Per contract / 1 month | Depends on status | property-employment |
| 10 | Employee-side claim (dues, wrongful termination) | Contract; Payment of Wages / Gratuity Acts | 15 days | No | property-employment |
| 11 | IP cease and desist | TM Act 1999; Copyright Act 1957; Patents Act 1970 | 7–15 days | No — **groundless threats risk** | ip-govt-other |
| 12 | Notice before suit against Government | CPC 1908, s.80 | 2 months | Yes | ip-govt-other |
| 13 | Consumer grievance | CP Act 2019 | 15 days | No | ip-govt-other |
| 14 | Defamation | Civil tort; BNS 2023 s.356 | 15 days | No | ip-govt-other |
| 15 | General purpose | — | 15 days default | No | ip-govt-other |

## Disambiguation

**"Cheque bounce"** — this skill drafts the *demand notice* (type 1). The complaint
that follows belongs to `s138-complaint-drafter`. If the user has already sent the
notice and the 15 days have run, hand off; do not draft a second notice.

**"Recovery"** — if there is an arbitration clause, type 4 is almost always the
right instrument, not type 2. Check for a clause before defaulting to a demand.

**"Recovery from a company that has stopped paying"** — types 2, 3 and 4 all fit.
Type 3 carries a ₹1 crore threshold and a pre-existing dispute risk; do not reach
for it as a debt-collection tactic without warning the user. See the profile.

**"Notice to vacate"** — type 7 applies only where no State rent control legislation
covers the premises. Establish which statute governs before drafting.

## Cross-cutting: pre-institution mediation

Where the follow-on proceeding would be a commercial suit of specified value
(₹3 lakh and above) under the Commercial Courts Act, 2015, s.12A requires
pre-institution mediation unless the suit contemplates urgent interim relief. The
Supreme Court held the requirement mandatory in *Patil Automation (P) Ltd. v.
Rakheja Engineers (P) Ltd.*, (2022) 10 SCC 1, with non-compliance attracting
rejection of the plaint under Order VII Rule 11 CPC.
`[VERIFY CURRENT POSITION — the scope of s.12A, particularly for counterclaims and
for what qualifies as urgent interim relief, is actively litigated.]`

This affects types 2, 4 and 5. Say so in the service memo so the client is not
surprised by a further step after the notice period expires.
