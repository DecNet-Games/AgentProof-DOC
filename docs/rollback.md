---
layout: default
title: Rollback
nav_order: 11
description: "Roll back a single burst or an entire agent session, in reverse journal order — and a report that lists every entry as Restored or Not restored, with the reason."
---

# Rollback
{: .no_toc }

1. TOC
{:toc}

---

Rollback is how a bad agent session stops being a bad day. It works from the journal: what the journal recorded is what rollback can restore — created objects are removed, deleted objects are recreated from snapshot, values are restored to baseline.

## Two scopes

- **Roll Back Burst** — reverts a single contiguous burst of edits to its pre-burst baseline.
- **Roll Back Session** — reverts all bursts in an agent session, in reverse journal (chronological) order, across domain reloads.

## The rollback report

Every rollback produces a report that lists **every entry as Restored or Not restored, with a plain-language reason. Nothing is silently skipped.** In the Guided Trial's verified run, the report listed all five entries as Restored:

- TrialCrate — *Restored from snapshot copy*
- TrialTurret (×2), TrialBarrel.mat, TrialSettings.asset — *Restored property to baseline value*

![The rollback report: all five entries Restored, with the post-rollback Review below it]({{ "/assets/images/rollback-report.png" | relative_url }})

## The manifest rule — stated exactly

`Packages/manifest.json` is the one deliberate exception. Manifest changes are journalled, but session rollback reports them as **Not restored** rather than silently skipping them — restoring a manifest mid-operation would trigger unexpected package-resolution cycles. In **Studio**, restoring a captured manifest snapshot is available as its own deliberate action: the checkpoint restore (see [Checkpoints]({{ site.baseurl }}/docs/checkpoints/)), which states what will change before it runs.

## Rollback is itself journalled

A rollback is a journal event, not an erasure: the Review shows the original session and its rollback in one timeline, and the rollback burst produces its own receipts. That is what makes "nothing an agent does is irreversible" compatible with "nothing an agent does is invisible" — both are read off the same append-only record.
