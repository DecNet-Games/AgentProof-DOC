---
layout: default
title: Installation
nav_order: 3
description: "Install AgentProof from the Unity Asset Store and run the one-click setup. AgentProof is sold exclusively through the Unity Asset Store."
---

# Installation
{: .no_toc }

## Asset Store only
{: .no_toc .text-delta }

> **AgentProof is sold exclusively through the Unity Asset Store** (publisher: Decnet Games). It is not distributed for free on GitHub or anywhere else — this site is the product's documentation, not a download. If you obtained a copy of AgentProof from any other source, it is not an official copy.

1. TOC
{:toc}

---

## Requirements

- **Unity 2022.3 LTS** or **Unity 6**.
- An Editor on **Windows**. Editor verification for v1.0.0 was performed on Windows; macOS is unverified in our own testing (see [What v1 Is Not]({{ site.baseurl }}/docs/what-v1-is-not/)). The Linux Editor is not supported in v1.
- **No third-party dependencies, no account, no network at run time.** AgentProof is editor-only — zero runtime components, zero player-build footprint — and all of its data lives locally in your project machine.

## Install from the Asset Store

1. Purchase AgentProof (or AgentProof Studio) on the Unity Asset Store under the Unity ID you use for your projects.
2. In the Unity Editor, open **Window → Package Manager**, switch the Packages filter to **My Assets**, find **AgentProof**, and choose **Download**, then **Import**.
3. Import the full package. It includes the editor tooling, the Guided Trial sample, the test suites (21 EditMode tests for Standard, 32 across the Studio surface), and the documentation set — the same quick-start, reference and "what v1 is not" documents that ship in the package's `Documentation~` folder.

## Run Setup (once)

1. Open the Home window: **Tools → Decnet Games → AgentProof → AgentProof Home**.
2. On first open the window shows the genuine first-run state: an empty journal, the welcome block with four quick actions, and the status strip reading **"Watching. No agent sessions recorded yet."**
3. Click **Run Setup / Verify Install**. Setup initialises the change journal and snapshot storage under `Library/AgentProof/`, validates your Unity version (2022.3 LTS or Unity 6), checks for installed agent bridges (such as CoplayDev MCP for Unity or the official CLI tools), captures the initial baseline of open scene assets, and updates the Watch Status — the bridge line reports what was detected (in our own verification run: "Setup verified. Watching. Bridge: None detected.", because no bridge was installed in that project).

![AgentProof Home on first run: welcome block, quick actions and Watch Status]({{ "/assets/images/welcome-first-run.png" | relative_url }})

From here, both watch modes are on. The fastest way to see the whole product work is the [Quick Start]({{ site.baseurl }}/docs/quick-start/) — the Guided Trial takes about ten minutes.
