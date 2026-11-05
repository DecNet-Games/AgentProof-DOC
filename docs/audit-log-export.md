---
layout: default
title: Audit Log Export
nav_order: 10
description: "Export the journal from the Review as full-fidelity JSON plus a plain-language Markdown summary, to a folder you choose."
---

# Audit Log Export
{: .no_toc }

1. TOC
{:toc}

---

From the Session Review, **Export Audit Log** writes the journal to a folder you choose, in two forms:

## JSON export

The complete machine-readable audit trail: burst sequences, content hashes, property deltas, console captures, and read-back verdicts — full fidelity, suitable for tooling, diffing, or attaching to an issue tracker.

## Markdown summary

A human-readable summary listing all sessions, bursts, and verdicts in plain language, with zero emojis — the version you paste into a bug report or a client email when the question is "what did the agent actually do to my project?"

## What the export is

The export is a faithful copy of the append-only journal (see [The Change Journal]({{ site.baseurl }}/docs/change-journal/)): sessions, bursts, verdicts, amendments, rollbacks and — in Studio — gate decisions, in the order they happened. It contains only what AgentProof observed and recorded; an edit neither watch mode could see was never journalled and so never appears. All data stays on your machine — the export writes only to the folder you pick.
