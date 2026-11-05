---
layout: default
title: Watch Modes
nav_order: 8
description: "Editor Watch covers changes made through the Editor — the path MCP bridges use. File Watch covers terminal agents editing files on disk. Both are always on after Setup."
---

# Watch Modes
{: .no_toc }

1. TOC
{:toc}

---

AgentProof observes your project through two complementary channels. After Setup, **both are always on** — there is nothing to arm per session.

## Editor Watch

Covers changes made **through the Editor itself** — Editor application updates, selection changes, and the undo/redo pipeline. This is the path every MCP bridge uses: when an agent drives Unity through CoplayDev MCP for Unity, the Unity CLI, or a scripted Editor driver, the edits land through the Editor and Editor Watch captures them.

## File Watch

Covers **terminal agents rewriting files on disk** — scripts, materials and other text assets modified by an external editor or command-line tool. Changes are detected on refresh (via Unity's AssetPostprocessor and directory polling) and journalled with a diff summary.

## Works with the bridge you already use

AgentProof is an overlay, not a bridge: it ships no MCP server and replaces nothing you run. Setup checks for installed bridges (such as CoplayDev MCP for Unity or the official CLI tools) and Watch Status reports what was detected on its bridge line — in a project with no bridge installed, that line honestly reads **"Bridge: None detected"**, and File Watch still covers terminal agents on its own.

## Watch Status

The Home window's Watch Status section shows the per-mode state, the detected bridge, and the journal location, live. It is the first place to look if an edit you expected is missing from the Review: if neither mode could have seen it (for example, a file changed while the Editor was closed), it was never journalled — AgentProof only reports what it observed.

![Watch Status after Setup: both modes live, bridge line, journal location]({{ "/assets/images/watch-status.png" | relative_url }})
