---
layout: default
title: The Guided Trial
nav_order: 12
description: "The shipped practice session: five edits, one silent failure, one rollback. What it does, what the verified run produced, and two honesty notes about the sample scene."
---

# The Guided Trial
{: .no_toc }

1. TOC
{:toc}

---

The Guided Trial is the package's built-in practice session, imported as a sample ("Guided Trial") from the Package Manager. It exists so you can watch the whole AgentProof loop — receipts, a NO CHANGE an agent would never report, and a full rollback — before trusting it with a real session.

## The five edits

The practice driver executes five typical agent edits in sequence, simulating both direct Editor changes and file modifications:

1. TrialTurret rotation speed 7.5 → 12.0
2. TrialSettings boss health 400 → 40
3. A material/range edit on the trial barrel
4. A clamped property edit — the submitted value exceeds the component's clamp, so Unity's own validation silently clamps it back
5. TrialCrate asset deleted from the project, with an automatic snapshot captured

## The verified run

In the capture-verified run of this exact sample (Unity 6, this package, v1.0.0), the session produced **five receipts grouped into four burst rows** — receipts complete **22.7 s** after the window opened, rollback report on screen at **39.0 s**:

- **[VERIFIED]** TrialTurret speed 7.5 → 12
- **[VERIFIED]** TrialSettings.asset bossHealth 400 → 40
- **[NO CHANGE]** TrialBarrel.mat range 10 → 10 — edit 4's clamp, caught by read-back
- **[VERIFIED]** Assets/TrialCrate.prefab Exists → Deleted

Rolling the session back restored **all five entries** (the crate from its snapshot copy; the rest to baseline values) — see [Rollback]({{ site.baseurl }}/docs/rollback/).

![The trial scene as it ships, in the Scene view: an empty grid — see the honesty notes below]({{ "/assets/images/trial-scene-editor.png" | relative_url }})

## Honesty notes — read before you judge the sample

1. **The trial scene is logic-only.** Its roots are exactly TrialTurret and TrialCrate: **zero renderers, no camera, no light.** Opening the scene shows an empty grid, as in the frame above. The practice is about receipts and rollback, not visuals — but you should know the scene looks like nothing before a buyer tells you.
2. **The trial import copies the sample without `.meta` files.** In an importing project, the imported scene's TrialTurret component instances are **not found by type scan** and `TrialSettings.asset` does not load as its type. The practice session still runs end-to-end, because the driver works from journal and baseline data rather than live components — but the imported scene you inspect is not wired the way the package source describes.
3. **Practice sessions are state-dependent.** Run on a non-pristine state (a second run after a rollback), the driver produces a different receipt set — different starting state, different truth. See [Session Review]({{ site.baseurl }}/docs/session-review/).
