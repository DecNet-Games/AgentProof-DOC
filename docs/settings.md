---
layout: default
title: Settings
nav_order: 17
description: "Re-run Setup, reset AgentProof's data, retention and audit settings — and, in Studio, the Auto Checkpoints toggle."
---

# Settings
{: .no_toc }

1. TOC
{:toc}

---

The Settings section sits at the bottom of AgentProof Home. (It is documented here from the shipped source; the section's contents below are the shipped controls.)

## Shared settings

- **Re-run Setup** — re-runs the one-click Setup / Verify Install pass: journal and storage initialisation, version validation, bridge check, baseline capture.
- **Reset AgentProof Data** — the product's own reset path for its stored data (journal, snapshots, checkpoints, product state). This is also the path used to stage a genuine first-run state. Reset is destructive to the audit record — export the audit log first if you need it.
- **Retention and audit settings** — how much history the journal, snapshots and audit data keep.

## Studio only

- **Auto Checkpoints** — checkpoints are taken automatically at each session start; this toggle disables that behaviour. Manual checkpoints from the Studio section are unaffected. See [Checkpoints]({{ site.baseurl }}/docs/checkpoints/).
