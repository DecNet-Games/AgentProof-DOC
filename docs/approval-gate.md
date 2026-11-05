---
layout: default
title: Approval Gate (Studio)
nav_order: 15
description: "A policy gate over destructive Editor operations: asset deletion, moves out of the project, manifest writes, Build Settings scene-list changes. Allow or Deny — every decision journalled."
---

# Approval Gate (Studio)
{: .no_toc }

1. TOC
{:toc}

---

Studio's gate watches the **destructive operations that pass through the Editor**, under a policy you configure:

- **Gated operations:** asset deletion, asset moves out of the project, `Packages/manifest.json` writes, and Build Settings scene-list changes. (From the verification session's logged policy state: `gatedOps=[delete_asset, move_asset, manifest_write, build_settings_write]`.)
- **Policy:** protected path prefixes (the verification project's policy state showed `protectedPaths=[Assets/Protected]`) and protected asset kinds.

## How a gated operation flows

1. An operation on the gated list is attempted through the Editor.
2. The gate raises an **approval prompt** naming the operation, the target, and the active session.
3. **Deny** blocks it, and the denial is journalled. **Allow** lets it proceed, and the approval is journalled.
4. The window's gate section keeps a **decisions list** ("Recent decisions: 0" in a project where nothing has been gated yet).

![The Approval Gate section in the Studio window: policy text, protected paths, gated operations, decisions list]({{ "/assets/images/gate-section.png" | relative_url }})

## The boundary, in the window's own words

The gate section states its limit plainly, verbatim:

> "The gate blocks deletions and other listed operations made through the Editor. Files an agent deletes directly on disk are detected on refresh and can be restored from the journal; they are not blocked."

That is the whole boundary: **Editor-mediated** operations are gated; direct on-disk deletions are **detected and recoverable** via File Watch and the journal, not blocked. AgentProof does not pretend otherwise, in the window or here.

## A note on the prompt pair

The gate **section** above is captured and verified. The live approval prompt itself — a gated delete under a protected path, photographed mid-decision — is a manual capture by design: automated harnesses deliberately never trigger a real gated delete. Treat the prompt as documented behaviour (it names the operation, the target and the active session; Deny/Allow journal the decision), with the section and its policy state as the shipped surface.
