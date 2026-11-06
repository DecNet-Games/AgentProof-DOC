---
layout: default
title: Editions — Standard vs Studio
nav_order: 18
description: "One codebase, two listings. Standard is the journal, receipts, review and rollback core. Studio adds checkpoints, conflict detection, the approval gate and the code-watch engine."
---

# Editions — Standard vs Studio
{: .no_toc }

1. TOC
{:toc}

---

One codebase, two listings. If you start on Standard, Studio is the same window with the Studio section present; Standard never shows locked-feature panels — the Studio section is simply absent from the Standard build.

## Standard

- **L1 Change Journal** — append-only journal, baselines, sessions, reload-safe.
- **L2 Receipts** — Editor Watch + File Watch; read-back verdicts Verified / No change / Applied with issues; persistence check; console correlation.
- **L3 Session Review + audit log export** — JSON + plain-language Markdown summary.
- **L4 Rollback** — per-burst and per-session, with a complete rollback report.
- The **Guided Trial** sample is included.
- **21 automated EditMode tests** (NUnit) for the Standard surface.

## Studio — adds

- **L5 Session checkpoints** — a checkpoint pins a journal position and captures tracked state; the checkpoint restore action restores the captured `Packages/manifest.json` snapshot through a guided restore. (Rollback of agent edits is the journal rollback — checkpoints do not rewind scenes or assets. See [Checkpoints]({{ site.baseurl }}/docs/checkpoints/).)
- **Conflict detection** — over the journal, engine-level: contested targets reported with both sessions' changes in journal order. v1.0.0 renders no conflict view. (See [Conflict Detection]({{ site.baseurl }}/docs/conflict-detection/).)
- **L6 Approval gate** — a policy for destructive Editor operations (asset deletion, moves out of the project, manifest writes, Build Settings scene-list changes) — Allow or Deny, every decision journalled. (See [Approval Gate]({{ site.baseurl }}/docs/approval-gate/).)
- **L7 Code-watch engine** — four checks on agent script diffs. The engine ships and is fixture-verified; in v1.0.0 its findings are not surfaced in the window or attached to receipts. (See [Code-Watch]({{ site.baseurl }}/docs/code-watch/).)
- **32 automated EditMode tests** (NUnit) across the full Studio surface.

## Verification record (both editions)

G-FINAL GO: Studio 32/32 and Standard 21/21 EditMode tests green on **Unity 6** and **2022.3 LTS**. Editor verification was performed on **Windows**. macOS is not claimed — see [What v1 Is Not]({{ site.baseurl }}/docs/what-v1-is-not/).
