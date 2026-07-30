---
title: The one column in SHOW ENGINES that explains why InnoDB won
platform: linkedin
status: idea
phoenix_source: PHX-S01 · labs/S01-Architecture/PHX-S01-M1-Lab.md · SHOW ENGINES
published_url:
date:
---

## The hook / insight

Run `SHOW ENGINES;` on any MySQL server and read one column top to bottom: **Transactions.**
Every enabled engine says NO — MEMORY, MyISAM, CSV, ARCHIVE, BLACKHOLE — *except* InnoDB.
That single column is basically the whole reason InnoDB became the default.

## Why it's non-obvious / worth a post

Most people "know" InnoDB is the default but can't say *why* in one sentence. This reframes
a boring diagnostic command into a story about an engineering trade-off. It's concrete
(a real command, real output) and it teaches judgment, not trivia.

## The DBA payoff (the part that attracts clients)

If a client's legacy app has a MyISAM table, that table silently gave up three things:
transactions, row-level locking (MyISAM locks the *whole table* on write → the classic
"app freezes under load"), and crash safety. Diagnosing a MyISAM-induced freeze and
migrating to InnoDB is a real, billable freelance scenario.

## Formats this could become

- LinkedIn post (screenshot of the Transactions column + the 3-things payoff)
- Hashnode section inside a "MySQL storage engines" article
- YouTube: 3-minute "read SHOW ENGINES like a DBA"

## Status notes

Raw idea. Learned during PHX-S01 on 2026-07-30. Not yet drafted.
