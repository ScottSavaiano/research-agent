---
name: conduct-analysis
description: Conducts the research agent's EXECUTION-regime ANALYSIS stage on the seven-step Plan→Teach→Review→Approve→Execute→Report→QC-audit loop. The agent writes a teaching analysis plan (the analytic approach, the specific scripts it will write and run, any human-in-the-loop steps, its two Review-Agent checkpoints), teaches it until the student understands, routes a handoff prompt to the Review Agent for a PLAN REVIEW, gets joint student+teacher approval, then EXECUTES the analysis code itself (writing and running the scripts) while the student directs and owns the work, writes a post-execution report into the Data Analysis Log, and routes a second handoff to the Review Agent for a QC AUDIT plus 3–5 hallucination spot-checks the student runs. The analysis sibling of source-and-prepare-data: it fires AFTER that stream's data is prepared, once per execution stream — the CORE analysis at Stage 19 and the EXTENSION analysis at Stage 23 — running each stream's Stage-14 analytic plan on the prepared dataset, which evolves as the real data shows what it supports (the one thing frozen at the seal is the Hypotheses and/or Expected Findings). The per-method-family analysis skeleton in section-scaffolds.yaml supplies the ordered teaching steps of the plan and the spine of the log (taught with family-specific examples). Produces two outputs: the UNGRADED Data Analysis Log (analysis/…-data-analysis-log.md) — the workbench record of the whole seven-step trail — plus the analysis artifact (code + tables/figures/estimates), staged in the workspace analysis/ folder; AND the GRADED Analysis and Execution Paragraph (Core at Stage 19 / Extension at Stage 23), a living paper paragraph fed by the log that narrates the whole arc — planning, execution, amendments (how the analysis evolved), and the QC steps including the student's own spot-checks of the agents' work — handed to the paper via an R10 writing_handoff (return-to-mentor → scaffold-section, function-not-content), exactly like source-and-prepare-data hands off the Dataset Creation Paragraph. The log also feeds the student's later Results Section and a short Methods analytic-strategy line. The agent runs the analysis code as disclosed, cited research tooling; the student directs it, understands it, and owns the work and its contribution audit. Each stage's two Review-Agent checkpoints (step-3 plan review, step-7 QC audit) each produce a dated review .md in the workspace reviews/ folder that the agent composes a prompt for and later retrieves. Status — draft, awaiting teacher-admin critique and educator review.
---

# Conduct Analysis

**Last edited:** 2026-07-08 (Cowork — **body-prose refinements** per the model-memo update. (1) **Sealed-plan framing retired:** the methods and analysis *evolve* as the student learns what the real data supports, and the student keeps the relevant paper paragraph current with what they actually did; the **one** thing frozen at Stage 15/16 is the **Hypotheses and/or Expected Findings** (anti-HARKing preserved as that one frozen thing). (2) **New graded paper output:** the Analysis stage now produces the graded, living **Analysis and Execution Paragraph** (Core 19 / Extension 23) *in addition to* the ungraded Data Analysis Log — this skill now returns an **R10 `writing_handoff`** (return-to-mentor → scaffold-section, function-not-content), exactly like `source-and-prepare-data`'s Dataset Creation Paragraph; the paragraph narrates the whole arc — planning, execution, amendments, **and** the QC steps including the student's own QC/spot-checks of the **agents' work** (a Regeneron/contribution strength). This reverses the prior "analysis is log-only / hands nothing to `working_paper.md` / no `writing_handoff`" statements. (3) **Review Agent** capitalized in prose; the two per-stage checkpoints each save a **dated review `.md` in a new `reviews/` folder** the agent composes a prompt for and retrieves. (4) **QC** spelled out as **Quality Control (QC)** at first mention. Scripted-moment quotes untouched. Prior: 2026-07-07 (Cowork — **re-authored to the seven-step Plan→Teach→Review→Approve→Execute→Report→QC-audit execution model**, per `design/execution-plan-model-2026-07-07.md` (the authoritative model memo of this date). **Supersedes the same-day mini-cycle-beats draft** built against `design/analysis-journal-2026-07-07.md`: the "student runs their own scripts / mini-cycle beats / Analysis Journal as graded / STS-eligibility authorship line" premise is retired. What survives from that draft is the per-family analytic **step structure** — now the **teaching content of the analysis plan** and the **spine of the Data Analysis Log**, not a student-run beat loop. STS correction applied: running analysis code is permitted research tooling (disclosed + cited), so the **agent executes the analysis**; the old "authorship line" section and Moment 3 (decline-to-analyze) are removed. Artifact renamed **Analysis Journal → Data Analysis Log** (ungraded workbench). Modeled on its execution sibling `source-and-prepare-data` (execution-lane dispatch + forward-continue, no return-to-mentor; own execution-track records; does not write `project_paper_status.md`; R11 review-agent handoff, now the step-7 QC audit). Stage numbers unchanged (core 19 / extension 23). Cites the three-stream/25-stage memo + spec §4.2/§4.5/§5.2.))
*Editing convention: see `00-handoff.md` → "Editing conventions" for editor identifiers and revision-marker rules. This skill also carries a Status section at the bottom recording the draft-vs-promoted lifecycle.*

## What this skill is

The research agent's **execution-regime analysis stage**. It takes the **prepared, analysis-ready dataset** (from
`source-and-prepare-data`, Stage 18/22) and the **Stage-14 methodology** (which already specifies this stream's
models, estimators, and robustness plan) and runs the **seven-step execution loop** on the analysis: the agent **plans**
the analysis as a piece of teaching, **teaches** it, routes it to the **Review Agent** for a plan review, gets **joint
student+teacher approval**, **executes** the analysis code itself, **reports** what it did into the Data Analysis Log,
and routes the report to the **Review Agent** for a Quality Control (QC) audit and spot-checks. It is the analysis counterpart of
`source-and-prepare-data` and, like it, runs **twice per cycle** — the **core** analysis at **Stage 19** and the
**extension** analysis at **Stage 23**, each after that stream's Data stage.

