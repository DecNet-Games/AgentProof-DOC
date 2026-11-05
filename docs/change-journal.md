---
layout: default
title: The Change Journal
nav_order: 6
description: "The append-only, domain-reload-safe journal underneath everything AgentProof does: sessions, bursts, baselines and snapshots, stored locally in your project."
---

# The Change Journal
{: .no_toc }

1. TOC
{:toc}

---

The journal is the record everything else reads from. Every session, burst, verdict, rollback and (in Studio) gate decision is written to an **append-only journal that survives domain reloads** — a change notified twice across a reload is journalled once.

## Where it lives

Journal and snapshot storage are initialised by Setup under **`Library/AgentProof/`** in your project (the changelog describes the journal as a JSONL-backed, monotonic-sequence journal under `Library/AgentProof/Journal`). Watch Status in the Home window shows the journal location for the current project. Nothing leaves your machine: no account, no cloud, no telemetry.

## What gets recorded

- **Sessions** — a contiguous run of agent activity, from the first observed edit to the burst that closes it.
- **Bursts** — a contiguous group of changes inside a session; receipts are issued per burst, and rollback works per burst or per session.
- **Baselines and snapshots** — the before-state a receipt is read back against, and the snapshot copies that let rollback recreate a deleted asset (the trial's deleted TrialCrate comes back "from snapshot copy").
- **Amendments and rollbacks** — rollbacks are themselves journal events, so the Review timeline shows them in place rather than erasing history. One consequence worth knowing: a checkpoint restore (Studio) is journal-silent with respect to rewind — the journal is **not** rewound by a restore; entries continue to grow across it (see [Checkpoints]({{ site.baseurl }}/docs/checkpoints/)).

## Why append-only matters

An audit log you can edit is a story, not evidence. Because the journal only grows, the Session Review can show an agent session, its receipts, its rollback, and a later session's work on the same target in one honest timeline — and the exported audit log (JSON + Markdown) is a faithful copy of it, suitable for attaching to a bug report or a client email.

See [Session Review]({{ site.baseurl }}/docs/session-review/) and [Audit Log Export]({{ site.baseurl }}/docs/audit-log-export/).
