---
title: Query vs Sleep — reading a MySQL processlist like a DBA
platform: linkedin
status: idea
phoenix_source: PHX-S01 · labs/S01-Architecture · SHOW PROCESSLIST + connection lifecycle
published_url:
date:
---

## The hook / insight

`SHOW PROCESSLIST` is the command you'll run most in a DBA career. The whole skill is
scanning one column — **Command** — and asking: is this connection *working* (`Query`) or
just *sitting there* (`Sleep`)? Watch a session flip from Query to Sleep after its
statement finishes and the connection lifecycle suddenly makes sense.

## Why it's non-obvious / worth a post

Beginners think a connection is either "on" or "off." The Query→Sleep distinction is the
missing middle: a connection can be open, idle, and holding resources while doing nothing.
That's the root of a huge class of production problems (idle-in-transaction, pool
exhaustion, timeout disconnects).

## The DBA payoff (the part that attracts clients)

Idle connections that outlive `wait_timeout` get closed by the server; a connection pool
then hands a dead connection to the next request → intermittent "server has gone away"
errors that only happen in low-traffic hours. This is the production scenario in the S01
lab. Being able to explain and fix it is direct client value.

## Formats this could become

- LinkedIn post (two-terminal SLEEP demo, before/after processlist)
- Hashnode: "Understanding MySQL connections: Query, Sleep, and the timeout trap"
- YouTube: live two-terminal demo — most tutorials never show this

## Status notes

Raw idea. Learned during PHX-S01 on 2026-07-30. Pending the two-terminal SLEEP test.