Its products: the **analysis artifact** (the code the agent wrote and ran + the tables/figures/estimates it produced),
the **Data Analysis Log** (the ungraded running record of all seven steps), and — fed by the log — the **graded Analysis
and Execution Paragraph** (the **Core** paragraph at Stage 19, the **Extension** paragraph at Stage 23), the living paper
paragraph this stage hands to the paper. The agent runs the code; the **student directs the analysis, understands every
step, and owns the work** — the pedagogy and the STS contribution audit are why the student is in the loop at every gate,
not because running code is off-limits.

**Running the analysis is permitted research tooling.** Regeneron STS permits AI use for student research projects when
disclosed and cited; the hard line it draws is on **writing** the Research Report, not on running analysis. So the agent
writes and runs the analysis scripts as a disclosed, cited instrument. The student is at the wheel — planning, learning,
approving, and auditing — because they must be able to describe and defend the work (evaluation area 2 / application
Q12), which is a pedagogy-and-contribution reason, never an eligibility rule about who types the code.

**It produces a graded paper paragraph — and an ungraded workbench log.** Like the Data stage, which hands its
**Dataset Creation Paragraph** off to the paper (R10), this stage hands its **Analysis and Execution Paragraph** off to
the paper via an **R10 `writing_handoff`** (return-to-mentor → scaffold-section, function-not-content) — the **Core
Analysis and Execution Paragraph** at Stage 19, the **Extension Analysis and Execution Paragraph** at Stage 23. That
paragraph is the **graded** output: a living paragraph, fed by the log, that narrates the whole arc — the planning, the
execution, the amendments (how the analysis evolved as the real data showed what it supports), **and** the Quality
Control steps, explicitly including the student's own QC/spot-checks of the **agents' work** (a Regeneron/contribution
strength — the student demonstrating oversight of disclosed AI tooling). The **Data Analysis Log** stays an **ungraded
workbench record** of all seven steps and feeds the paragraph; the log also feeds the student's own later **Results
Section** and a short **analytic-strategy line in Methods**, written during the Results/Discussion write-up.

## When this skill fires

Dispatched in **execution regime**, after the proposal seal (Stage 16) and the one project-level **IRB** (Stage 17), once
that stream's **Data** stage is done: **Stage 19** after the **core** Data stage (18), **Stage 23** after the
**extension** Data stage (22). It runs in the research agent's execution lane and does not return to the mentor
mid-stage; at the end it **returns to the mentor with an R10 `writing_handoff`** for the Analysis and Execution Paragraph
(scaffold-section), exactly as the Data stage does for the Dataset Creation Paragraph. Its two **Review-Agent
checkpoints** (the step-3 plan review and the step-7 QC audit) are student-mediated agent handoffs, not returns to the
mentor: for each, the agent composes a full handoff prompt pointing the Review Agent at the relevant docs and instructing
it to save a **dated review `.md` in the workspace `reviews/` folder**, which the agent later retrieves. The
paper/position stage advances **mentor-side** when the student returns for the paragraph scaffold and, later, the Results
write-up.

