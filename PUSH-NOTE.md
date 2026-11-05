# PUSH NOTE — AgentProof-DOC (built 2026-11-05, local only, NOT pushed)

## What this folder is

The complete, push-ready source tree for AgentProof's documentation site, built to the Decnet house "-DOC" pattern (master prompt: `~/workspace/unity-listings/perch-docsite-prompt.md`; structure/config mirrored from SteamDeck-DOC and ShipSheet-DOC):

- Just the Docs Jekyll site via `remote_theme` (no `theme:` gem key, no `just-the-docs` gem in the Gemfile — the pairing that fixed the two known GitHub Pages errors: "The just-the-docs theme could not be found" and "The github-pages gem can't satisfy your Gemfile's dependencies").
- 23 content pages: Home + Getting Started + Installation + Quick Start + The Home Window + The Change Journal + Receipts & Verdicts + Watch Modes + Session Review + Audit Log Export + Rollback + The Guided Trial + Checkpoints + Conflict Detection + Approval Gate + Code-Watch + Settings + Editions + What v1 Is Not + FAQ + Troubleshooting + Changelog + Support.
- Real media only, repo-relative under `assets/`: 9 real Editor captures from the verified capture session in `../raw/` (welcome, watch status, receipts, rollback report, Studio section, checkpoint take, gate section, three-session review, trial scene), the catch-and-rollback GIF, and the demo video (`assets/videos/agentproof-overview.mp4`). Whole site ≈ 2.1 MB.
- Content sourced from the shipped package (`C:\Users\anshw\Projects\Unity-Assets\AgentProof\Packages\com.decnetgames.agentproof` — package.json, CHANGELOG.md, `Documentation~` quick-start / reference / what-v1-is-not, Guided Trial README), the reconciled listing copy (`../LISTING-COPY-FINAL.md`), and the capture session's `../VERIFY.md`.
- **Reconciliation discipline (the reason this tree was built after the capture session):** wherever the shipped docs or the prep listing copy conflict with `VERIFY.md`, VERIFY.md wins. Applied corrections: checkpoint restore = captured `Packages/manifest.json` snapshot only (never "return the whole project"); conflict detection = engine-level, no conflict view; code-watch = shipped engine, not wired into the live pipeline, findings reach no window surface and change no verdict; no setup-report panel; trial scene logic-only + `.meta`-less import disclosed; macOS never claimed (unverified — Editor verification on Windows only).
- No product Asset Store URL exists yet (draft only), so Home/Installation link the Decnet Games publisher page (118262) — swap in the product URL after the listing goes live, as with SteamDeck-DOC.

## Exact repo to create

- **Name:** `AgentProof-DOC`
- **Owner:** `DecNet-Games` (GitHub org account)
- **Visibility:** public (required for GitHub Pages on this setup)
- **Live URL once Pages is on:** https://decnet-games.github.io/AgentProof-DOC/ (matches the `baseurl: "/AgentProof-DOC"` already set in `_config.yml`)

## Push route (do this from the laptop, per the standing no-card-spam rule)

Bulk pushes go via laptop git over SSH — never the GitHub connector.

1. BOSS creates the empty repo `DecNet-Games/AgentProof-DOC` on GitHub (no README, no .gitignore — this tree carries its own).
2. Copy this folder's contents to the laptop clone location, then: `git init` (if needed) → `git add .` → `git commit` → the final `git push` is BOSS's own ~10-second action at his terminal (laptop git credentials only work interactively — known constraint).
3. On GitHub: repo **Settings → Pages → Build and deployment → Source: GitHub Actions** (the standard github-pages workflow), or "Deploy from a branch" → `main` / root if Actions is unavailable. PERCH-DOC/SteamDeck-DOC run on the same org setup — mirror whichever source they use.
4. After the first successful build, verify:
   - the live URL loads with the Just the Docs theme (no theme error),
   - Home shows the receipts hero image, the GIF, and the demo video plays,
   - nav order: Home, Getting Started, Installation, Quick Start, The Home Window, The Change Journal, Receipts & Verdicts, Watch Modes, Session Review, Audit Log Export, Rollback, The Guided Trial, Checkpoints (Studio), Conflict Detection (Studio), Approval Gate (Studio), Code-Watch (Studio), Settings, Editions — Standard vs Studio, What v1 Is Not, FAQ, Troubleshooting, Changelog, Support.
5. Only after the site is live: the portal listing description for AgentProof can carry the house link line with `DOCUMENTATION → https://decnet-games.github.io/AgentProof-DOC/` (dead-link rule: never publish the link before the site resolves). The house-format description is ready at `../DESCRIPTION-HOUSE.md`, and the portal draft copy is `../LISTING-COPY-FINAL.md` — never the prep original.

## What remains

- Repo creation + push + Pages enable: BOSS-side steps above (by design — this build stopped at a complete local tree, per instructions).
- Nothing in the tree itself: content, config, Gemfile, and media are complete and internally verified (page count, front matter, nav order, and every asset reference checked against disk).
- Product-side open items that belong to the capture pack, not this tree: the gate approval-prompt pair and the Settings close-frame are manual captures (~2 min at the editor, by design) — see `../VERIFY.md` Open Items.
