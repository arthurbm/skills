# skills

Agent skills by Arthur Brito Medeiros, in the [Agent Skills](https://skills.sh) format: each skill is a folder with a `SKILL.md` that agents such as Claude Code, Codex and Cursor load on demand.

## Install

One skill:

```bash
npx skills add arthurbm/skills --skill <name>
```

Every skill in the repository:

```bash
npx skills add arthurbm/skills
```

## Skills

| Skill | What it does |
|---|---|
| [`study-notebook`](skills/study-notebook/SKILL.md) | Teaches a topic over many sessions, publishing Lessons and References in a Notebook site with interactive practice. |

## Layout

Each skill lives in `skills/<name>/`. A skill derived from someone else's work carries a `CREDITS.md` with what came from where and the upstream license.

## License

[MIT](LICENSE).
