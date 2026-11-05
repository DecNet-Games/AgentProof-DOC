---
layout: default
title: The Home Window
nav_order: 5
description: "AgentProof Home is one Editor window: status strip, Welcome and Setup, Watch Status, Guided Trial, Session Review, the Studio section, and Settings."
---

# The Home Window
{: .no_toc }

1. TOC
{:toc}

---

Everything in AgentProof lives in one window: **Tools → Decnet Games → AgentProof → AgentProof Home**. Session Review is also a menu shortcut into the same window — there are no orphan windows. The Standard build shows the shared sections; in the Studio build the same window carries a Studio section (checkpoints, the approval gate, code-watch heading). Standard never shows locked-feature panels — the Studio section is simply absent.

## Header and status strip

The strip reads the watch state at a glance: whether AgentProof is watching, how many sessions have been recorded, and the last activity — for example, after the trial: *"Watching. Sessions recorded: 3. Last activity: Assets/TrialCrate.prefab (Recorded)."*

## Welcome and Setup

On first run the welcome block offers four quick actions, including **Run Setup / Verify Install**. One exactness note: the shipped window has **no setup-report panel** — Setup's result feeds the Watch Status bridge line ("Setup verified. Watching. Bridge: None detected." in a project with no bridge installed), and the post-setup page shows Watch Status live. There is no separate report screen to look for.

## Watch Status

Per-mode state for Editor Watch and File Watch, the bridge detected (if any), and the journal location. See [Watch Modes]({{ site.baseurl }}/docs/watch-modes/).

![Watch Status, complete, after Setup]({{ "/assets/images/watch-status.png" | relative_url }})

## Guided Trial

Start the practice session, watch its receipts land in the Review, and roll it back. See the [Quick Start]({{ site.baseurl }}/docs/quick-start/).

## Session Review

Sessions, bursts and readable before/after property rows, with receipt amendments and rollbacks in the same timeline, plus **Export Audit Log**. Receipts render as inline rows — the shipped Review has **no separate receipt-detail view**; the before/after row is the detail. See [Session Review]({{ site.baseurl }}/docs/session-review/).

![A three-session Review timeline in the Studio build]({{ "/assets/images/studio-review.png" | relative_url }})

## Studio section (Studio build only)

Checkpoints (shown as a **count**, not a per-checkpoint list — that is the shipped UI), the Approval Gate with its policy text, and the Code-Watch heading. See [Checkpoints]({{ site.baseurl }}/docs/checkpoints/), [Approval Gate]({{ site.baseurl }}/docs/approval-gate/) and [Code-Watch]({{ site.baseurl }}/docs/code-watch/) — the last two pages state their scope exactly, including what v1.0.0 does not surface.

![The Studio section: gate policy, the checkpoint count, and the Code-Watch heading]({{ "/assets/images/studio-section.png" | relative_url }})

## Settings

Re-run Setup, **Reset AgentProof Data**, retention and audit settings, and — in the Studio build — the **Auto Checkpoints** toggle (automatic checkpoints at each session start can be disabled). See [Settings]({{ site.baseurl }}/docs/settings/).
