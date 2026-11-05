---
layout: default
title: What v1 Is Not
nav_order: 19
description: "AgentProof v1's explicit boundaries: not a bridge, not an agent, no compile certification — and the exact scopes of checkpoint restore, conflict detection and code-watch."
---

# What v1 Is Not
{: .no_toc }

To ensure reliability, predictable performance, and focused capability, AgentProof v1 establishes strict engineering boundaries. This page is the honest list — including three scopes that are narrower than a quick feature list might suggest, stated exactly.

1. TOC
{:toc}

---

## Not a bridge, not an agent

- **Not an MCP bridge:** AgentProof contains no MCP server, no WebSocket server, and no agent connection protocol. You bring your own bridge (such as CoplayDev MCP for Unity) or run terminal agents editing files directly.
- **Not an agent:** no chat interface, no LLM prompts, no code generation, no autonomous task orchestration. It is strictly an independent audit, verification, and rollback layer.

## No certification

- **No compile-verification certification:** AgentProof does not certify that your game compiles or that a build is green. Console state is recorded per burst as read from Unity, without speculative claims about runtime behaviour.
- **No Play Mode test probes in v1:** scripted Play Mode assertions and input simulations are excluded from the v1 core.
- **Not a version control replacement:** it does not branch, merge, or push to remotes. It operates alongside Git without modifying your Git configuration.
- **No telemetry or cloud accounts:** all journals, snapshots, and settings are stored locally on your machine. No data leaves your workstation.

## The three scopes, stated exactly

- **Checkpoint restore is manifest-only (Studio).** A checkpoint pins a journal position and captures tracked state; the restore action restores the captured `Packages/manifest.json` snapshot through a guided restore. It does not return scenes, assets or settings to the checkpoint state, and it does not rewind the journal. Undoing edits is the journal rollback's job. In Standard, manifest changes are journalled and reported as **Not restored** by session rollback.
- **Conflict detection has no view (Studio).** The engine detects contested targets over the journal and reports both sessions' changes in journal order. v1.0.0 renders no conflict view in the window.
- **Code-watch findings reach no window surface (Studio).** The engine is shipped and fixture-verified, but it is not called by the live watch pipeline in v1.0.0: its findings are not attached to receipts, do not change verdicts, and are not listed in the Review. There is no one-click fix surface. It is four targeted diff checks — not a linter, not full-codebase static analysis — and it never silently modifies code.

## Platform honesty

- **No Linux Editor support in v1.**
- **macOS is unverified.** The product is built for the macOS Editor, but v1.0.0 was not verified on a Mac in our own testing — treat macOS as unverified until we publish a Mac verification pass. Editor verification for v1.0.0 was performed on Windows.

## Smaller shipped truths

- The window has **no setup-report panel** — Setup's result feeds the Watch Status bridge line.
- The Review has **no receipt-detail view** — receipts are inline rows.
- The Studio window shows checkpoints as a **count**, not a list.
- The **Guided Trial scene is logic-only** (no meshes, camera or light) and its import copies the sample **without `.meta` files**, so the imported scene's script links do not resolve as live components; the practice driver works from journal/baseline data. See [The Guided Trial]({{ site.baseurl }}/docs/guided-trial/).
