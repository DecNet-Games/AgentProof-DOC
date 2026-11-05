---
layout: default
title: FAQ
nav_order: 20
description: "Short answers: bridges, verdicts, rollback scope, what Studio really adds in v1.0.0, macOS, and where your data lives."
---

# FAQ
{: .no_toc }

1. TOC
{:toc}

---

## Does AgentProof replace my MCP bridge?

No. AgentProof ships no MCP server and connects to no agent. It observes the Editor and your project files, so it works with the bridge you already use — CoplayDev MCP for Unity, the Unity CLI — or with a terminal agent editing files directly (File Watch). Setup reports what it detected; with no bridge installed, the Watch Status bridge line reads "None detected" and everything else still works.

## How is a verdict decided?

By reading the state back from Unity, never from the agent's report: read-back value vs. baseline and target, console delta for the burst, and a persistence check after save/reload. **Verified** = landed clean. **No change** = the read-back equals the baseline (the edit did not land — e.g. it was clamped). **Applied with issues** = landed, but with new console errors, a failed persistence check, or a prefab-override conflict. See [Receipts & Verdicts]({{ site.baseurl }}/docs/receipts-and-verdicts/).

## Can rollback undo a deleted asset?

Yes — deletions are journalled with a snapshot, and rollback recreates the asset from the snapshot copy. The rollback report lists every entry as Restored or Not restored with the reason; nothing is silently skipped.

## Does rollback restore Packages/manifest.json?

No — deliberately. Session rollback journals manifest changes and reports them as **Not restored**, to avoid triggering package-resolution cycles mid-operation. In Studio, the checkpoint restore action restores a captured manifest snapshot as its own guided operation. See [Checkpoints]({{ site.baseurl }}/docs/checkpoints/).

## What does a checkpoint actually restore?

Exactly one thing: the captured `Packages/manifest.json` snapshot, through a guided restore that states what will change first. A checkpoint **pins a journal position and captures tracked state** — it does not rewind scenes, assets, settings, or the journal itself. Undoing edits is [rollback]({{ site.baseurl }}/docs/rollback/).

## Where is the conflict view?

There isn't one in v1.0.0. Studio's conflict detection is a verified engine over the journal — it reports contested targets with both sessions' changes in journal order — but the shipped window renders no conflict view. See [Conflict Detection]({{ site.baseurl }}/docs/conflict-detection/).

## Where do code-watch findings appear?

In v1.0.0, nowhere in the window. The code-watch engine ships and is verified against the product's own fixtures (six findings across the fixture set), but it is not wired into the live watch pipeline: findings are not attached to receipts and are not listed in the Review. See [Code-Watch]({{ site.baseurl }}/docs/code-watch/).

## Does it work on macOS?

Unverified. The product is built for the macOS Editor, but v1.0.0 was not verified on a Mac in our own testing — treat macOS as unverified until we publish a Mac verification pass. Editor verification was performed on Windows. Linux Editor is not supported in v1.

## Where does my data live?

In your project machine, under `Library/AgentProof/` — journals, baselines and snapshots. No account, no cloud, no telemetry; nothing leaves your workstation.

## Which Unity versions?

Unity 2022.3 LTS and Unity 6, verified on both: Standard 21/21 and Studio 32/32 EditMode tests green on each, plus the GUI capture verification on Unity 6. (The 2022.3 verification stands on the headless test record; the Unity 6 pass is the one photographed on this site.)
