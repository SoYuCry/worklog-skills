# Repository Guidelines

## Project Structure & Module Organization

This repository packages a Codex skill for converting raw work notes into reviewed daily reports. The distributable skill lives in `worklog-daily-report/`:

- `worklog-daily-report/SKILL.md` contains the main workflow instructions and user-facing behavior.
- `worklog-daily-report/agents/openai.yaml` defines agent metadata/configuration.
- `worklog-daily-report/references/templates.md` stores reusable report templates.
- `README.md` and `README.zh.md` document the project for English and Chinese readers.

Keep new skill assets inside `worklog-daily-report/`. Use `references/` for static guidance, examples, and templates; add new agent config files under `agents/` only when they are actually used.

## Build, Test, and Development Commands

There is no build system or package manifest in this repository. Validate changes with lightweight local checks:

- `Get-ChildItem -Recurse worklog-daily-report` — inspect the skill package layout.
- `Get-Content worklog-daily-report/SKILL.md` — review the main instruction file.
- `git diff --check` — detect trailing whitespace and patch formatting issues.

If future tooling is added, document the exact root-level command here, such as `npm test`, `pnpm lint`, or `python -m pytest`.

## Coding Style & Naming Conventions

Write Markdown in short, scannable sections with descriptive headings. Preserve the existing professional, instructional tone and avoid inventing product capabilities. Use kebab-case for directories and Markdown assets, for example `worklog-daily-report` and `templates.md`. Keep YAML files small, two-space indented, and limited to configuration data.

## Testing Guidelines

No automated tests are present yet. For content changes, manually verify that the skill still follows its review-first workflow: raw notes become a cleaned draft before any final report. When adding tests later, place fixtures under `worklog-daily-report/references/fixtures/` or `tests/fixtures/`, and cover English, Chinese, mixed-language, empty-input, and malformed-note cases.

## Commit & Pull Request Guidelines

Recent commits use concise, imperative subjects such as `Restore Chinese README encoding` and `Restore WorkLog daily report skill project`. Follow that style: start with a verb, name the affected area, and keep the subject under about 72 characters. Pull requests should include a summary, files changed, validation performed, linked issue if any, and before/after examples for output or template changes.

## Security & Configuration Tips

Do not commit private worklogs, company names, personal notes, or generated reports containing sensitive data. Keep examples anonymized and clearly synthetic.
