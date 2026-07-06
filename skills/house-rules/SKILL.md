---
name: house-rules
description: Editing-attribution convention for the research-agent profile. Fires only when you are about to edit, write to, or revise one of your own skill SKILL.md files in `~/.hermes/profiles/research-agent/skills/` — or the staging drafts of those skills at `~/Downloads/hermes-curriculum/build/research-agent/skills/`. Does NOT fire on per-student workspace files (`project_design.md`, `reference_articles.md`, `decisions.md`, `working_paper.md`, etc.) — those are the student's own work and follow a different provenance discipline. Does NOT fire on edits to curriculum design documents in `~/Downloads/hermes-curriculum/design/` or the handoff — those are teacher-admin and Cowork territory; if asked to edit them, refuse and route the work to teacher-admin or to Cowork. Carries the editor identifier this profile must use (`research-agent`), the document-level and section-level attribution markers required on substantive edits, and the closed-question retention discipline for open-items catalogues. Status — draft, awaiting first live use.
---

# House Rules — Editing Conventions for the Research-Agent Profile's Own Skills

**Last edited:** 2026-05-26 (Cowork — initial draft, parallel to the teacher-admin house-rules skill, scoped narrowly to research-agent's own skill files)
*This skill's own editing follows the convention it documents.*

## What this skill is

This skill is the operational version of the editing-attribution convention recorded in `~/Downloads/hermes-curriculum/00-handoff.md` under the heading "Editing conventions — attribution markers across the canonical documents." The handoff section is the canonical source; this skill makes the convention discoverable and enforceable from inside the research-agent Hermes profile, *for the narrow case where the research-agent is being asked to edit one of its own skills*.

The convention exists because the curriculum's documents are edited by multiple agents — Cowork sessions, teacher-admin Hermes profile, the educator directly, occasionally linters, and (rarely) the student-facing agents when their own skills need refinement. Without attribution markers, an agent reading a changed document cannot tell who shaped its current state, which produces real coordination problems. For the research-agent, this matters only at the narrow boundary of its own skill files — not the per-student workspace work that is the research-agent's primary job.

## When this skill fires

Recognition is **situational and narrow**. Fire when:

- You are about to write to, edit, or substantively revise one of your own skill SKILL.md files at `~/.hermes/profiles/research-agent/skills/<skill-name>/SKILL.md`.
- You are about to write to, edit, or substantively revise the staging draft of one of your own skills at `~/Downloads/hermes-curriculum/build/research-agent/skills/<skill-name>/SKILL.md` (this is the working folder Cowork uses for skill authoring before commit to the research-agent GitHub repository).
- You are about to *create* a new skill in either of the above locations.
- The user (or the learning loop) asks you to "improve", "refine", "extend", "fix", or "rewrite" one of your own skills.

## When this skill does NOT fire

Most of your work as the research-agent is *not* under this convention. The skill specifically does not fire on:

- **Per-student workspace files.** When you write to `working_paper.md` (Methods section, Results section, parts of Discussion), `reference_articles.md`, `decisions.md`, `project_design.md`, or any file under the student's `~/research-curriculum/` workspace, that is *the student's own work product*, not a canonical curriculum document. The student's workspace files have their own provenance through the conversation and through `decisions.md` entries; they do not get document-level "Last edited" markers from you. Treat workspace-file editing as part of your normal job.
- **Curriculum design documents.** If the user asks you to edit any file under `~/Downloads/hermes-curriculum/design/` (architecture spec, decision-history, decision-log, implementation plan, platform primer, dispatch contract, program-context) or the `~/Downloads/hermes-curriculum/00-handoff.md` file at the working-folder root, **refuse and route the request.** Those documents are teacher-admin and Cowork territory. The student-facing research-agent is not the right surface for curriculum-level edits. Say something like: *"That file is one of the curriculum's design documents, which I'm not the right agent to edit. The teacher-admin Hermes profile or a Claude Cowork session is the appropriate path — could you bring this request to one of those?"*
- **Other agents' skill files.** If the user asks you to edit a skill under `~/.hermes/profiles/project-mentor/skills/` or `~/.hermes/profiles/review-agent/skills/`, **refuse** — those skills belong to the other agents' profiles and editing them from research-agent would create cross-profile attribution confusion. Route the request to the appropriate profile.
- **The research-agent SOUL.** Your SOUL is canonical-and-bundled and is deliberately excluded from the attribution convention. If a request would have you modify the SOUL, stop and ask the user first — modifying the SOUL has implications for your own behavior that this skill is not authorized to absorb.
- **Reads** of any of the above files. Reading is not editing.
- **Non-markdown files.** YAML configs, Python scripts, JSON files in your profile have other attribution mechanisms (git history); they are not under the markdown-document convention this skill governs.

## What this skill does (when it does fire)

When the skill fires — you are about to edit one of your own skill SKILL.md files — before you begin the edit, do these three things in order:

### Step 1 — Identify yourself with the correct editor identifier

You are the **research-agent** profile. Whenever you mark a document under this convention, the editor identifier is `research-agent`. The other identifiers in the curriculum's editor list (`Cowork`, `teacher-admin`, `review-agent`, `educator`, `linter`) belong to other agents and contexts; do not use them for your own edits.

### Step 2 — Update the document-level "Last edited" line

Every research-agent skill SKILL.md file carries a `**Last edited:** YYYY-MM-DD (editor — short summary)` line near the top, under the document title (under any pre-existing Status or Last verified header, where one exists — those coexist). On every substantive edit, update this line with:

- **Today's date** in `YYYY-MM-DD` format
- **`research-agent`** as the editor
- **A short summary** of what you are about to change (one phrase, not a sentence)

Example:

```
**Last edited:** 2026-05-26 (research-agent — refined the literature-discovery trigger language to handle the case where the student's reference articles have empty bibliographies)
```

If the skill file does not yet have a "Last edited" line, add one as part of your edit.

### Step 3 — Add a section-level revision marker for substantive changes

For substantive changes to a specific section — a rewritten paragraph, a new sub-section, a corrected citation, a removed claim, a new operational rule — add an italic one-liner at the end of the revised section:

```
*Revised 2026-05-26 (research-agent) — short description of what changed.*
```

**Mark substantive changes, not every keystroke.** Typo fixes, cross-reference number bumps, formatting normalization, and small clarifying word choices do not need section-level markers. Rewritten paragraphs, new operational rules, corrected citations, and removed claims do.

If you are uncertain whether a change is substantive enough to warrant a section-level marker, lean toward marking.

## The closed-question retention discipline

If one of your skills has an "Open authoring items" or similar open-questions catalogue, **resolved items are retained with strikethrough and a resolution date**, not deleted:

```
~~3. **The original open question text.**~~ *Resolved 2026-05-26 (research-agent) — short note pointing to where the resolution lives.*
```

This prevents a future session from reopening a settled question as if undecided. Deletions are reserved for items retired *without* resolution (the concern was eliminated by structural change), and the retirement is noted in the document's revision summary.

## Before you edit — checklist

1. **Confirm the file path is under your own profile's skill directory** — either `~/.hermes/profiles/research-agent/skills/` (live) or `~/Downloads/hermes-curriculum/build/research-agent/skills/` (staging). If it's neither, this skill does not apply.
2. **Read the skill's current "Last edited" line** (if one exists) to know the prior edit's context.
3. **Read the section you're about to change** before changing it. The convention is "edit in place, preserve voice and structure"; large rewrites should be discussed with the educator before you make them.
4. **Make the edit.**
5. **Update the "Last edited" line** with today's date, `research-agent` as the editor, and your short summary.
6. **Add a section-level marker** if the edit is substantive.
7. **If the edit resolves an open-items catalogue entry**, apply the closed-question retention discipline.

## What this skill does NOT do

- **Author the curriculum's content for you.** The skill governs *how* you edit your own skills, not *what* they say. Substantive content decisions about a skill's behavior are between you and the educator.
- **Govern your normal student-facing work.** Workspace-file editing — the bulk of what you do — is outside this convention's scope. You do not add attribution markers to `working_paper.md` or `decisions.md` entries.
- **Authorize you to edit other agents' files.** The project-mentor's skills, the review-agent's skills, the curriculum design documents, the SOULs — all out of scope. Refuse and route.

## Where the convention lives canonically

The canonical source for the editing convention is `~/Downloads/hermes-curriculum/00-handoff.md` under the heading "Editing conventions — attribution markers across the canonical documents." That section is the source of truth. If you are ever uncertain about what the convention requires and this skill's body does not give you a clear answer, read the canonical section via `read_file ~/Downloads/hermes-curriculum/00-handoff.md` and find the "Editing conventions" heading.

## The editor identifier list (current)

For reference when reading other documents' attribution markers:

- **`Cowork`** — Claude Cowork session (filesystem-native Claude agent)
- **`teacher-admin`** — Hermes teacher-admin profile (curriculum-side critique passes, distribution-file authoring)
- **`research-agent`** — this profile (your identifier on every edit you make to your own skills)
- **`review-agent`** — Hermes review-agent profile (analogous to research-agent for its own skills)
- **`educator`** — direct hand-edit by the user
- **`linter`** — formatting-only changes from a linter or formatter pass

Do not invent identifiers. If you encounter an edit that doesn't fit one of the existing identifiers, ask the user.

## Status

**Draft, awaiting first live use.** Authored 2026-05-26 (Cowork) as part of the attribution-convention adoption pass; parallel to the teacher-admin house-rules skill, scoped narrowly to research-agent's own skill files. The skill's behavior has not yet been exercised against a real research-agent editing session. The first few times it fires, expect to refine the trigger language (the `description:` field) based on whether it correctly recognizes the cases where editing one of the research-agent's own skills is about to happen versus the cases where it is not (most importantly, the cases where the user is asking for workspace-file work — which should NOT fire this skill). The skill is `hermes curator pin`-eligible — once exercised and refined, pin it so the curator's idle-stale-archive sweep does not touch it.
