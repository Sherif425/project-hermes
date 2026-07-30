# Source Map — the Phoenix → Hermes dependency ledger

Every published content piece records the Phoenix sprint/chapter/lab it was distilled
from. This is the traceability that lets you find and update downstream content when
Phoenix corrects something upstream. It is the content-project equivalent of Phoenix's
own Sprint ↔ Phase table.

## How to use

- When a piece is **published**, add a row.
- `Phoenix source` should be specific: sprint ID + the exact concept, ideally a commit or
  file path (e.g. `PHX-S01 · labs/S01-Architecture/PHX-S01-M1-Lab.md · SHOW ENGINES`).
- If Phoenix later revises that source, scan this table for affected pieces.

## Ledger

| Date | Piece | Platform | Phoenix source | Live URL |
|------|-------|----------|----------------|----------|
| _(none published yet)_ | | | | |

## Frontmatter convention

Every draft and published file carries this at the top so provenance travels with the
piece even outside this table:

```yaml
---
title:
platform:        # linkedin | hashnode | youtube | book
status:          # idea | draft | published
phoenix_source:  # e.g. PHX-S01 · SHOW ENGINES transactions column
published_url:
date:
---
```
