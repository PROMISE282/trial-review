# trial-review

[한국어](README.md) | [English](README.en.md)

> A Claude skill that ranks several proposed changes by a mock vote of job-role jurors, so you can decide which to apply first.

For the introduction, how it works and the judging criteria, see [trial-review-introduction](https://github.com/PROMISE282/trial-review-introduction). This repository contains only the plugin files.

Please send feedback through [GitHub Issues](https://github.com/PROMISE282/trial-review/issues) in this repository or by email to promise211217@gmail.com.

> **Notice about the user-evaluation period:** To collect user evaluations more smoothly, all features are currently unlocked with no restrictions. Once enough evaluations have been gathered and the plugin has been improved, an update that limits its capabilities may be released without advance notice.

## What it does

- Extracts proposed fixes, changes or policies from the conversation or from code repositories and files, evaluates them in a trial format, and outputs a ranking table by approval ratio.
- The presiding judge is the PM, and the jury has up to 8 jurors per agenda. Job roles and the target user are chosen to match the agenda's issues.
- It runs both the first round (before applying) and the second round (after applying). Temporary application for the second round is done in a working copy, and changes are applied only after approval.
- With many agendas it uses a summary format (including 25 or more).

| Issue type | Jurors |
| --- | --- |
| Code centered on screens and wording | PM, UX, FE, BE, QA, A11y, CS, Data |
| Server / DB / API / infrastructure | PM, BE, DBA, security, SRE, QA, CS, Data |
| Policy / planning | PM, sales, finance, legal, operations, CS, target user, Data |

## Installation

### Claude Code (CLI)

```
/plugin marketplace add PROMISE282/trial-review
/plugin install trial-review@promise282-trial-review
```

### Claude Desktop

In the plugin screen of the Claude Code tab, add `PROMISE282/trial-review` as a marketplace, then install `trial-review`.

### skills CLI (Claude Code, Codex, Cursor, etc.)

You can also install just the skill with the CLI from [skills.sh](https://skills.sh).

```
npx skills add PROMISE282/trial-review
```

Only the skill folder (`SKILL.md`, `references/`) is copied, and plugin commands such as `/trial-review:trial-review` are not created. Saying something like "judge this in trial format" invokes it automatically through its description.

## Usage

Paste the agendas into the conversation or point to files or a repository, and say "judge this in trial format," "rank the priorities by jury vote," or "rank by approval ratio" (in Korean, or in English: "trial review", "jury vote"). To call it directly, type `/trial-review:trial-review`.

## Limitations

- This is a **mock vote** in which one model imitates job-role perspectives; the samples are not independent. It is not a real human vote or statistical evidence.
- Legal opinions are not legal advice.
- Detecting technical defects is the job of code review and CI.
