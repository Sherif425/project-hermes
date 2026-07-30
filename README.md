# Project Hermes

> The public-facing content pipeline that carries Project Phoenix learning out into the
> world as published, monetizable content — without ever polluting Phoenix itself.

## What this is

Project Hermes is a **content and audience-building project**. Its raw material is the
understanding developed in **Project Phoenix** (the MySQL DBA engineering handbook). Its
output is public content: LinkedIn posts, Hashnode articles, YouTube videos, and
eventually a book — assembled to build reputation, attract freelance DBA clients, and
create products that can be sold.

## The core design rule: one-directional dependency

```text
Project Phoenix  ──(source of truth)──▶  Project Hermes
     (learning)                              (content)
```

- **Phoenix never depends on Hermes.** Phoenix does not know this project exists.
- **Hermes depends on Phoenix.** Every content piece references the specific Phoenix
  sprint, chapter, or lab it was distilled from (see `source-map.md`).
- **Never copy Phoenix content into Hermes.** Reference it. Copying creates two versions
  that drift — the exact problem Phoenix's v1 documents suffered from.

This is the same discipline as a healthy software dependency: the library (Phoenix)
never imports the app (Hermes).

## Structure

```text
project-hermes/
├── README.md            # this file
├── STRATEGY.md          # sequencing: leads first, audience next, product last
├── source-map.md        # content piece → Phoenix origin (the dependency ledger)
├── pipeline/
│   ├── ideas/           # raw captures — "this would make good content"
│   ├── drafts/          # in progress
│   └── published/       # shipped, with links + dates
├── linkedin/            # platform-specific final assets
├── hashnode/
├── youtube/             # scripts, thumbnails, descriptions
└── assets/              # shared images and diagrams
```

The **pipeline stages matter more than the platform folders**, because the real workflow
is *one insight → many formats*: an idea becomes a LinkedIn post, then a blog section,
then eventually a book chapter. Organize by stage first, platform second.

## Workflow (one insight, many formats)

1. A Phoenix sprint ends → it drops at least one entry in `pipeline/ideas/`
   (this is a Phoenix Definition-of-Done item, the only link between the projects).
2. Promising ideas move to `pipeline/drafts/` and are written up.
3. Published pieces move to `pipeline/published/` with their live URL and date,
   and get an entry in `source-map.md`.

## Relationship to Project Atlas

Project Hermes lives under **Project Atlas** (the framework for structured learning
initiatives), since content-from-learning is exactly such an initiative. It is a sibling
of Phoenix under Atlas, not a third independent ecosystem.

## License

All rights reserved (see LICENSE). Hermes is the commercial layer; Phoenix may open in
the future, but Hermes's polished, monetizable output stays closed.
