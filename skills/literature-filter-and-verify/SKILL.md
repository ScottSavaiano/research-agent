---
name: literature-filter-and-verify
description: Conducts the research agent's stage-7 filtering, verification, and access-triage — taking `literature-discovery`'s candidate set and producing the decision-ready topic and methods reading lists. For each candidate it does three things: (1) RANKS it by relevance to the reading brief (topic relevance for the topic list; method relevance for the methods list); (2) VERIFIES it is real — resolves to a DOI / academic-graph record, the anti-hallucination guard ("a paper that cannot be verified is not found", the fetch-before-use guarantee shared with `fetch-articles`/R12); (3) determines its FULL-TEXT ACCESS STATE — (a) agent-fetchable, (b) online but needs one human step (an institutional/library login or an author/repository request), or (c) unavailable (abstract-only). It surfaces each entry to the student as a decision card — relevance (1–20, lists sorted highest-first) · one-to-two-sentence gloss · real ✓ · access traffic-light (✅ fetch / 🟡✔️ one human step / ❌ abstract-only) · provenance — with a 🔁 logo on articles re-used across both lists (summarized once). The student (with the agent) chooses inclusion; the verified, included set hands to `paper-engagement`, and the access-state drives that skill's fetch routing. Fires after `literature-discovery` in the stage-7 flow. Status — DRAFT (Tier 2; first draft 2026-06-29).
---

# Literature Filter and Verify