## The seven-step loop (how this stage runs)

The Analysis stage runs the same **seven-step loop** as every execution/prep stage (`design/execution-plan-model-2026-07-07.md`).
The gate is at the **plan** level, not per line of code:

1. **Plan.** The agent writes an **analysis plan whose purpose is to teach**: the analytic principles and concepts, the
   **ordered analytic steps** (from this family's `analysis` skeleton, reconciled with the Stage-14 plan), the
   **specific scripts it intends to write and run** (named in the plan — e.g., `01-fit-primary-model.R`,
   `02-robustness.R`), any **human-in-the-loop step** it cannot do itself written as *"you have to do this for me — here
   are the steps"* (rare in analysis — e.g., a credentialed compute environment), and it **schedules its two
   Review-Agent checkpoints** (steps 3 and 7).
2. **Teach.** The agent teaches the plan and answers questions, going deeper until the student **signals understanding**.
   Teaching lives up front, in the plan — not spread across per-step execution.
3. **Review-Agent plan review.** On the understanding-signal, the agent **composes a full handoff prompt** — pointing the
   **Review Agent** at the Data Analysis Log plan, `project_design.md`, and the methodology, and instructing it to **save
   a dated review `.md` in `reviews/`** (e.g., `reviews/2026-05-14-core-analysis-plan-review.md`) — which the student
   pastes to the Review Agent for an expert methodological review of the *plan*. The student signals when it is done; the
   agent **retrieves the dated review file**, processes any changes with the student, and **loops back through steps 1–2**
   as needed.
4. **Approve (the plan).** The reviewed, revised plan is approved **jointly by the student (understanding) and the
   teacher** before anything runs.
5. **Execute.** The agent **writes and runs the analysis code directly** — individual acts of coding are **not** gated
   step by step; the agent just does them, following the approved plan. The student directs and performs any
   human-in-the-loop step the plan assigned to them.
6. **Report.** The agent writes a **post-execution report** into the Data Analysis Log: what it actually ran, the
   results/diagnostics, and **how the analysis evolved** — a script that changed, a step added, the methodology adjusted
   to fit what the real data supports — and it keeps the relevant paper paragraph current with what was actually done
   (framed as rigorous practice, below).
7. **Review-Agent QC audit.** The agent **composes a second full handoff prompt** — pointing the **Review Agent** at the
   report and the output files in `analysis/`, and instructing it to **save a dated audit `.md` in `reviews/`** (e.g.,
   `reviews/2026-05-14-core-analysis-qc-audit.md`) — which the student pastes to the Review Agent. The audit **flags any
   unexpected findings** and suggests **3–5 spot-checks the student runs themselves** to catch any hallucination in the
   execution step. This is the R11 / V5-function-2 AI-error guard, now a scheduled step. The agent **retrieves the dated
   audit file** and **prompts the student to report back what the audit and their spot-checks turned up so it can log
   them.**

**Loop-back on the QC audit (step 7).** The student deep-dives each flag. If it is an error that **compromises the whole
analysis (or dataset)**, it loops **all the way back** — the agent re-executes and re-reports, and the stage is
re-audited; the stage is not approve-complete until the audit comes back clean. If it is a **smaller error**, the agent
just fixes it and issues a **new report** — no full loop-back. Either way, **everything is logged.**

**The ordered analytic steps come from the family skeleton.** The step sequence the plan teaches — and the spine of the
log — is this stream's method family's **`analysis` skeleton** in `section-scaffolds.yaml` (the sibling of that family's
`methods`/`results` skeletons), reconciled with the student's own Stage-14 plan (add/prune/reorder to fit the actual
study). Each skeleton row carries a step, a `record` prompt (what to log), and a `note` with a **family-specific
example** from the exemplars — so the student is *shown* how a published study in their family ran and reported that
step. For an **off-menu family (item 13)** with no skeleton, the plan's steps are **built live with the student** from
their methodology, the same way the paper scaffold is for that item.

## What it writes — the Data Analysis Log and the Analysis and Execution Paragraph

This stage produces two things: the **ungraded Data Analysis Log** (the workbench, below) and — fed by it — the **graded
Analysis and Execution Paragraph** handed to the paper (R10; see "What feeds the paper"). The log is the workbench; the
paragraph is the graded distillation.

One log per stream, staged in the workspace **`analysis/`** folder — the **ungraded workbench record of the whole
seven-step trail**:

