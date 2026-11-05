---
layout: default
title: Quick Start
nav_order: 4
description: "The ten-minute path: run the Guided Trial, read the five receipts — including the NO CHANGE an agent would never tell you about — and roll the session back."
---

# Quick Start
{: .no_toc }

1. TOC
{:toc}

---

**Outcome:** review your first agent session receipts and roll back the changes within 10 minutes, using only the built-in home window and the Guided Trial. Timings below are from the verified capture run of this exact path: receipts complete **22.7 s** after the window opened; window-open → rollback report **39.0 s**.

## Step 1 — Open AgentProof Home

**Tools → Decnet Games → AgentProof → AgentProof Home.** On first open, the window shows the welcome block with four quick actions and the status strip reading **"Watching. No agent sessions recorded yet."**

## Step 2 — Run one-click Setup

Click **Run Setup / Verify Install**. Setup initialises the change journal and snapshot storage under `Library/AgentProof/`, validates your Unity version, checks for installed agent bridges, and captures the initial baseline of open scene assets.

## Step 3 — Start the Guided Trial

In the **Guided Trial** section, click **Start Practice Session**. The built-in practice driver executes five typical agent edits, simulating both direct Editor changes and file modifications. One honesty note before you run it: the trial scene is **logic-only** — it ships as data objects (a turret and a crate, no meshes, no camera), because the practice is about receipts and rollback, not visuals. The driver works from journal and baseline data, end to end.

## Step 4 — Read the receipts

Open the **Session Review**. In the verified run, the session produced five receipts, grouped in the window into burst rows:

| Edit | Read-back | Receipt |
|---|---|---|
| TrialTurret speed 7.5 → 12 | landed | **VERIFIED** |
| TrialSettings bossHealth 400 → 40 | landed | **VERIFIED** |
| TrialBarrel range 10 → 10 | clamped back by the script's own validation | **NO CHANGE** |
| TrialCrate prefab Exists → Deleted | landed, snapshot taken | **VERIFIED** |

The verdict header read **"Verified: 3 \| No Change: 1 \| Applied with issues: 0"**. The NO CHANGE row is the point of the product: the practice script's own validation silently clamped the value back, the agent-side edit "succeeded" — and the read-back receipt shows before equals after.

![The trial session's receipts: verdict counts and the four burst rows with before and after values]({{ "/assets/images/receipts-live.png" | relative_url }})

## Step 5 — Roll the session back

Click **Roll Back Session**. The rollback engine processes the session's entries in reverse journal order and produces a **Rollback Report**: in the verified run, all five entries read **Restored** — the deleted TrialCrate "Restored from snapshot copy", the turret, barrel and settings entries "Restored property to baseline value".

![The rollback report: every entry Restored, with the post-rollback Review below it]({{ "/assets/images/rollback-report.png" | relative_url }})

## Next steps

AgentProof is now watching your project. Edits made through CoplayDev MCP for Unity, the Unity CLI, or terminal agents modifying files on disk are journalled, verified on refresh, and reviewable at any time. Read [Receipts & Verdicts]({{ site.baseurl }}/docs/receipts-and-verdicts/) for exactly how each verdict is decided, and [Rollback]({{ site.baseurl }}/docs/rollback/) for the two rollback scopes.
