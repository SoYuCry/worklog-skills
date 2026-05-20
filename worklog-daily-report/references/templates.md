# Templates

Use these templates as compact guides. Prefer repository-specific templates from `README.md` when present.

## Cleaned-note review draft

```markdown
# Cleaned Raw Notes Review: YYYY-MM-DD

## Work / process evidence

- What happened: ...
- Initial thought / approach: ...
- Iteration / attempts: ...
- Blockers / rework / decisions: ...
- Next step: ...

## Communication / collaboration context

- ...

## Non-work / social / environment context

- ...

## Uncertain items

- `raw phrase` -> `possible correction`: reason / uncertainty / needs user confirmation

## Consistency corrections

- `raw phrase` -> `canonical name`: matched from approved notes / glossary-like context / repeated context
```

Rules:

- Keep this close to the source and slightly rough.
- Do not turn it into a polished report, final conclusion, or performance-review narrative.
- Move late-remembered details near the related task when the relationship is clear; otherwise keep them under uncertain items.
- Include uncertain corrections only when relevant.
- Use consistency corrections for likely name/project/company/tool recognition errors. Prefer approved daily/final notes over raw notes; mark weak matches as uncertain.
- Keep social, gossip, life, emotion, and environment context labeled separately from work evidence.
- Ask the user to approve or edit this draft before writing final outputs.

## Daily worklog fallback

```markdown
# Daily Worklog: YYYY-MM-DD

## Main focus

- ...

## Completed work

- ...

## Communication / collaboration

- ...

## Decisions and reasoning

- ...

## Problems, blockers, and fixes

- ...

## Tomorrow / next steps

- ...

## Review-worthy material

- ...

## Goal-relative comment

Goal: probation / quarterly review / annual report / promotion / not provided

### Evidence observed today

- ...

### Assessment

- ...

### Risk / gap

- ...

### Suggested next action

- ...
```

Use `Goal-relative comment` only after cleaned-note approval and final report generation. If no goal is available, omit it or write `Goal: not provided` with only generic evidence-based advice. Keep evidence, assessment, risks, and advice separate. Do not infer performance status, manager expectations, promotion probability, or private facts not supported by the approved notes.

## Weekly/monthly/reporting extraction

```markdown
## Outcomes

- ...

## Evidence

- Date: ...
- Source daily file: ...

## Risks / blockers

- ...

## Next reporting angle

- ...
```
