# NOTES.md Format

`NOTES.md` lives at the workspace root. It holds the learner profile, the state between sessions, and the history behind both. The profile is the learner's voice: on format, it outranks this skill's defaults and [LESSON-STANDARDS.md](./LESSON-STANDARDS.md).

## Template

```md
# Notes

## Learner profile

- Language: {the language of the Notebook and the conversation}
- Reading context: {where and on what the learner reads the Notebook, e.g. "phone, in short breaks"; "laptop, at a desk"}
- Session: {typical length, and how to treat a stated stop time}
- Format: {preferences that tighten or relax the Lesson standards, e.g. "one goal per Lesson, next step always explicit"}
- Known ground: {domains the learner is fluent in, the source of analogies}
- Practice: {how the learner wants to practise, e.g. "writes the core of the project; the agent writes the repetitive parts and reviews"}

## Where we left off

> {date}: {last Lesson published, what comes next, loose ends}

- Notebook: {URL, how access is protected, how to deploy when the Notebook's README does not say}

## Format history

- **{date}:** {what the learner asked for or reacted to} → {the profile line or rule it produced}

## Detours for later

| Date | Detour | Resume at |
|---|---|---|
| {date} | {the side question} | {the Lesson or milestone where it fits} |

## Gaps

- {Information the teaching needs and does not have yet, e.g. a source chapter the learner still has to provide.}
```

## Rules

- **Write profile lines as teaching needs** ("short blocks, one goal per Lesson"). The learner decides whether the reason behind a need goes in too.
- **Every profile change gets a Format history line**, so a later session can tell a deliberate rule from a passing remark, and revise it knowingly.
- **"Where we left off" is one dated paragraph, replaced each session.** The history of past sessions lives in git and in the learning records.
- **Close detours in place**: when one is taken up, replace its "Resume at" with "resumed on {date}: {where it went}".
- **Keep it under two screens.** Settled decisions move to the learner's project or to a learning record.
