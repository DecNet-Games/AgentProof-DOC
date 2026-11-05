---
layout: default
title: Checkpoints (Studio)
nav_order: 13
description: "A checkpoint pins a journal position and captures tracked state. Its restore action restores the captured Packages/manifest.json snapshot — exactly that, stated plainly."
---

# Checkpoints (Studio)
{: .no_toc }

> **Scope, stated exactly.** A checkpoint **pins a journal position and captures the tracked state** at that point. The checkpoint **restore action restores the captured `Packages/manifest.json` snapshot** — through a guided restore that states what will change before it runs. A checkpoint restore does **not** rewind scenes, assets or settings, and it does not rewind the journal. Rolling back an agent's edits is a different mechanism: the [journal rollback]({{ site.baseurl }}/docs/rollback/), which restores recorded values, removes created objects and recreates deleted ones from snapshot, per burst or per session.
{: .block-tip }

1. TOC
{:toc}

---

## Taking a checkpoint

Checkpoints are taken **manually** from the Studio section of AgentProof Home, and **automatically at each session start** (the automatic ones can be disabled in [Settings]({{ site.baseurl }}/docs/settings/)).

The shipped window shows checkpoints as a **count**, not a per-checkpoint list. In the verification session the count pair across two consecutive frames is the take's fingerprint: "Total checkpoints: 6", then — after a manual take (checkpoint `cp_20261105_004327_02b1cb`, pinned at journal sequence 11) — "Total checkpoints: 7".

![The Studio section after a checkpoint take: the count reads 7]({{ "/assets/images/checkpoint-taken.png" | relative_url }})

## Restoring a checkpoint

The restore is **guided**: it states what will change before it runs, and what it changes is the manifest. Restoring returns `Packages/manifest.json` to the snapshot captured with the checkpoint — the deliberate, isolated way to undo a manifest state, kept separate from session rollback, which reports manifest changes as *Not restored* by design (see [Rollback]({{ site.baseurl }}/docs/rollback/)).

What restore provably does, from the verification run: it returned **ok**, and the journal was **not** rewound across it (entries grew 11 → 16). It changes no window state — which is why this site's capture pack uses one honestly-disclosed post-restore frame for the restored state: there is no visible "rewind" to photograph, because no rewind of scenes or assets happens.

## Checkpoints vs. rollback — which one do I want?

| You want to… | Use |
|---|---|
| Undo an agent session's edits — values, created objects, a deletion | [Session rollback]({{ site.baseurl }}/docs/rollback/) |
| Undo one burst inside a session | [Burst rollback]({{ site.baseurl }}/docs/rollback/) |
| Return `Packages/manifest.json` to a known earlier snapshot | Checkpoint restore |
| Mark "here is a known-good point" before a complex agent task | Take a checkpoint (its journal pin is the marker; pair it with rollback for the edits themselves) |
