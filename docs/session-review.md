---
layout: default
title: Session Review
nav_order: 9
description: "Sessions, bursts and readable before/after property rows in one timeline — with receipt amendments and rollbacks shown in place, and the audit log one click away."
---

# Session Review
{: .no_toc }

1. TOC
{:toc}

---

The Session Review is where the journal becomes readable. Open it from AgentProof Home (or its menu shortcut into the same window).

## What you see

- **Sessions** in chronological order, expandable in place.
- **Bursts** inside each session, with **readable before/after property rows** — the same rows the receipts were issued from. The shipped Review renders receipts as inline rows; there is **no separate receipt-detail view**, by design: the row is the detail.
- **Verdict counts** per session (for example "Verified: 3 \| No Change: 1 \| Applied with issues: 0").
- **Amendments and rollbacks in the same timeline** — a rollback does not erase the session it undid; it appears after it, with its report. A rollback burst itself produces receipts (in the trial's post-rollback Review, the counts rose to Verified: 4 including the rollback burst).

![A three-session Review timeline in the Studio build, third session expanded: a speed edit, a colour diff, a deletion burst]({{ "/assets/images/studio-review.png" | relative_url }})

## Practice sessions are state-dependent

One behaviour worth knowing before you judge a receipt set: the Guided Trial driver works from the project's current journal/baseline state. Run on a non-pristine scene (for example, a second run after a rollback), it can produce a **different receipt set** — in verification, a third session on a post-rollback scene produced three bursts including a colour change and a turret deletion that the canonical first run did not. That is the journal telling the truth about a different starting state, not inconsistency.

## From review to evidence

From the Review you can **Export Audit Log** (JSON + Markdown) for a bug report or a client email — see [Audit Log Export]({{ site.baseurl }}/docs/audit-log-export/) — and roll back any burst or session — see [Rollback]({{ site.baseurl }}/docs/rollback/).
