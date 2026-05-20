---
name: worklog-daily-report
description: Use when the user provides raw, messy, spoken, or fragmented work notes and wants a review-first cleaned draft, daily worklog, weekly/monthly material, or probation/promotion/performance-review evidence. Preserve raw meaning, align recurring names/projects from prior approved notes when likely, create rough semi-structured review drafts, mark uncertainty, separate work from social/environment context, and give evidence-based goal-relative comments only after approval. Never treat speech-to-text as part of the skill.
---

# WorkLog Daily Report

Use this skill when the user provides pasted raw text notes and wants a daily worklog, weekly/monthly/reporting material, goal-oriented review evidence, or a reviewed reflection summary.

The skill does **not** transcribe audio. Users are responsible for converting speech to text with their own tools and pasting the raw text.

## Core contract

1. Preserve source meaning before polish. Do not invent facts, dates, metrics, names, decisions, blockers, or outcomes.
2. Back up raw text when working in a repository with a `raw/` convention. Existing raw files are source evidence and must not be beautified or rewritten.
3. Cleaned notes are an intermediate review artifact. Show them to the user first.
4. Do not write or update final reports until the user explicitly approves the cleaned notes.
5. Keep final outputs aligned to the repository's existing conventions, especially `README.md` when present.
6. Keep reusable instructions generic. Do not bake private employer, manager, strategy, compensation, or personal-performance details into the skill.
7. Maintain naming consistency across time. Use lightweight context to normalize likely recognition mistakes for coworkers, projects, teams, companies, tools, and recurring concepts, but mark uncertain matches instead of guessing.
8. Separate work evidence from social, gossip, life, emotion, and environment context. Non-work context may inform advice only when clearly labeled and evidence-bound.
9. Goal-relative comments are optional and evidence-based. Provide them only after cleaned-note approval and final daily report generation, and never infer performance status, manager expectations, promotion probability, or private facts not in evidence.

## Trigger interpretation

Treat these as requests for this skill:

- write a daily report from raw notes
- organize my raw data / raw notes
- turn these notes into a worklog
- summarize today's fragmented notes
- prepare weekly/monthly/review material from daily logs
- similar requests in another language

If the request includes pasted notes and asks for a final daily report, still run Phase 1 first and stop for approval.

## Phase 0: Intake and raw backup

1. Determine the target date from the user message or current date. If ambiguous, use the date stated in the notes; otherwise ask one concise question.
2. Look for lightweight context that can improve consistency. Prefer approved daily/final notes, then explicit glossary-like context if present; use raw notes only as weak supporting evidence. Use context only for likely corrections; do not invent new entities. Raw-only or weak matches must be marked uncertain unless repeated or strong.
3. If the repo has `raw/YYYY-MM/`, save new pasted raw text there before cleaning:
   - Use `raw/YYYY-MM/YYYY-MM-DD.md`.
   - If the file does not exist, create it with the exact raw text plus minimal date/source heading.
   - If the file exists, append the new raw text as a new raw input section unless it is clearly duplicate content.
   - Never rewrite existing raw sections for style.
4. If no repo raw convention exists, keep the raw text in the chat context and explain that no raw file was written.

## Phase 1: Cleaned-note review draft

Create a cleaned draft for user review. This draft should be rough, semi-structured, and still close to the source. Its main job is correction and supplementation, not polish.

Cleaning rules:

