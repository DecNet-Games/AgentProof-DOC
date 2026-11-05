---
layout: default
title: Receipts & Verdicts
nav_order: 7
description: "How AgentProof decides Verified, No change, or Applied with issues — by reading the state back from Unity, never from what the agent said it did."
---

# Receipts & Verdicts
{: .no_toc }

1. TOC
{:toc}

---

AgentProof never determines the outcome of an edit from agent claims or command return codes. For each burst of changes it **reads the serialized values directly back from Unity** — from engine state or the disk asset — compares them with the baseline and the requested target, correlates the console delta, and runs a **persistence check** after a save or reload. It then issues exactly one verdict:

| Verdict | Criteria | Meaning |
|---|---|---|
| **VERIFIED** | Read-back value equals the target requested value; no new console errors during the burst; persistence check passes | The change was applied cleanly and verified in Unity |
| **NO CHANGE** | Read-back value equals the original before-value despite a reported write | The change failed to land, or was clamped back to baseline by validation logic |
| **APPLIED WITH ISSUES** | The change landed, but something is wrong: new console errors during application, a persistence re-read failure, or a prefab-override conflict | Applied — with side effects you need to see |

## Reading a receipt

Each receipt carries the target, the **before value**, the **after (read-back) value**, the verdict, and the console correlation for its burst. Receipts render as **inline rows** in the Session Review — the shipped Review has no separate receipt-detail view; the row is the detail. The verdict header summarises the session: in the Guided Trial's verified run, **"Verdicts: Verified: 3 \| No Change: 1 \| Applied with issues: 0"** over five receipts grouped into four burst rows:

- **[VERIFIED]** TrialTurret speed 7.5 → 12
- **[VERIFIED]** TrialSettings.asset bossHealth 400 → 40
- **[NO CHANGE]** TrialBarrel.mat range 10 → 10 — the practice script's validation clamped the submitted value back; the agent-side write "succeeded", the read-back did not move
- **[VERIFIED]** Assets/TrialCrate.prefab Exists → Deleted, with a snapshot taken for recovery

![The receipt rows and verdict counts after the Guided Trial]({{ "/assets/images/receipts-live.png" | relative_url }})

## What a verdict is not

A verdict is a statement about **recorded state**, per burst — nothing more. AgentProof does not certify that agent code compiles or that your game works; console state is reported as read. See [What v1 Is Not]({{ site.baseurl }}/docs/what-v1-is-not/).