**Last edited:** 2026-06-29 (Cowork — **teacher-admin critique applied** (F1.1 supplied-unverified verification state; F1.2 consumer field-set named; F1.3 🔁 ownership; F2.1 V5 precedence one-directional; F2.2 failed-human-step → ❌ degradation; F2.3 glyph legend). Same day — **canonical surfacing spec added** (educator-approved): relevance on a **1–20 scale**, lists **sorted highest-first**; the **🔁 re-used logo** replacing the methods-list sub-division; the access **traffic-light** (✅ fetch / 🟡✔️ one human step / ❌ abstract-only) with **interlibrary-loan and purchase routes struck**; the closing-prompt wording where the **student** chases an unavailable article via the teacher. Prior same day — first draft. Second of the literature-review trio. Authored against `literature-discovery` (the candidate set it consumes), `conduct-literature-review` (the soft-gated 2–10 counts; the abstract-only edge case), `fetch-articles` (403-is-final / no-paywall-circumvention; the anti-hallucination fetch-before-use guarantee, R12), the research-agent SOUL, and the educator's access-triage addition of 2026-06-29 (verify two things, three access states; surface rank + gloss + real + access). Pairs with `literature-discovery` (upstream) and `paper-engagement` (downstream).)
*Editing convention: see `00-handoff.md` → "Editing conventions". Status section at the bottom records the draft-vs-promoted lifecycle.*

> **Tier-2 reconciliation flags (for the research-agent build):** (1) the **research-agent dispatch/position model** (shared with the trio). (2) **The reading-list home** (the catalog these checks write into — §11 file-ownership; proposed as the reading-list surface). (3) **The access-probe mechanics** — exactly how the skill tests fetchability (the `fetch-articles` HEAD/landing-page probe vs. a dry-run fetch) is a build detail. The **content** of the checks is the reviewable substance.

## What this skill is

The **second** of the literature-review trio and its **gatekeeper**: it turns `literature-discovery`'s raw candidates into the **decision-ready reading lists** the student actually reads. It does not read the articles deeply (that is `paper-engagement`) — it produces the **triage layer** the student needs to choose what to include. For each candidate, three operations:

1. **Rank by relevance** to the reading brief — topic relevance for the topic list, method relevance for the methods list — on a **1–20 scale**, and **sort each list highest-first**. Ranking is **advice to the student**, never an auto-include/exclude: the student decides inclusion (the counts are soft-gated 2–10 per synthesis at the mentor's stage-7 gate; this skill helps assemble a sufficient, well-ordered field, it does not enforce the count).

2. **Verify it is real** — resolve the candidate to a **DOI / academic-graph record** (the script's resolve operation, shared with `literature-discovery`). This is the **anti-hallucination guard**: a candidate that does not resolve to a real record is **dropped, never listed** — the same structural "a paper that cannot be verified is not found" guarantee `fetch-articles` and R12 carry. No fabricated or unresolvable citation reaches the student's reading list. **Supplied articles are the one nuance (F1.1):** an `add this <DOI/URL/citation>` reference runs resolve like any candidate (unresolvable → dropped, with a specific ask for a better identifier). A **supplied PDF** the student physically holds is kept even if it won't resolve — the file exists — but "the file exists" is **not** "the work is a confirmed real publication": an unresolvable supplied PDF is surfaced in the distinct **`supplied — unverified`** state, **never** under the `real ✓` glyph, with a nudge to confirm the source with the teacher. Only an academic-graph / DOI resolution earns `real ✓`.

3. **Determine the full-text access state** — three-way (the educator's 2026-06-29 addition):
   - **(a) Agent-fetchable — ✅** — the full text is openly reachable and `fetch-articles` can stage it (open access, a public PDF, a repository copy).
   - **(b) Online but needs one human step — 🟡✔️ (the yellow check)** — the full text exists online but requires a person to act. The card **names the exact step**: an **institutional or library login**, or an **author / repository request**. Routed to the student and, where institutional access may exist, the **research teacher or faculty mentor**. If that single human step is **exhausted without producing the text** (login unavailable, no reply), the entry **degrades to ❌ abstract-only** (same flag) rather than waiting indefinitely (F2.2). *(Interlibrary-loan and purchase routes struck 2026-06-29 — out of scope; access tops out at a single login-or-request step.)*
   - **(c) Unavailable — ❌** — no reachable full text. The article can still be included **abstract-only**, flagged (the `conduct-literature-review` abstract-only edge case — permitted, discouraged for a list's most core articles).

## The surfacing spec — the decision card (canonical, educator-approved 2026-06-29)

The two lists are surfaced **separately** (topic list, then methods list), each **sorted by relevance, highest first**. Each entry is a compact decision card so the student can choose inclusion at a glance:

> **[N/20] · [Author (year)]** — *[venue]* [🔁 if re-used]
> *[one-to-two-sentence gloss — what it is / why it might fit]*
> [ real ✓ | supplied — unverified ] · [ ✅ | 🟡✔️ + the exact step | ❌ ] · *[provenance: found by search / added by you / curriculum corpus]*

**The fields:**
- **N/20** — the relevance ranking (1–20); each list is sorted highest-first. Ranking is **advice**; the student chooses inclusion.
- **real ✓ / supplied — unverified** — `real ✓` means it resolves to a DOI/academic-graph record; nothing fabricated is listed. A **supplied PDF that won't resolve** shows as **`supplied — unverified`** instead (the student holds the file, but it isn't confirmed against an academic graph — confirm the source with your teacher). `real ✓` is never shown for an unresolved item.
- **access** — the traffic-light: **✅** fetch now · **🟡✔️** one human step (a login or a request), named · **❌** no full text, abstract-only.
- **provenance** — found by search · added by you (student/mentor-supplied) · curriculum corpus.
- **🔁 (re-used logo)** — the article serves **both** lists: it is summarized **once** (under Topic) and counts for Methods too. Marked on both lists; `paper-engagement` writes its single nine-item summary under Topic and does not re-summarize it. The flag originates in `literature-discovery` (which builds the methods list off the topic list); this skill **surfaces** it and may **additionally** set it for an article that ranks onto both lists at filter time (F1.3). *(This replaces sub-dividing the methods list into "re-used" vs. "new" sections — one sorted list, the logo carries the distinction.)*

The **gloss is a distinct artifact** from the nine-item summary `paper-engagement` later teaches: the gloss is a **triage line** (drawn from the abstract/record, to decide inclusion); the summary is the **deep paper-content read** the student writes during engagement. Keeping them separate prevents the gloss being mistaken for the required summary.

**A legend travels with every surfacing** so the glyphs are never bare: the N/20 ranking, real ✓ (or `supplied — unverified`), the ✅/🟡✔️/❌ access states, and the 🔁 re-used logo.

**The closing prompt** invites inclusion and routes the access cases: the agent fetches the ✅ ones and walks the student through the 🟡✔️ step; for an ❌ article, the framing is *"we'll mark it as 'abstract only,' or you can try to chase it down via your teacher."* The chase is the **student's**, via the teacher — the agent does not pursue full text beyond its fetch lane (the no-circumvention discipline).

## How the access state drives `paper-engagement`
The access-state is the routing input to the next skill:
- **(a)** → `paper-engagement` auto-fetches via `fetch-articles` (R7a).
- **(b)** → `paper-engagement` routes the student through the named human-in-the-loop steps before settling; the article waits in the list until the text arrives.
- **(c)** → `paper-engagement` proceeds **abstract-only**, flagged for the student and the mentor's synthesis gate.

## What this skill writes to the workspace
- **The verified, triaged reading lists** (topic + methods) — each entry carrying rank, gloss, real-confirmation, access-state, and provenance. *(Home: the reading-list surface — §11 flag.)* The **included** set (the student's inclusion choices) is marked for `paper-engagement`.
- It writes **no** article PDFs itself (that is `fetch-articles`, invoked by `paper-engagement` at engagement time) and **no** paper content (that is the student's, during engagement).

## Cross-agent handoff
Inbound from `literature-discovery` (the candidate set — this skill relies on each candidate's **abstract** (the gloss source), **provenance**, **DOI/identifiers** (the resolve input), and the **dual-purpose cross-flag**; the **access state is not received** — it is this skill's to determine. F1.2). Hands the **included, verified, access-stated** reading lists **forward to `paper-engagement`**. Uses the discovery script's **resolve** operation for verification and `fetch-articles`' reachability rules for the access probe. A defense-in-depth note: this skill's existence-verification is the **structural** guarantee at the source — **mandatory and standing on its own**; the Review Agent's `claim-verification` (V5 function-2 — "are these real articles?") is an **additional** student-run spot-check layered on top, never what makes this step skippable (F2.1).

## Edge cases (initial)
- **A candidate will not verify.** Dropped, never listed (anti-hallucination). If it came from a supplied *citation* the student is sure of, the skill says specifically why it could not be resolved and asks for a better identifier — it does not list it on faith. *(A supplied *PDF* the student physically holds is the one exception — kept as **`supplied — unverified`**, never `real ✓`; F1.1.)*
- **Access state (b) but the student has no route.** Surface it specifically; route to the research teacher or faculty mentor (institutional access may exist); never substitute an unofficial copy (the `fetch-articles` rule).
- **A core article is (c) unavailable.** Permitted abstract-only but flagged; the full-text hunt runs the legitimate channels first (library, teacher, author email) — the same routing as `conduct-literature-review`'s abstract-only edge case.
- **Relevance is genuinely ambiguous.** Rank it honestly with the uncertainty noted; inclusion is the student's call (and the mentor's at the synthesis gate), not the skill's to decide.
- ~~**A purchase is the only access route.** Flagged as a cost decision routed to the student/teacher — never auto-incurred against the budget.~~ *(Struck 2026-06-29 — purchase and interlibrary-loan routes are out of scope; access tops out at the 🟡✔️ login-or-request step, else it is ❌ abstract-only.)*

## Status
**DRAFT (Tier 2), first draft 2026-06-29.** Second of the literature-review trio. Through the teacher-admin critique loop (2026-06-29, no blocking — findings applied: F1.1/F1.2/F1.3/F2.1/F2.2/F2.3). Reconciliation flags above are Tier-2 build items (dispatch/position model; reading-list home; access-probe mechanics), not gates on content. The anti-hallucination verify-before-list guarantee mirrors `fetch-articles`/R12. Pairs with `literature-discovery` (upstream) and `paper-engagement` (downstream); the mentor-side counterpart is `conduct-literature-review`. Eventual location: here.
