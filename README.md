# need-reader-skill

Three Codex/Cursor skills for managing inline `need:` / `need：` notes in Markdown.

## Skills

| Skill | Purpose |
| --- | --- |
| `need-reader` | Expand inline `need:` / `need：` prompts into red Need cards. |
| `need-reader-clear` | Turn completed Need cards from red to green with `done:` / `done：`, or clear a parent/current/child group with `donest:` / `donest：`. |
| `need-reader-check` | List remaining red Need cards with file and line jump targets. |

## Layout

```text
SKILL.md
skills/
  need-reader/
    SKILL.md
    Relationship.md
  need-reader-check/
    SKILL.md
    Relationship.md
  need-reader-clear/
    SKILL.md
    Relationship.md
```

The root `SKILL.md` is kept as a compatibility entry for the original `need-reader` skill. The full three-skill workflow lives under `skills/`.

## Install

Install the repository, or copy the three folders under `skills/` into your local skills directory:

```bash
mkdir -p ~/.codex/skills
cp -R skills/need-reader ~/.codex/skills/
cp -R skills/need-reader-check ~/.codex/skills/
cp -R skills/need-reader-clear ~/.codex/skills/
```

## Workflow

1. Run `need-reader` to expand new inline `need:` / `need：` notes.
2. Add `done:` / `done：` inside one completed Need card, or `donest:` / `donest：` when the whole parent/current/child Need group is complete, then run `need-reader-clear`.
3. Run `need-reader-check` to list remaining red Need cards.

## License

MIT
