---
layout: home
title: Home
nav_order: 1
description: "AgentProof reads every AI agent edit in Unity back from Unity itself and issues a verdict — verified, no change, or applied with issues — with a journal and one-click session rollback."
permalink: /
---

# AgentProof
{: .fs-9 }

Every agent edit, read back from Unity itself — **verified, no change, or applied with issues.**
{: .fs-6 .fw-300 }

[Get started]({{ site.baseurl }}/docs/getting-started/){: .btn .btn-primary .fs-5 .mb-4 .mb-md-0 .mr-2 }
[Buy on the Unity Asset Store](https://assetstore.unity.com/publishers/118262){: .btn .fs-5 .mb-4 .mb-md-0 }

![The Session Review after the Guided Trial: verdict counts and the receipt rows with before and after values]({{ site.baseurl }}/assets/images/receipts-live.png)

---

## Your agent says the edit worked. Unity is the one who knows.

You drive Unity with an AI coding agent — Claude Code, Codex, Cursor, Antigravity — through a free bridge, or by letting a terminal agent edit project files directly. And you have felt the era's defining failure at least once: the agent reported success, and Unity disagreed. A value that was never set. A change that silently reverted. A deletion nobody recorded. The agent reports what it asked for. **AgentProof asks Unity what it holds now.**

AgentProof is an overlay, not a bridge. It ships no MCP server, replaces nothing you run, and needs no account. It observes the Editor and your project files, journals every change, and issues a receipt for each burst of agent activity — computed by reading the target state back from Unity, never from what the agent said it did.

- **Read-back verdicts** — every burst gets exactly one: **Verified**, **No change**, or **Applied with issues**, with the before/after values on the receipt.
- **A permanent journal** — sessions, bursts and verdicts in an append-only, reload-safe audit log you can export as JSON plus a plain-language Markdown summary.
- **One-click rollback** — roll back a burst or a whole session; the report lists every entry as **Restored** or **Not restored**, with the reason.

![Receipts, then the rollback report, then the trial scene — the catch-and-rollback loop]({{ site.baseurl }}/assets/images/catch-and-rollback.gif)

<video controls preload="metadata" style="max-width:100%" src="{{ site.baseurl }}/assets/videos/agentproof-overview.mp4"></video>

## See it work in ten minutes

The package ships a **Guided Trial**: a practice agent session of five edits — one of them a silent edit that never lands — ending in a one-click session rollback. In the verified capture run, the trial's receipts were complete **22.7 seconds** after the window opened, and the rollback report was on screen at **39.0 seconds**: the turret speed edit (7.5 → 12) read **VERIFIED**, the boss health edit (400 → 40) read **VERIFIED**, the clamped range edit (10 → 10) read **NO CHANGE**, and all five rollback entries read **Restored**.

## Two editions, one codebase

**Standard ($79)** is the journal, receipts, review and rollback core. **Studio ($149)** adds checkpoints with a guided manifest restore, conflict detection, the approval gate, and the code-watch engine — each documented here in exactly the terms the shipped build supports. See [Editions]({{ site.baseurl }}/docs/editions/).

> Editor verification for v1.0.0 was performed on Windows, on Unity 2022.3 LTS and Unity 6. macOS is **not** claimed — see [What v1 Is Not]({{ site.baseurl }}/docs/what-v1-is-not/).
