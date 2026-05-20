---
name: worklog-daily-report
description: Clean user-provided raw text notes for review before generating daily worklog reports, weekly/monthly/reporting material, or reflection summaries. Use when the user asks to write a daily report, organize raw notes, turn pasted notes into a worklog, or summarize fragmented notes for review. Always preserve raw meaning, require cleaned-note approval before writing final reports, and never treat speech-to-text as part of the skill.
---

# WorkLog Daily Report

Use this skill when the user provides pasted raw text notes and wants a daily worklog, weekly/monthly/reporting material, or a reviewed reflection summary.

The skill does **not** transcribe audio. Users are responsible for converting speech to text with their own tools and pasting the raw text.

## Core contract

1. Preserve source meaning before polish. Do not invent facts, dates, metrics, names, decisions, blockers, or outcomes.
2. Back up raw text when working in a repository with a `raw/` convention. Existing raw files are source evidence and must not be beautified or rewritten.
3. Cleaned notes are an intermediate review artifact. Show them to the user first.
4. Do not write or update final reports until the user explicitly approves the cleaned notes.
5. Keep final outputs aligned to the repository's existing conventions, especially `README.md` when present.
6. Keep reusable instructions generic. Do not bake private employer, manager, strategy, compensation, or personal-performance details into the skill.
7. Maintain naming consistency across time. Use existing repository context to normalize likely recognition mistakes for coworkers, projects, teams, companies, tools, and recurring concepts, but mark uncertain matches instead of guessing.

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
2. Look for lightweight context that can improve consistency, such as prior daily/raw files, a glossary, or recurring names in existing notes. Use it only for likely corrections; do not invent new entities.
3. If the repo has `raw/YYYY-MM/`, save new pasted raw text there before cleaning:
   - Use `raw/YYYY-MM/YYYY-MM-DD.md`.
   - If the file does not exist, create it with the exact raw text plus minimal date/source heading.
   - If the file exists, append the new raw text as a new raw input section unless it is clearly duplicate content.
   - Never rewrite existing raw sections for style.
4. If no repo raw convention exists, keep the raw text in the chat context and explain that no raw file was written.

## Phase 1: Cleaned-note review draft

Create a cleaned draft for user review. This draft should be readable but still close to the source.

Cleaning rules:

- Preserve original intent and chronology.
- Split long streams into coherent paragraphs or bullets.
- Remove filler, repeated starts, and obvious spoken-language clutter.
- Correct likely recognition or wording mistakes only when context makes the correction likely.
- Normalize likely misrecognized names of people, projects, teams, companies, tools, and recurring concepts using existing repo context.
- Mark uncertain corrections instead of silently changing meaning.
- Keep work and non-work notes, but classify them clearly.
- Separate factual work progress from interpretation, emotion, and future plans.
- Do not over-compress; the cleaned draft is still source material, not the final report.

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
- Optional state and advice

For weekly/monthly/review material, aggregate from approved daily content and preserve evidence boundaries.

For non-work notes, include them only in clearly labeled reflection, life, idea, or context sections unless the user asks for a purely professional report.

Automation boundary:

- Daily reports may be generated after cleaned-note approval.
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
- Non-work notes were either separated or intentionally included according to user intent.
- Non-ASCII writes were checked for encoding corruption.
