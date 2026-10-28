# Quality Review — Legal Notice

Run this before delivering. Read the draft as though it had arrived from the other
side and you were looking for the defect that defeats it.

In Claude Code this step can be delegated to a sub-agent with a clean context. On
claude.ai there is no sub-agent, so run it inline — but run it as a separate pass
over the finished draft, not as a check while writing.

---

## A. Statutory compliance

- [ ] The correct provision is cited, and it is the provision that actually applies
      on these facts
- [ ] Where the criminal law is invoked, BNS and BNSS provisions are cited, not IPC
      and CrPC
- [ ] The compliance period matches the statutory period in the profile file
- [ ] Every mandatory content item for this notice type is present
- [ ] The notice is being issued within any outer statutory limit, and the
      calculation is shown

## B. Dates

- [ ] Every date is an absolute calendar date, not "within 30 days"
- [ ] The date the cause of action arose is stated and is supported by a document
- [ ] The follow-on filing deadline is computed and appears in the service memo
- [ ] Limitation on the underlying claim has been checked against the Limitation Act
      table, and the claim is not time-barred
- [ ] Where a date depends on an unsupplied fact, it is marked
      `[REQUIRES VERIFICATION]` and computed both ways

## C. Parties

- [ ] Client's full legal name and constitution are correct, and match the contract
- [ ] Every noticee is named in full, with the capacity in which they are arrayed
- [ ] For a company noticee, the registered office address is used
- [ ] Where officers are made personally liable, the statutory basis for doing so is
      pleaded, not assumed

## D. Substance

- [ ] Every operative document is quoted verbatim, not paraphrased
- [ ] Every document is identified in the body by nature, date, number and parties
- [ ] No annexures, enclosures or schedules anywhere in the notice
- [ ] No fact appears that the client did not supply
- [ ] Facts believed but unconfirmed are flagged as such in the text
- [ ] The amount claimed is broken down by head and the arithmetic is correct
- [ ] Interest is claimed on a stated contractual or statutory basis, not asserted
- [ ] The demand paragraph is unambiguous and states what is required, by when

## E. Exposure

- [ ] The notice threatens only proceedings the client has instructed and is willing
      to bring
- [ ] For an IP notice: the groundless threats exposure under s.142 TM Act, s.60
      Copyright Act or s.106 Patents Act has been raised with the user, and the
      client's willingness to sue confirmed
- [ ] For a defamation notice: the amplification risk has been raised
- [ ] For a s.8 IBC notice: the user has been asked about any pre-existing dispute
- [ ] Nothing in the notice concedes a fact, waives a right, or admits a defence
- [ ] The reservation of rights clause is present

## F. Form

- [ ] Draft header present
- [ ] Modes of dispatch in the header block match the service memo
- [ ] Subject line names the provision and the demand
- [ ] Paragraphs numbered continuously, each opening with "That"
- [ ] Amounts in figures and words, Indian digit grouping
- [ ] One date format throughout
- [ ] Signature block carries the advocate's name, enrolment number and address
- [ ] No section headings anywhere in the body — the notice runs as continuous
      numbered paragraphs, and the demand is one of them
- [ ] Nothing follows the signature block

## G. Assumptions

- [ ] Every fact in the notice traces to something the user supplied
- [ ] No date, amount, name, address, designation or capacity was inferred
- [ ] Every gap the user could not fill is a visible `[____]`, not a plausible value
- [ ] Open items are listed for the user, not silently resolved
- [ ] Where the house format was supplied, it was followed; where it was not, the
      default was used and the user was told so

---

## Output format

```
## Quality Review

### Issues
1. [HIGH] <what is wrong>
   Location: <paragraph or section>
   Fix: <what to do>

2. [MEDIUM] ...

### Summary
- Statutory compliance: PASS / n issues
- Dates: PASS / n issues
- Parties: PASS / n issues
- Substance: PASS / n issues
- Exposure: PASS / n issues
- Form: PASS / n issues
- Assumptions: PASS / n issues

### Assessment
READY FOR ADVOCATE REVIEW / NEEDS REVISION
<one or two lines>
```

Fix every HIGH before delivering. Deliver MEDIUM and LOW items to the user alongside
the draft rather than silently resolving them — the advocate decides.