- `analysis/core-data-analysis-log.md` — the **Core Data Analysis Log** (Stage 19).
- `analysis/extension-data-analysis-log.md` — the **Extension Data Analysis Log** (Stage 23).

The log holds **all seven steps for the stage**: the plan (the teaching notes + the named scripts), the teaching Q&A
worth keeping, the **Review Agent's plan review** (step 3, retrieved from `reviews/`) and how it changed the plan, the **joint approval**, the
**execution + report** (steps 5–6), the **QC audit** (step 7) with its suggested spot checks and the **student's results
running them**, and the resolution of anything the audit flagged. Because several of these come back through the
*student* (the plan review, the audit, the spot-check results), the agent **explicitly prompts the student to report
what they found so it can log it** — *"tell me what you found so I can add it to your log."*

A suggested skeleton for the execution + report entry:

```
### Execution report — <the analytic step / block, in the student's words>
- **Planned:** what this step set out to do, and why (tie to the methodology).
- **Ran:** the script the agent wrote and ran (name + the exact call), and what it did.
- **Result:** the output and diagnostics — the numbers, the assumption checks, what stands out.
- **How the analysis evolved:** any script that changed, step added, or way the methodology was
  adjusted to fit what the real data supports — keep the relevant paper paragraph current with
  what you actually did; the one thing frozen is your Hypotheses and/or Expected Findings.
```

The analysis **artifact** — the runnable scripts the agent wrote and their tables/figures/estimates — is staged
alongside the log in `analysis/`. The log references the artifact (which script, which call) rather than pasting large
outputs.

**The methods and analysis evolve; the one frozen thing is the Hypotheses and/or Expected Findings.** What is frozen at
the seal (Stage 15/16) is only the **Hypotheses and/or Expected Findings** — you never change your predictions after
seeing the data (the anti-HARKing line). The methods and the analysis, by contrast, **evolve as the student learns what
the real data supports** (a model that will not converge, an assumption that fails): the agent **refines the analysis to
fit the data, and the student keeps the relevant paper paragraph current with what they actually did** — the Analysis
and Execution Paragraph, in the student's own words. Keeping that paragraph current with the real work is exactly what a
rigorous study does.

## What feeds the paper

This stage feeds the paper in two ways:

- **Directly, via an R10 `writing_handoff`.** The **Analysis and Execution Paragraph** (Core at Stage 19 / Extension at
  Stage 23) is handed to the paper on the `source-and-prepare-data` pattern — return-to-mentor → scaffold-section,
  function-not-content — where the scaffold gives the paragraph its shape and **the student writes every word**. It is
  the graded output, and it is kept current as the analysis evolves.
- **Downstream, student-written.** The **Data Analysis Log** is the source the student later distills — **themselves**,
  when they write Results/Discussion — into the **Results Section** (the findings, the robustness/sensitivity story of
  which checks held) and a short **analytic-strategy line in the Methods** (the analysis *as settled*: the final models,
  estimators, software, robustness), supported by the paper skills there.

## What this skill writes to the workspace

- `analysis/` — the **Data Analysis Log** for this stream (`core-data-analysis-log.md` /
  `extension-data-analysis-log.md`) and the **analysis artifact** (the scripts the agent wrote + their
  tables/figures/estimates).
- `reviews/` — the two **dated Review-Agent files** for this stage: the step-3 plan review and the step-7 QC audit (e.g.,
  `reviews/2026-05-14-core-analysis-plan-review.md`, `reviews/2026-05-14-core-analysis-qc-audit.md`), retrieved by the
  agent after the student runs each handoff.
- `decisions.md` — any analytic decision whose rationale belongs in the record (e.g., a consequential re-specification or
  a way the analysis evolved to fit the data), per the standalone-entry convention.
