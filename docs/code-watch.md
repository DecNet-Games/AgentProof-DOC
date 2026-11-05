---
layout: default
title: Code-Watch (Studio)
nav_order: 16
description: "A shipped engine with four checks on agent script diffs. Verified against the product's own fixtures — and, stated plainly, not wired into the live watch pipeline in v1.0.0."
---

# Code-Watch (Studio)
{: .no_toc }

> **Scope, stated exactly.** Code-watch is a **shipped engine**, verified against the product's own fixtures. In v1.0.0 the engine is **not wired into the live watch pipeline**: it is never called by File Watch or the receipts engine, so its findings are **not surfaced in the window and are not attached to receipts**. The Studio window carries a Code-Watch heading; no findings list exists in the shipped build. This page documents the engine as it actually ships — no more.
{: .block-tip }

1. TOC
{:toc}

---

## The four checks

The `CodeWatchEngine` evaluates an agent script diff against four targeted failure patterns:

1. **Serialized-field rename without `[FormerlySerializedAs]`** — a renamed field with no migration attribute is flagged as a probable rename: the silent data-loss pattern for Inspector-bound assets.
2. **Fake-null patterns** — `?.` access, `is null` or `== null` idioms on `UnityEngine.Object`-derived fields, which bypass Unity's lifetime checks: Unity's destroyed-object null is not a real null.
3. **Member APIs not in your Unity version's index** — member accesses are checked against a bundled per-Unity-version API index (one for 2022.3, one for Unity 6). A member not present is flagged as **not found in the index** — an index result, never a claim of proof.
4. **Event subscription without an unsubscribe** — a `+=` with no matching `-=` in the same class, flagged as a leak risk.

## Verified behaviour — the fixture run

Run over the product's own shipped test fixtures, the engine produced **6 findings**, one per pattern it is built for:

| Finding | Fixture evidence |
|---|---|
| fake_null | `Assets/TestFakeNull.cs` — destroyed-object null is not a real null; fix: explicit `!= null` check |
| invented_api | `GameObject.FindByTag` — not in the Unity 6000 API index → `FindWithTag` |
| event_without_unsubscribe | subscription with no matching `-=` — leak risk |
| rename_without_attribute | ×2 — suggested `[FormerlySerializedAs("oldSpeed")]` and `[FormerlySerializedAs("OldSpeed")]` |
| version_api (under "2022.3") | `Rigidbody.linearVelocity` — not in the 2022.3 index → `velocity` |

## What v1.0.0 does not do with it

- Findings do **not** appear in the Session Review, on receipts, or anywhere in the window.
- No verdict changes because of a code-watch finding — an "Applied with issues" verdict in v1.0.0 is never a code-watch result (see [Receipts & Verdicts]({{ site.baseurl }}/docs/receipts-and-verdicts/)).
- There is **no one-click fix surface** — the fix suggestions above are the engine's finding text, not an applied repair.
- It is four targeted diff checks, not a linter and not full-codebase static analysis, and it never silently modifies code.
