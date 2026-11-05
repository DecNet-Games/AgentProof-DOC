---
layout: default
title: Troubleshooting
nav_order: 21
description: "An edit is missing from the Review, a verdict surprises you, a restore did less than you expected — what each of those actually means in the shipped build."
---

# Troubleshooting
{: .no_toc }

1. TOC
{:toc}

---

## An agent edit never appeared in the Review

AgentProof only reports what it observed. Check, in order:

1. **Was Setup run in this project?** Both watch modes arm at Setup. The status strip should read "Watching."
2. **Which path did the edit take?** Editor-mediated edits are Editor Watch's; files changed on disk are File Watch's, detected **on refresh** — if the Editor hasn't refreshed since the change, the journal entry lands at the next refresh.
3. **Was the Editor open?** A file changed while the Editor was closed was never journalled and cannot appear retroactively.

## A receipt reads NO CHANGE but the agent insists it wrote the value

That is the product working as designed. The read-back equals the baseline: either the write never landed, or the target's own validation clamped it back (the Guided Trial's fourth edit is exactly this — see [Quick Start]({{ site.baseurl }}/docs/quick-start/)). Believe the receipt: it is read from Unity's serialized state, not from the agent's report.

## A receipt reads APPLIED WITH ISSUES

The change landed, but one of these fired during its burst: new console errors, a persistence re-read failure after save/reload, or a prefab-override conflict. Open the Console for the burst's window of time; the receipt's row shows the before/after values either way. (In v1.0.0 a code-watch finding is never the cause — see [Code-Watch]({{ site.baseurl }}/docs/code-watch/).)

## Rollback restored everything except the manifest

By design. Manifest changes are journalled and reported **Not restored** in the rollback report — never silently skipped. In Studio, restore the manifest separately via a checkpoint restore. See [Rollback]({{ site.baseurl }}/docs/rollback/).

## I restored a checkpoint and my scene didn't change

Also by design, and the documentation says so wherever checkpoints are described: the checkpoint restore action restores **only** the captured `Packages/manifest.json` snapshot. It does not rewind scenes, assets, settings or the journal. To undo edits, roll back the session. See [Checkpoints]({{ site.baseurl }}/docs/checkpoints/).

## I can't find the conflict view / code-watch findings / setup report

None of those are window surfaces in v1.0.0:

- Conflicts: engine-level detection over the journal — [Conflict Detection]({{ site.baseurl }}/docs/conflict-detection/).
- Code-watch findings: the engine ships, unwired from the live pipeline — [Code-Watch]({{ site.baseurl }}/docs/code-watch/).
- Setup report: Setup's result feeds the **Watch Status bridge line**; there is no report panel.

## The Guided Trial scene is an empty grid

As shipped: the trial scene is logic-only (TrialTurret + TrialCrate data objects, no renderers, no camera). The practice session still runs end-to-end — the driver works from journal and baseline data — and its import copies the sample without `.meta` files, so the scene's script links do not resolve as live components in your project. Both facts are documented on [The Guided Trial]({{ site.baseurl }}/docs/guided-trial/) page.

## A second trial run gave different receipts

Practice sessions are state-dependent: the driver starts from the project's current journal/baseline state. A run on a post-rollback scene legitimately produces a different receipt set. The canonical reference run is the one in the [Quick Start]({{ site.baseurl }}/docs/quick-start/).

Still stuck? [Support]({{ site.baseurl }}/docs/support/).
