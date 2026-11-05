---
layout: default
title: Conflict Detection (Studio)
nav_order: 14
description: "When two sessions contest the same target, the shipped conflict-detection engine reports it in journal order. Engine-level in v1.0.0 — there is no conflict-view window."
---

# Conflict Detection (Studio)
{: .no_toc }

> **Scope, stated exactly.** Conflict detection in v1.0.0 is **engine-level**. The shipped build's Home window contains **no conflict view** — nothing renders contested targets on a screen, and there is no in-window "roll back either session from the same screen" surface. What ships and is verified is the detection engine over the journal. Rolling back a session is done with the [journal rollback]({{ site.baseurl }}/docs/rollback/), per burst or per session.
{: .block-tip }

1. TOC
{:toc}

---

## The problem it addresses

Two agents in one project — or one agent in two overlapping sessions — can touch the same object or file. Session A sets a value; session B, working from the older state, sets it again. Neither session's receipts are wrong individually; the loss is in the overlap.

## What the engine does

The shipped `ConflictEngine` reads the journal and detects **contested targets**: the same object or file changed by overlapping sessions. For each contested target it reports **both sessions' changes in journal order**, so the overwrite order — who changed what, after whom — is a matter of record.

## Verified behaviour

Run over a real three-session journal from the verification session, the engine returned **4 real conflicts**, contested by three sessions, over exactly the targets the trial sessions had all touched:

- TrialTurret
- TrialSettings.asset
- TrialBarrel.mat
- Assets/TrialCrate.prefab

## What v1.0.0 does not do with it

- No window, panel or view renders the conflicts — the engine's output is not a screen in the shipped build.
- There is no per-conflict rollback button; use session/burst rollback from the Review.
- Detection is over the journal: it can only contest targets the journal recorded.
