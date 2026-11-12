# trial-review

[한국어](README.md) | [English](README.en.md)

> A Claude skill that ranks several proposed changes by a mock vote of 5 jurors, so you can decide which to apply first.

For the introduction, how it works and the judging criteria, see [trial-review-introduction](https://github.com/PROMISE282/trial-review-introduction). This repository contains only the plugin files.

## What it does

- Evaluates proposed fixes, changes or policies pasted into the conversation in a trial format and outputs a ranking table by approval ratio.
- The presiding judge is the PM, and the jury is a fixed set of 5 depending on the type of issue.

| Issue type | 5 jurors |
| --- | --- |
| Screen / copy | PM, UX, FE, QA, general user |
| Server / DB / API / infrastructure | PM, BE, security, QA, operations |
| Policy / planning | PM, finance, operations, CS, general user |

## Limits

| Item | This plugin | Pro |
| --- | --- | --- |
| Jurors | Fixed at 5 | Up to 8 per agenda, with selectable job roles and target users |
| Legal jurisdiction | No legal role (only flags "legal review needed") | Korea by default; adds jurisdictions when signals are present |
| Evaluation | Round 1 only (before applying) | Round 1 + round 2 after applying |
| Input | Text pasted into the conversation only | Includes reading code repositories and files |
| Local changes | Does not read, create or modify files | Temporary application in a working copy; applied after approval |
| Agenda count | 5 per run | Summary format; handles 25 or more |

> These limits are set by the skill instructions (`SKILL.md`). They do not technically block Claude Code's tool permissions, so to reliably block tool use, also use Claude Code's permission settings.

## Installation

### Claude Code (CLI)

```
/plugin marketplace add PROMISE282/trial-review
/plugin install trial-review@promise282-trial-review
```

### Claude Desktop

In the plugin screen of the Claude Code tab, add `PROMISE282/trial-review` as a marketplace, then install `trial-review`.

> The Pro edition has a different name, `trial-review-pro`, so installing both does not cause invocation conflicts.

### skills CLI (Claude Code, Codex, Cursor, etc.)

You can also install just the skill with the CLI from [skills.sh](https://skills.sh).

```
npx skills add PROMISE282/trial-review
```

Only the skill folder (`SKILL.md`, `references/`) is copied, and plugin commands such as `/trial-review:trial-review` are not created. Saying something like "judge this in trial format" invokes it automatically through its description.

## Usage

Paste the agendas into the conversation and say "judge this in trial format," "rank the priorities by jury vote," or "rank by approval ratio" (in Korean, or in English: "trial review", "jury vote"). To call it directly, type `/trial-review:trial-review`.

If you give a file path or repository link, it does not open it and asks you to paste the agenda content instead.

## Limitations

- This is a **mock vote** in which one model imitates job-role perspectives; the samples are not independent. It is not a real human vote or statistical evidence.
- It does not provide legal opinions and is not legal advice.
- Detecting technical defects is the job of code review and CI.