- It hands the **Analysis and Execution Paragraph** to the paper via an **R10 `writing_handoff`** (return-to-mentor →
  scaffold-section), exactly as `source-and-prepare-data` does for the Dataset Creation Paragraph; it does not itself
  write finished prose into `working_paper.md`, and it does not write `project_paper_status.md` (the paper/position stage
  advances mentor-side on the student's return).

## The scripted moments

Per the established convention: adapt wording and re-point examples to the student's study; preserve the core steps and
their order; concise, example-driven, no rationale lectures. **All six are pending the educator voice read
(2026-07-07).**

### Moment 1 — Framing the analysis plan (step 1)

> *Intent: I plan the analysis and teach it to you, you approve it, then I run it while you direct and own it.*
> *Agent (pending educator voice read 2026-07-07):* "Now we run your analysis — but we plan it before we run anything. First I'll write up the plan: the analytic steps we'll take and why, the exact scripts I'll write and run, and where the two Review Agent checkpoints fall. I'll teach you that plan until every piece of it is clear to you — ask me anything; as the researcher who'll present and defend this analysis, you'll want to know it cold. Once you understand it and it's been reviewed and approved, I run the code and you direct it, read the output with me, and own the calls. The whole story — the plan, the review, what I ran, what came back — goes in your Data Analysis Log. Let's start with the plan: here's the first analytic step your methodology calls for, and how I'd run it."

### Moment 2 — Teaching to understanding (step 2)

> *Intent: make the plan fully the student's before it goes to review.*
> *Agent (pending educator voice read 2026-07-07):* "As a budding researcher, you're going to want to be clear on every piece of this before it runs — so walk the plan back to me: what does each step do, why that model and not another, and what would tell us it went wrong? Anywhere it's still fuzzy, that's where we dig in; the clearer this is to you now, the stronger you'll be when you present it. When you can talk me through the plan in your own words, we're ready to send it to the Review Agent."

### Moment 3 — The plan-review handoff (step 3)

> *Intent: hand the plan to the Review Agent with a full prompt; it saves a dated review, which I retrieve.*
> *Agent (pending educator voice read 2026-07-07):* "Good — the plan's ready for an expert methodological review before anything runs. Copy this and paste it to your Review Agent: **‹Review Agent — read my analysis execution plan in my Data Analysis Log, along with `project_design.md` and my methodology, and pressure-test the plan as an expert methodologist: is the analytic approach sound, are the models and estimators right for my data and question, and what would you change? Save your review as a dated file in `reviews/`, e.g. `reviews/2026-05-14-core-analysis-plan-review.md`.›** Run it, then just let me know when it's done — I'll retrieve its review file, we'll work in any changes together and re-teach whatever changed, and then we're ready for approval."

### Moment 4 — Executing and reporting (steps 5–6)

> *Intent: after approval, run the code and write the report; the analysis can evolve, only the Hypotheses stay frozen.*
> *Agent (pending educator voice read 2026-07-07):* "The plan's reviewed and approved, so I'll run it now. I'll write and run `[script]`, and we'll read what comes back together. … Here's the report for your log: what I ran, the estimate and its diagnostics, and anything the real data led us to adjust along the way. Your analysis is allowed to evolve as the data shows you what it supports — the one thing that never changes is your frozen Hypotheses or Expected Findings. Whatever we actually did goes into your [Core/Extension] Analysis and Execution Paragraph, which is exactly what a strong study reports. Read the result with me: is this what your methodology expected to see?"

### Moment 5 — The QC-audit handoff + spot-checks (step 7)

> *Intent: hand the report + output to the Review Agent for a Quality Control audit and 3–5 spot-checks the student runs; retrieve the dated audit, log the spot-check results.*
> *Agent (pending educator voice read 2026-07-07):* "One more checkpoint before this stage is done — a **Quality Control ("QC")** audit. Copy this to your Review Agent: **‹Review Agent — read my analysis execution report and the output files in `analysis/`, run a QC audit and flag anything unexpected in the results, and give me 3–5 spot-checks I can run myself to confirm the analysis was produced correctly. Save the audit as a dated file in `reviews/`, e.g. `reviews/2026-05-14-core-analysis-qc-audit.md`.›** Run the spot-checks it hands you — that's how we catch it if something went wrong in what I ran. Then let me know when it's done: I'll retrieve the audit file, and you tell me what your spot-checks turned up so I can log it and we can settle anything it flagged."

### Moment 6 — A step won't behave (loop-back)

> *Intent: separate a fixable step from a methodology-level change; either way the analysis evolves and the paragraph is updated, Hypotheses stay frozen.*
> *Agent (pending educator voice read 2026-07-07):* "That didn't come out the way the plan assumed — and catching it here is exactly what this stage is for. Two cases. One: it's a fixable step — the model needs a tweak it can take without changing what you're testing — so we adjust that step and I re-run it. Two: your methodology genuinely can't run as written on this real data, so the analysis has to change more substantially. Either way, your analysis is allowed to evolve to fit what the real data supports — the one thing that stays frozen is your Hypotheses or Expected Findings. When it evolves, you update your **Core Analysis and Execution Paragraph** (or your **Extension Analysis and Execution Paragraph**) to describe what you actually did. Keeping that paragraph current with the real work is exactly what a strong study does. Let's tell the two cases apart: what did this step expect to do, and what did it actually do?"

## Edge cases

**Off-menu family (item 13).** No `analysis` skeleton exists; **build the plan's step sequence live with the student**
from their Stage-14 methodology (reading one of their method exemplars for how that kind of analysis is run), and flag
the gap so the educator can vet and, if recurring, add a family skeleton — the same synthesis discipline the paper
scaffold uses.

**A failed/stuck analysis.** A step that will not run (non-convergence, a broken assumption, a dataset limitation the
prep did not catch) surfaces at execution and is handled in the report (step 6): re-specify the analysis to fit what the
real data supports, keep the relevant paper paragraph current with what was actually done, and escalate to a human
(teacher / faculty mentor) when the analysis cannot be made sound. The Hypotheses and/or Expected Findings stay frozen;
only the methods and analysis evolve. It is never resolved by fabricating or hand-editing output.

**A QC-audit flag that compromises the whole analysis.** The step-7 loop-back: the agent re-executes and re-reports, and
the stage is re-audited; it is not approve-complete until the audit comes back clean. A smaller flag is just fixed and
re-reported.

**Synthetic-as-object studies (shape E).** When the methodology's "data" is generated (via
`generate-synthetic-data`), the analysis still runs here on the seven-step loop over that generated dataset and its
fidelity checks — the plan, execution, and log work the same way.

