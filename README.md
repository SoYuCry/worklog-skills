# WorkLog Daily Report Skill

English | [????](README.zh.md)

A Codex skill for turning messy raw text notes into reviewed daily worklogs, weekly/monthly reporting material, and performance-review evidence.

## The problem

Most useful work records do not start as polished documents.

They start as fragmented notes:

- ?I fixed that bug in the afternoon? wait, also talked to someone about data access.?
- ?This idea might matter later, but I do not know where to put it.?
- ?I should write a weekly report, but everything is scattered across chat, memory, and random notes.?

Raw notes are valuable, but they are hard to use:

- They are messy and hard to reread.
- They mix work progress, emotions, ideas, meetings, and next steps.
- They are too fragmented to become a report directly.
- Writing a proper daily report from scratch takes too much time.
- If you wait until Friday or month-end, you forget the evidence.

This skill is designed for the tiny moments when you actually have energy to record things:

- five minutes on the subway,
- waiting for food delivery,
- walking back from a meeting,
- before leaving the office,
- right after a useful conversation.

Just dump the raw text. The skill helps you turn it into something usable.

## Who is this for?

This is useful for:

- interns and new hires during probation,
- professionals who need daily/weekly/monthly reports,
- people preparing promotion or performance-review material,
- researchers, engineers, quants, analysts, and product people with fragmented daily progress,
- anyone who thinks better by ?rambling first, organizing later.?

## The solution

The workflow is intentionally simple:

```text
raw text notes
  -> cleaned review draft
  -> user approval
  -> daily worklog / weekly material / review evidence
```

The skill does **not** transcribe audio.

Use whatever input method you like. For Chinese users, a practical workflow is:

1. Use Doubao Input Method, system dictation, or another speech-to-text tool.
2. Speak for a few minutes.
3. Paste the raw text into Codex.
4. Let this skill clean the notes into a review draft.
5. Review once.
6. Approve it.
7. Generate the final daily report or reporting material.

## Why the review step matters

This skill does not jump directly from raw notes to a polished report.

It first creates a **cleaned review draft**.

That draft is still close to the source, but more readable:

- long streams are split into paragraphs,
- repeated filler is removed,
- related items are grouped,
- likely speech-recognition mistakes are corrected,
- names of people, projects, teams, and companies are kept consistent with prior context,
- uncertain corrections are marked instead of silently rewritten,
- work and non-work notes are separated.

Only after explicit user approval does the skill write the final report.

This protects the most important thing: **your meaning should not be changed by the summarizer.**

## Design principles

### 1. Raw notes are evidence

Raw notes should be backed up and treated as source material. The skill should never beautify raw notes in place.

### 2. Clean first, report second

A daily report should be based on reviewed notes, not on an unchecked model interpretation of messy input.

### 3. Preserve meaning before polish

The skill may improve readability, but it must not invent facts, dates, metrics, decisions, blockers, or outcomes.

### 4. Fit workplace scenarios

The default output is designed for professional worklogs:

- what was done,
- what was learned,
- who was involved,
- what decisions were made,
- what blockers appeared,
- what should happen next,
- what evidence may be useful for weekly/monthly/performance review.

### 5. Keep non-work notes, but classify them

Real raw notes often contain life, mood, ideas, or reflection. The skill can keep them, but should label them clearly instead of mixing them into a professional report.

### 6. Maintain consistency across time

Worklogs are cumulative. If a coworker, project, company, tool, or recurring concept has appeared before, the skill should use that existing context to correct likely recognition mistakes and keep naming consistent.

For example, if prior notes mention `Alice Zhang` and the new raw text contains a likely misheard variant, the cleaned draft may normalize it to `Alice Zhang` and optionally record the correction. When the match is uncertain, the skill should flag it instead of guessing.

This is a skill responsibility at the review stage, not uncontrolled automation. The skill should help maintain a lightweight glossary from existing notes, but final reports should still wait for user approval.

## Automation boundary

This skill can help generate daily, weekly, monthly, and review material, but it should not silently publish or overwrite final reports.

Recommended responsibility split:

- The skill cleans raw notes and drafts reports.
- The user approves cleaned notes and important final outputs.
- Daily reports can be generated after approval.
- Weekly/monthly/review reports should be generated from approved daily material, not directly from unreviewed raw notes.

## Install

Copy the skill folder into a Codex skills directory:

```text
worklog-daily-report/
```

Project-local installation:

```text
.codex/skills/worklog-daily-report/
```

User-global installation on Windows:

```text
%USERPROFILE%/.codex/skills/worklog-daily-report/
```

Then ask Codex something like:

```text
Organize these raw notes into a daily worklog.
```

The skill should first return a cleaned review draft and wait for approval.

## Repository layout

```text
worklog-daily-report/
  SKILL.md
  references/
    templates.md
  agents/
    openai.yaml
```

## Open-source safety

The skill itself is generic. Do not publish private worklog data with it.

Avoid committing:

- employer names,
- manager names,
- confidential project details,
- compensation,
- trading/strategy details,
- personal performance records.

## License

MIT