- Preserve original intent and chronology.
- Use rough semi-structured sections or bullets so the user can quickly scan and correct the draft.
- Prefer these review lanes when relevant: work/process evidence; communication/collaboration context; non-work/social/environment context; uncertain items; consistency corrections.
- Keep the draft slightly unfinished: do not make it sound like a polished daily report, final conclusion, or performance-review narrative.
- Split long streams into coherent paragraphs or bullets.
- Move late-mentioned details back near the related earlier point when the relationship is clear. Example: if the user describes a bug fix, then later remembers the initial hypothesis, place that hypothesis near the bug-fix process instead of leaving it at the end.
- If the relationship is not clear, keep the detail in uncertain items or open questions instead of forcing a connection.
- Group scattered mentions of the same task, person, blocker, decision, or next step together, while preserving enough ordering to show how the thought evolved.
- Preserve process evidence: initial thought, changed approach, attempts, communication, blockers, rework, decisions, and open questions when present.
- Remove filler, repeated starts, and obvious spoken-language clutter.
- Correct likely recognition or wording mistakes only when context makes the correction likely.
- Normalize likely misrecognized names of people, projects, teams, companies, tools, and recurring concepts using lightweight context. Prefer approved daily/final notes over raw notes; raw-only matches are weak evidence.
- Mark uncertain corrections instead of silently changing meaning.
- Keep work and non-work notes, but classify them clearly.
- Separate factual work progress from interpretation, emotion, social context, environment signals, and future plans.
- Do not over-compress; the cleaned draft is still source material for human review, not the final report.

After producing the cleaned draft, stop and ask for explicit approval or edits.

Accept approval phrases such as: `approved`, `use this version`, `looks good`, `proceed`, `go ahead`, or clear equivalents in the user's language. User edits alone do not imply approval; after edits, present the revised cleaned draft and wait again unless the user also says to proceed.

## Phase 2: Final output after approval

Only after explicit approval, generate the requested final artifact.

For daily worklogs, follow the repository's existing daily-report convention. If no convention exists, use this compact structure:

- Date
- Main focus
- Completed work
- Communication / collaboration
- Decisions and reasoning
- Problems, blockers, and fixes
- Tomorrow / next steps
- Review-worthy material
- Optional goal-relative comment

For weekly/monthly/review material, aggregate from approved daily content and preserve evidence boundaries.

For non-work notes, include them only in clearly labeled social, environment, reflection, life, idea, or context sections unless the user asks for a purely professional report. Do not mix them into professional work sections by default.

Goal-relative comment rules:

- Use this goal source priority: explicit user-stated goal in the current request; repository/reporting convention; prior approved goal context if clearly available; otherwise omit the goal-relative comment or label `Goal: not provided` and give only generic evidence-based advice if useful.
- Generate goal-relative comments only after cleaned-note approval and final daily report generation.
- Separate evidence from interpretation: include evidence observed today, assessment, risks/gaps, and suggested next action.
- Do not infer performance status, manager expectations, promotion probability, or private facts not supported by the approved notes.
- Non-work/social/environment context may inform advice only when evidence-bound and clearly labeled.

Automation boundary:

- Daily reports and goal-relative comments may be generated after cleaned-note approval.
- Weekly, monthly, and performance-review material should be generated from approved daily reports when possible.
- Do not silently publish, overwrite, or treat unreviewed raw notes as final evidence.
- If the user asks for fully automatic daily/weekly generation, explain that this skill is review-first by design and ask for explicit approval before final writes.

## File and staging rules

- `raw/` stores source evidence.
- `daily/` stores approved daily reports.
- `weekly/`, `monthly/`, and review/performance folders consume approved daily material.
- Do not use `review/` as a transient cleaned-note staging area unless the repository explicitly defines that usage.
- Prefer showing cleaned-note drafts in chat. If persistence is requested, use a clearly named temporary/review-draft path that cannot be confused with final review material.

## Encoding safety

For Chinese or other non-ASCII content:

- Avoid shell `echo` or redirection for writing user text.
- Prefer `apply_patch` or explicit UTF-8 file writes.
- After writing, read the file back as UTF-8 and check for replacement characters, excessive question marks, or mojibake.
- Preserve Markdown LF line endings when possible.

## Verification checklist

Before claiming completion:

- Raw input was preserved or the lack of raw storage was explained.
- Cleaned draft was shown before any final report write.
- Final report was written only after explicit approval.
- Existing raw notes were not overwritten or beautified.
- Final output follows repo conventions or clearly states the fallback template used.
- Uncertain name/project/company matches were not silently normalized.
- Non-work, social, gossip, and environment context were separated or intentionally included according to user intent.
- Goal-relative comments were omitted when no goal was available, or clearly labeled as `Goal: not provided`.
- Any comment/advice was evidence-bound and separated from factual report content.
- Non-ASCII writes were checked for encoding corruption.
