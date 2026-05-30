# need-reader-skill

Agent skill for processing inline `need:` prompts in Markdown documents.

When you write technical notes with embedded questions like `need: 解释成大白话`, this skill tells the agent to:

- Extract each `need:` and answer it in a structured **Need card**
- Keep top-level needs as standalone cards at their original position
- Nest follow-up needs as sub-cards inside parent Need blocks
- Append a **Need 处理清单** checklist when done

## Install

### Cursor / Codex (recommended)

```bash
npx skills add wuluoluoda/need-reader-skill
```

### Manual

Copy `SKILL.md` into your skills directory:

```bash
# Cursor
mkdir -p ~/.cursor/skills/need-reader
cp SKILL.md ~/.cursor/skills/need-reader/

# Codex
mkdir -p ~/.codex/skills/need-reader
cp SKILL.md ~/.codex/skills/need-reader/
```

## Usage

Attach the skill or invoke it in chat:

```text
/need-reader @your-document.md
```

Or mention it when a Markdown file contains `need:` markers you want processed.

## Card format

Top-level:

```md
---

> **🔴 Need-01 | Title**
>
> Answer in plain language.
>
> - Point 1
> - Point 2
```

Nested (inside an existing Need block):

```md
>>> **🔴 Need-01.1 | 追问：follow-up question**
>>>
>>> - Point 1
>>> - Point 2
```

## License

MIT