## Where this skill lives in the architecture

A **research-agent execution skill**, bundled in the research-agent distribution, dispatched at Stages 19/23. The
analysis sibling of `source-and-prepare-data`; it consumes that skill's prepared dataset and the Stage-14
methodology, and the family `analysis` skeleton in `section-scaffolds.yaml` (now the teaching steps of the plan + the log
spine). It writes the `analysis/` execution records and the `reviews/` dated Review-Agent files, and hands the
**Analysis and Execution Paragraph** to the paper via an R10 `writing_handoff` (scaffold-section); it does not itself
write finished `working_paper.md` prose or `project_paper_status.md`. Upstream: the stream's Data stage. Downstream: the
paper (the Analysis and Execution Paragraph) and the student's own Results/Discussion write-up (the paper skills), fed by
the Data Analysis Log. The two **Review-Agent checkpoints** (step-3 plan review, step-7 QC audit) and the Friday
integrity audit are the backstops on the analysis record.

## Status

**Draft, re-authored 2026-07-07 (Cowork)** to the seven-step Plan→Teach→Review→Approve→Execute→Report→QC-audit model
(`design/execution-plan-model-2026-07-07.md`), superseding the same-day mini-cycle-beats draft. Authored against the
three-stream / 25-stage architecture memo, the architecture specification (§4.2, §4.5, §5.2), the dispatch contract
(execution-lane dispatch; the step-7 QC audit is the R11 obligation; the step-3 plan review binds the not-yet-built
Review Agent per the model memo §4), and its execution sibling `source-and-prepare-data`. The 2026-07-08 refinements
added the **graded Analysis and Execution Paragraph** (handed to the paper via an R10 `writing_handoff`,
scaffold-section) alongside the ungraded Data Analysis Log, routed the two Review-Agent checkpoints to **dated files in
`reviews/`**, and retired the sealed-plan framing (only the Hypotheses and/or Expected Findings are frozen). Awaiting
teacher-admin critique and the educator voice read of its scripted moments.

### Open authoring items

1. **Scripted moments.** Six scripted moments are **drafted** (framing the plan; teaching to understanding; the
   plan-review handoff; executing + reporting; the QC-audit handoff + spot-checks; the loop-back / deviation-as-rigor
   moment) — **pending the educator voice read (2026-07-07)**, per precedent.
2. **Review-Agent checkpoints.** The step-3 plan review is a **new** pre-execution Review-Agent use (an extension of
   V5-1) that **binds the Tier-3 Review-Agent build** (the Review Agent is not yet built); the step-7 QC audit is the
   existing R11 / V5-2 guard, now a scheduled step. Each checkpoint composes a full handoff prompt and saves a **dated
   review `.md` in `reviews/`** that the agent retrieves; pin the exact handoff-prompt shapes with the Review-Agent
   build, on the `source-and-prepare-data` precedent.
3. **`analysis` skeleton coverage.** Families 1–13 `analysis` skeletons are authored in `section-scaffolds.yaml`, now
   relabeled as analysis-plan teaching steps + Data Analysis Log spine (non-paper); confirm each against its exemplars at
   the educator review, as with the methods/results skeletons.
