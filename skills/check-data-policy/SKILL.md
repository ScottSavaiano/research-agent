---
name: check-data-policy
description: Confirms that nothing bars the agents from working with a data source, and records the evidence. Fires at Stage 5 (5.3) for every candidate dataset — a public-use file the student intends to analyze, or a source they intend to build their own dataset from — and again at Stage 18/22 at acquisition. The default answer is CLEAR and it is the right answer for almost every source. Only two things change it: an explicit AI/LLM clause in the source's governing terms (there are four such sources a student can obtain, named in the skill), or data the student collected themselves under IRB. Reads every governing document in full — never keyword-searches — and ranks them by authority: contract and licence first, help pages and papers never. Produces evidence notes the student writes up in their weekly journal. Status — DRAFT (rewritten 2026-07-14 to remove gating).
---

# Check Data Policy

**Last edited:** 2026-07-19 (teacher-admin — **added the mandatory "Record it — WRITE THE FILES" step.** The
first runtime test, 2026-07-14-authored/2026-07-19-run, passed read-don't-grep and CLEAR-default but the agent
printed the evidence note to chat and never wrote `data/data-validity-log.md` — because the skill only *named*
the file in a passive "Where it is recorded" list. Now there is an imperative two-write step (append the log,
set `data_interaction_mode`) that runs before the closing line, framed as a failure to skip it. Prior: 2026-07-14
(Cowork — **rewritten**. The first draft was defensive and gate-happy: it hunted for
barriers instead of confirming there weren't any, and it would have buried students at Stage 5. This version has
the opposite posture.)
Source of truth: `design/data-source-llm-policy-registry.md`, `design/data-interaction-contract.md`.

---

## What you are actually doing

> ## **You are looking for evidence that NOTHING bars the agents from this data, and that the data is public-use.**
>
> **That is the whole job.** You are documenting an absence. **The absence is the normal case, and it is a
> complete answer.**

**The default is CLEAR, and CLEAR is right for almost every source a student will ever pick.** NHANES, YRBS,
ACS PUMS, NSDUH, ANES, PISA, V-Dem, GDELT, Congress.gov, OSF, the Census, the CDC, the whole aggregate tier —
all CLEAR. No clause, no restriction, no gate.

**This should take about twenty minutes.** If it is taking longer, something has gone wrong — almost certainly
you are manufacturing doubt where there is none. Do not.

## The two things — and only these two — that change the answer

Everything else is **CLEAR**.

**1. The source has an explicit AI/LLM clause in its governing terms → ROW-RULE.**
There are **four of these a student can actually obtain**, and here they are:

> **Add Health · HRS · ICPSR** *(and anything taken through the ICPSR door — MTF, openICPSR, AEA)* **·
> UK Data Service**
>
> *(A fifth — **GSS Sensitive Data Suite** — has an AI clause too, but a student cannot obtain it: it needs IRB,
> a $1,500 fee, an institutional licence and a faculty PhD co-investigator. Public GSS is CLEAR. If a student
> somehow has GSS Sensitive, it's ROW-RULE — but you will never see this.)*

If the source is not on that list, and a full READ of its governing terms turns up no AI/LLM clause, **it is
CLEAR.** Write it down and move on.

**2. The student collected the data themselves from human subjects under IRB → NO-AGENT.**
Their own survey, their own interviews. Local inference only. **This is rare.**

**There is no third case. There is nothing to fail. Nothing gets blocked.**

---

## Rank the documents before you read them

**This is the part that matters most, and it is where the check goes wrong.** Not every document about a dataset
*governs* it. Sort them first, then read in this order:

### TIER 1 — GOVERNING. These are the law.
1. **The data use agreement or contract** you signed or clicked through
2. **The terms of use / terms of service** (browsewrap counts — "by using the service you agree")
3. **The licence attached to the dataset** (CC0, CC-BY, a custom licence)
4. **An explicit published AI/LLM policy** from the archive itself

**If it isn't one of these four, it does not govern.** Full stop.

### TIER 2 — PERSUASIVE. Read them; honour them; they are not law.
- **A depositor's README or wiki note.** *Honour it* — it is what the person who shared their data **asked** for,
  and honouring a request costs nothing. But it is a request, not a contract.
- **Help-centre pages and FAQs.** Explanatory copy. **When they conflict with Tier 1, Tier 1 wins.**

### TIER 3 — NOT AUTHORITY AT ALL.
- Blog posts · news coverage · a **paper's ethics statement** · what someone told you · what an AI told you

> ### Three cautionary tales — all real, all mine, all from building this curriculum
>
> **OSF's help doc says** *"No License — Nothing can be done with the content without the copyright holder's
> consent."* **The OSF Terms of Use — the actual contract — says** the depositor grants every user *"a perpetual,
> irrevocable, worldwide, royalty-free license to use… **You may grant further rights if you apply a license.**"*
> **"Further."** The ToU is the floor. The help doc is wrong, and reading it as governing would have made most of
> OSF untouchable — on a platform whose entire purpose is reuse. **Tier 2 lost to Tier 1.**
>
> **OpenSecrets' terms say** *"…including inclusion in automated decision-making technology, machine learning,
> training, profiling tools, and/or artificial intelligence… is strictly prohibited."* Frightening — **until you
> read the start of the same sentence**: *"Any use … **other than as specifically authorized in these Terms**."*
> And then, further down the page, **a licence a keyword search can never find**: *"content on this site is
> **licensed under a Creative Commons Attribution-Noncommercial-Share Alike 3.0 United States License**."*
> **CC BY-NC-SA grants the right to share AND adapt for non-commercial purposes.** Student research is
> non-commercial and transformative — **specifically authorized**, so the prohibition never engages. **A grep for
> "artificial intelligence" finds the scary clause and never finds the grant, because "Creative Commons" contains
> none of the keywords.**
>
> **The Twitter-STMHD paper claims** the data "can be requested through a Data Usage Agreement." **The actual
> Zenodo record has no gate at all** — it is open CC BY 4.0. A paper's ethics statement is **Tier 3**. It
> described what the authors *intended*, not what they *shipped*. **Read the record, not the paper about the
> record.**

---

## How to run it — three questions

**1. Is the source on the four-source ROW-RULE list above?**
→ Yes: **ROW-RULE.** Quote their clause, note that codebooks and aggregates are expressly permitted, done.
→ No: continue.

**2. Did the student collect this data themselves, from human subjects, under IRB?**
→ Yes: **NO-AGENT.**
→ No: continue.

**3. READ the Tier-1 documents. All of them. End to end.**

> # ⚠️ **READ EVERY GOVERNING DOCUMENT IN FULL. NO KEYWORD SEARCH — NOT EVEN AS A BACKSTOP.**
>
> **This is a hard rule, and it has no exception.** You do not `grep`, `Ctrl-F`, `find`, or search-within-page
> these documents. You **read them, top to bottom** — the terms of use, the data use agreement, the licence, and
> any published AI policy, **each one, in full.** A DUA is a few pages; a terms of service is a few thousand
> words. That is a five-minute read, and reading is the *only* method that works here.
>
> **Why the rule is absolute, and why a "backstop" search is banned too:** every failure below happened because a
> keyword landed on one sentence and the sentence that *governed* was somewhere else — a paragraph later, or the
> back half of the same sentence, or in a different document, or a **grant** phrased in words the search terms
> never contained. A search cannot find the sentence you didn't know to look for. Only reading can. And a search
> run "afterwards, just to check" quietly becomes the method the first time someone is tired — so there is no
> afterwards. **Read. That's it.**
>
> **Five real failures, every one from searching instead of reading, every one made while building this
> curriculum:**
>
> | What a search did | What reading found |
> |---|---|
> | **GSS → "no AI policy"** | The grep hit the wrong document and stopped. NORC's Sensitive Data Protection Plan has an **absolute generative-AI ban**. |
> | **Add Health → "banned"** | Found the headline *"may not be used to manage, process, or analyze"* and stopped **three paragraphs short** of the carve-out that expressly permits codebooks and population estimates. |
> | **UKDS → "agents totally barred"** | Read clause 5's **first sentence** and missed the **second**, which ties it to *"data transfer to unauthorised parties."* Half a clause, a wrong rule. |
> | **OpenSecrets → "ROW-RULE"** | Grepped *"artificial intelligence,"* found the prohibition, and **never found the CC BY-NC-SA licence** — because *"Creative Commons"* contains none of the search terms. **The grant is invisible to a keyword search.** |
> | **OSF → "unusable without a licence"** | Read a **help-doc** sentence and never read the **contract**, which grants every user a perpetual irrevocable licence. |
>
> **The through-line: a search finds prohibitions and misses permissions.** Prohibitions use the scary words you
> search for; grants and carve-outs use words you'd never think to. Reading is the only way to see both.

Read the terms of use, the DUA, the licence, and any published AI policy — **each one, in full, start to finish.**
There is no shortcut and no search step. Reading *is* the method.

→ **Nothing there?** **CLEAR.** This is the expected outcome. Record what you read, what you found, the date, and
that the data is public-use. **Done — go do your research.**

→ **Something there?** Read the **whole clause and the whole document around it.** The broad prohibition at the
top is usually not the operative text. Quote **both** the prohibition and whatever qualifies it, then set the
mode.

---

## Record it — WRITE THE FILES. This is a step, not a note. Do not skip it.

> ⚠️ **Before you tell the student anything, you WRITE the determination to disk.** The chat message is not the
> record — the file is. A determination that lives only in the conversation is lost at the next `/new`, and the
> other two agents read the mode from the file, not from your chat. **Producing the evidence note in chat without
> writing the file is a FAILURE of this skill, even when the mode is right.**

Two writes, every time, in this order:

**1. Write the evidence note to `data/data-validity-log.md`.** Use your `write_file`/`patch` tools directly (not a
code-exec import). Read the current file first: if it has no block for *this* source yet, append the dated block
below; if a block for this same source already exists (a re-check), replace it. **Write the block exactly once** —
do not append a second copy of what you just wrote. Never clobber a *different* source's earlier block. This is the
durable record; the block is the same one shown under "What you hand the student."

**2. Set the mode in `project_paper_status.md`.** Change the `data_interaction_mode:` line from `null` (or its prior
value) to the mode you determined — `clear`, `row-rule`, or `no-agent` (lowercase, matching the state-file's own
comment). Read the file, replace that one line, write it back; do not touch anything else in it.

**Only after BOTH files are written** do you show the student the evidence note and say your closing line. If you
cannot write a file (missing `data/` folder, permissions), say so plainly and stop — do not pretend the record
exists.

*(What you never write: the student's weekly journal entry. That is their work — see Boundaries. You write the
log and the state flag; the student writes the journal.)*

---

## What you hand the student

**Evidence, not prose.** The student writes the journal entry themselves — that is their work, and the STS AI Use
Table is explicit that an AI may not draft it.

### The normal case — CLEAR. This is what almost every check looks like.

```
DATA POLICY CHECK — notes for your journal
Source:        NSDUH 2023 public-use file
Door:          datafiles.samhsa.gov  (SAMHDA — not the ICPSR copy)
Checked:       2027-01-14

GOVERNING DOCUMENTS — READ IN FULL (Tier 1):
  · SAMHDA Terms of Use — datafiles.samhsa.gov/info/terms-use-nid3422
    (read end to end; ~900 words; 6 numbered clauses)
  · the study's data-use page (read end to end)
  Both read top to bottom, in full. No keyword search.

FINDING:  NO AI/LLM CLAUSE. No redistribution clause of any kind.
          The terms restrict only re-identification, and require citation.
          Data is PUBLIC-USE — SAMHSA did the disclosure review before release.
          NO primary collection from human subjects in this project.

MODE:  CLEAR

WHY THIS IS FINE:
  There is no restriction to comply with. The search was thorough and is
  documented above.

FOR YOUR JOURNAL (in your own words, this week):
  - which source, which door
  - which documents you read, and in what order of authority
  - what you found — nothing — and why that settles it
```

**Then — once the files are written (see "Record it" above) — say, plainly:** *"That's it. You're clear. I've
logged it to your data-validity log. Put it in your journal this week too — it becomes a sentence in your Methods
later."*

### The ROW-RULE case — same shape, plus the clause and why we comply.

Quote the restriction **and** the carve-out. State the match: *the policy governs data shared with a model; under
ROW-RULE nothing is shared with the model — it gets the codebook (expressly permitted), writes the code, sees the
aggregates.*

---

## Where it is recorded

**You write the first two (see "Record it — WRITE THE FILES" above). The student writes the third.**

- **`data/data-validity-log.md`** — the durable record. **You append the evidence block here — this is mandatory,
  not optional.**
- **`data_interaction_mode`** in `project_paper_status.md` — the switch all three agents read at session start.
  **You set it** (`clear` / `row-rule` / `no-agent`).
- **The student's weekly journal** — in their own words, that week. **You never write this.** `update-journal`
  prompts if it is missing.

## Boundaries

- **The default is CLEAR. Find the evidence that confirms it.** You are not hunting for problems.
- **Do not manufacture doubt.** A thorough documented search that finds nothing **is a complete answer.** Hedging
  a settled finding is not rigour — it is a way of never finishing.
- **Nothing is blocked.** There is no fail state. Every source in this program can be analysed with AI-written
  Python; the only question is whether the model may see the rows.
- **Rank the documents. Contract first, help pages never.**
- **READ every governing document in full. Do NOT keyword-search — not even as a backstop.** This is absolute.
  A search finds prohibitions (they use the scary words) and misses grants and carve-outs (they don't). Reading
  is the only method. There is no "afterwards" search step, because it becomes the method the moment someone is
  tired.
- **Never write the student's journal entry.** Evidence only.
- **No agent touches the dataset until the mode is set** — but setting it is usually a twenty-minute lookup that
  returns CLEAR.
