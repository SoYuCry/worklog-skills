# Worklog Skills

English | [简体中文](README.zh.md)

**Remember what you actually did before the details disappear.**

Worklog Skills is a Codex skill for turning messy daily work notes into reviewable work memory, daily logs, and evidence you can reuse for updates, weekly reports, papers, reviews, and performance summaries.

## The Problems

Work reporting usually fails before the writing starts.

1. **You forget what you did.** By the end of the day, Friday, or month-end, your work is scattered across memory, chats, meetings, commits, notes, and half-written thoughts.
2. **The process details disappear.** The first idea, failed attempts, why the plan changed, who gave input, and how the solution evolved are often gone by the time you write the report.
3. **The final result looks smaller than the real effort.** Research, debugging, communication, rework, judgment, and tradeoffs are invisible unless you captured them when they happened.

This skill is designed for small recording moments: five minutes on the subway, waiting for food delivery, walking back from a meeting, a quick recap before leaving work, or right after a useful conversation.

## Solution

Dump rough notes first. Let the skill organize them into a human-reviewable draft before any final report is written.

| Problem | What the skill does |
| --- | --- |
| “I do not remember what I did.” | Preserves raw notes and groups fragmented work into reviewable work/process evidence. |
| “I remembered a detail later.” | Moves late-mentioned details near the related task when the relationship is clear. |
| “Names and projects are inconsistent.” | Aligns recurring names, projects, companies, and tools using lightweight prior context. |
| “The model might guess wrong.” | Marks uncertain corrections instead of silently rewriting them. |
| “Some context is social or environmental.” | Separates work evidence from social, gossip, life, emotion, and environment context. |
| “I need this for probation or review.” | Adds an optional goal-relative comment after the approved daily report. |

The workflow is intentionally review-first:

```text
raw notes
  -> rough cleaned review draft
  -> explicit user approval
  -> daily worklog / weekly material / review evidence
  -> optional goal-relative comment
```

The skill does **not** transcribe audio. Use any speech-to-text or note-taking tool you like, then paste the raw text into Codex.

## The Five Features in Detail

### 1. Lightweight term alignment

The skill can normalize likely misrecognized coworker names, project names, company names, tools, and recurring concepts.

Context priority:

```text
approved daily/final notes
  > explicit glossary-like context
  > raw notes as weak supporting evidence
```

Weak or raw-only matches are marked as uncertain. The skill does not require or promise a persistent glossary system.

### 2. Rough semi-structured review drafts

The cleaned draft is not a polished report. It is a rough review artifact that helps you check whether the meaning is right.

Typical lanes:

- Work / process evidence
- Communication / collaboration context
- Non-work / social / environment context
- Uncertain items
- Consistency corrections

### 3. Uncertainty marking

If a correction, name match, date, cause, or conclusion is uncertain, it is labeled for review instead of hidden inside fluent prose.

### 4. Work and non-work context separation

Real notes include work, social context, mood, gossip, environment signals, and personal reflection. The skill keeps these separated so professional reports stay clean, while useful context can still inform advice.

### 5. Goal-relative comments

After an approved daily report, the skill can add a short comment for goals such as probation conversion, quarterly review, annual review, promotion preparation, lab meetings, or paper progress.

The comment separates:

- evidence observed today,
- assessment,
- risk / gap,
- suggested next action.

It must not infer promotion probability, manager expectations, or private facts not supported by approved notes. If no goal is available, the comment is omitted or marked `Goal: not provided`.

## Voice input tip

This skill does **not** transcribe audio. For Chinese voice-to-text, [Doubao Input Method](https://shurufa.doubao.com/) is a comfortable option to dictate a quick five-minute note and paste the text into Codex. It supports mobile and macOS; Windows is not supported yet.

## Install

### Recommended: project-local Codex skill

This skill is usually most useful inside one worklog or research repository, so the recommended setup is project-local:

```text
<your-repo>/.codex/skills/worklog-daily-report/
```

From the target repository, install with the Codex Skill Installer:

```bash
python3 ~/.codex/skills/.system/skill-installer/scripts/install-skill-from-github.py --repo SoYuCry/worklog-skills --path skills/worklog-daily-report --dest .codex/skills
```

Windows PowerShell:

```powershell
python "$env:USERPROFILE\.codex\skills\.system\skill-installer\scripts\install-skill-from-github.py" --repo SoYuCry/worklog-skills --path skills/worklog-daily-report --dest .codex/skills
```

Restart Codex after installation.

### Plugin marketplace, if available

If your agent supports plugin marketplaces:

```text
/plugin marketplace add SoYuCry/worklog-skills
/plugin install worklog-skills@worklog-skills
```

### Global Codex install

If you want the skill available across projects, ask Codex:

```text
Install the worklog-daily-report skill from SoYuCry/worklog-skills
```

Or run:

```bash
python3 ~/.codex/skills/.system/skill-installer/scripts/install-skill-from-github.py --repo SoYuCry/worklog-skills --path skills/worklog-daily-report
```

### Manual install

```bash
git clone https://github.com/SoYuCry/worklog-skills.git /tmp/worklog-skills
mkdir -p .codex/skills/worklog-daily-report
cp -r /tmp/worklog-skills/skills/worklog-daily-report/* .codex/skills/worklog-daily-report/
```

After installation, ask:

```text
Organize these raw notes into a daily worklog. My goal is getting promoted and paid more.
```

The skill should first return a cleaned review draft and wait for approval.

## Repository Layout

```text
.claude-plugin/
  marketplace.json
  plugin.json
.codex-plugin/
  plugin.json
skills/
  worklog-daily-report/
    SKILL.md
    references/
      templates.md
```

## Open-source Safety

The skill is generic. Do not publish private worklog data with it.

Avoid committing employer names, manager/coworker names, confidential project details, compensation, trading/strategy details, or personal performance records.

## License

MIT
