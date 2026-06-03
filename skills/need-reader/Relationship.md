# Need Workflow Relationship

## Shared Idea

Need workflow has three separate lifecycle actions:

| Skill | Role | Marker |
| --- | --- | --- |
| `need-reader` | Expand inline questions into Need cards | `need:` / `need：` |
| `need-reader-clear` | Mark completed Need cards green | `done:` / `done：` / `donest:` / `donest：` |
| `need-reader-check` | List remaining red Need cards with jump targets | `🔴 Need-xx` |

## Design Decision

Keep the three skills independent. Do not embed `need-reader-clear` or `need-reader-check` into `need-reader` execution.

Reason:

- Creating a Need, clearing a Need, and checking remaining Needs are different user intents.
- Independent invocation keeps each skill short and lowers accidental edit risk.
- `done:` / `done：` is local; `donest:` / `donest：` clears the whole parent/current/child Need group.
- Relationship notes live here rather than in `SKILL.md` so routine skill loading stays small.

## Recommended Order

1. Run `need-reader` to expand new `need:` notes.
2. Run `need-reader-clear` after adding `done:` / `done：` or `donest:` / `donest：` markers inside completed Need cards.
3. Run `need-reader-check` to find unresolved red Need cards and jump back to them.

## Cross-Skill Contract

- `need-reader` creates red Need cards by default.
- `need-reader-clear` changes Need title balls from `🔴` to `🟢`; `done:` / `done：` clears one card, and `donest:` / `donest：` clears the parent/current/child group.
- `need-reader-check` reports only remaining `🔴 Need-xx` cards; it does not edit content.
- Non-Need red balls are out of scope for all status operations.
