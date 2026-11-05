---
layout: default
title: Changelog
nav_order: 22
description: "AgentProof release history, from the shipped package changelog."
---

# Changelog
{: .no_toc }

All notable changes to the AgentProof package are documented here. The format is based on Keep a Changelog, and the project adheres to Semantic Versioning. This page reproduces the shipped package's `CHANGELOG.md`.

---

## [1.0.0] — 2026-11-04

### Added

- Change Journal core: JSONL-backed monotonic sequence journaling under `Library/AgentProof/Journal`.
- Baseline manager: automated scene object serialization and file-level snapshot captures.
- Receipt Engine: independent read-back verification producing `VERIFIED`, `NO CHANGE`, and `APPLIED WITH ISSUES` verdicts.
- Watch systems: dual-mode monitoring via Editor Watch (Editor API and undo pipeline) and File Watch (disk modifications).
- Rollback Engine: reverse-chronological burst and full-session rollback with detailed restoration reports.
- Session Review: UI displaying burst hierarchies, before-and-after property deltas, and audit export (JSON and Markdown).
- Guided Trial: interactive 5-edit practice session showcasing read-back verification and one-click rollback.
- Studio Edition features:
  - Checkpoint manager with snapshot restore and multi-session conflict detection.
  - Approval gate for protecting critical asset paths and project manifests against destructive Editor actions.
  - Code-watch engine verifying renamed fields, fake-null patterns, API version indexing, and event unsubscription pairs.
- Target parity: verified support for Unity 2022.3 LTS and Unity 6 across Windows and macOS.

> **Documentation note (this site, not the shipped file):** two lines above are stated more broadly than the shipped build supports, and this site corrects them wherever they matter: the checkpoint manager's "snapshot restore" restores the captured `Packages/manifest.json` snapshot (see [Checkpoints]({{ site.baseurl }}/docs/checkpoints/)), and "across Windows and macOS" is a build target — v1.0.0's verification was performed on Windows, and macOS is unverified in our own testing (see [What v1 Is Not]({{ site.baseurl }}/docs/what-v1-is-not/)).
