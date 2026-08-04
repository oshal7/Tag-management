# Compass · Tag Management — Build log

Living log of everything we've built, newest first, with links. Every push
auto-deploys to GitHub Pages.

- **Live site:** https://oshal7.github.io/Tag-management/
- **Repo:** https://github.com/oshal7/Tag-management (branch `claude/session-yqmsqa`)

---

## Consumption module — `consumption.html`
Live: https://oshal7.github.io/Tag-management/consumption.html

- **2026-08-03 — Scaled to ~14,400 resources.** The consumption module now runs
  on a realistic estate: **14,400 placeholder resources** across **40 AWS types**
  (EC2, RDS, Aurora, Redshift, EKS, Lambda, S3, DynamoDB, EMR, SageMaker, MSK,
  OpenSearch…) distributed into the five groups (3,400 / 2,600 / 2,100 / 2,300 /
  1,800) plus **1,200 unassigned · 700 unnamed · 300 orphaned**. Assignment is
  computed once and cached (invalidated on every move / assign / rule edit), so
  group pages, buckets, and the explorer stay fast; large lists render capped
  (250 in a group, 150 in the assign drawer, 400 in the explorer) with a
  "showing X of N" note so the DOM never chokes on thousands of rows.
- **2026-08-03 — Rule editor + module stitching.** Edit/add a group's rule
  conditions (field · operator · value, with a live match count) and its
  name/kind from Group details → *Edit rules*, the way onboarding does.
  Sidebars now link **Onboarding ↔ Consumption ↔ Resource Explorer** so the two
  modules navigate as one product (`#explorer` deep-link supported).
- **2026-08-03 — Group tabs, Resource Explorer, smart move.** Group details
  gained **Overview / Resources** tabs; the **Sub-groups** card moved to the
  right rail. New **Resource Explorer** (table/cards, search + type/account/env/
  group filters, bulk-select → one-click map to a group). **Smart move flow**:
  moving resources recommends *linked* resources not selected, grouped by
  cluster/relationship (child/parent/linked), scalable to many.
- **2026-08-03 — Resource 360 reworked.** Dropped Attribution & Evidence;
  hierarchy/roll-up ladder on top; kept cost insights; **Linked & shared** now
  opens a side drawer with a **List ⇄ Graph** toggle.
- **2026-08-02 — First cut.** All groups on one page with a **# ⇄ $** switcher;
  **Cards** + **Cost treemap** iterations; **Unassigned / Unnamed / Orphaned**
  buckets with an assign flow; group details with money at all levels
  (trend, cost-by-service donut, cost-by-account/env bars) + AI insights.

## Onboarding module
- **2026-08-04 — Scaled to ~14,400 resources (all four approaches).** Every
  onboarding iteration now analyses the same realistic estate as consumption:
  **14,400 resources across 36 AWS types**, with the five system-suggested
  groups sized 3,400 / 2,600 / 2,100 / 2,300 / 1,800, **85% coverage**, and
  **~332 real conflicts** where the cross-cutting *Audit & Compliance* rule
  overlaps Payments and Core (genuine chaos to resolve). Matched-resource
  tables stay capped (top 5–6 + "…and N more") so the rule-review pages render
  instantly. onboarding-v2, wizard and board run this on their live rule engine;
  onboarding v1's static figures were updated to match.
- **2026-08-02 — onboarding-v2 (primary).** Refined cards that expand to an
  inline rules page (functional engine): manual + AI add-condition, matched-
  resources table (account/VPC/owner/tags), resource-type count mapping.
  Live: https://oshal7.github.io/Tag-management/onboarding-v2.html
- **2026-08-02 — Wizard approach.** 3-step guided setup: review each group
  (full detail) → resolve conflicts → initiate mapping (loader → done).
  Live: https://oshal7.github.io/Tag-management/onboarding-wizard.html
- **2026-08-02 — Board / kanban approach.** A column per group with a Review
  drawer (board-styled details) + Start mapping.
  Live: https://oshal7.github.io/Tag-management/onboarding-canvas.html
- **2026-08-02 — onboarding v1.** First Opsolute-style onboarding: Cards /
  Workspace / Guided iterations, AI drawer, conflict resolver.
  Live: https://oshal7.github.io/Tag-management/onboarding.html

## Compass wireframes (lo-fi, hand-drawn)
- **2026-07 — v2 interactive prototype.** Rule engine, groups, live conflicts,
  cost treemap, Resource 360 — separate-page shell.
  Live: https://oshal7.github.io/Tag-management/v2.html
- **2026-07 — v1 static wireframe.** 23 screens covering the full information
  architecture (overview, coverage, treemap/explorer/graph/provenance, review,
  rules, reporting, governance, time-travel).
  Live: https://oshal7.github.io/Tag-management/wireframe.html

## Hosting
- **2026-07 — GitHub Pages.** Landing page + Actions deploy workflow; every push
  redeploys.
  Live: https://oshal7.github.io/Tag-management/
