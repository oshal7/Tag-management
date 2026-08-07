# Compass · Tag Management — Build log

Living log of everything we've built, newest first, with links. Every push
auto-deploys to GitHub Pages.

- **Live site:** https://oshal7.github.io/Tag-management/
- **Repo:** https://github.com/oshal7/Tag-management (branch `claude/session-yqmsqa`)

---

## Consumption module — `consumption.html`
Live: https://oshal7.github.io/Tag-management/consumption.html

- **2026-08-07 — Group + Resource 360 upgrades.** Resource 360 now splits the
  confusing single block into a clear **Cost roll-up path** (Resource → App →
  Service → Group → Account, with "rolls up into" between each) and a separate
  **Dependency tree** (parent/children); the **Pin** button is gone and an
  **✦ AI insights** card is added. **New** (🟢) and **terminated** (🔴) resources
  are surfaced everywhere — highlight cards in a group's Overview, NEW/TERMINATED
  badges + row styling and quick-filter chips in the Resources tab, and status on
  the resource page. Trends in both group and resource pages became real area
  charts with month ticks and a **3M / 6M / 12M** duration filter. **Download
  report** now actually works — client-side CSV for a group, a resource, and the
  landing **Export** (all from a cost/consumption standpoint).
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
- **2026-08-07 — Shorter resource-type mapping.** In the group review detail, the
  resource-type mapping now shows the top **15** types with a **＋ Show N more
  types** toggle instead of a long list (all onboarding approaches).
- **2026-08-04 — Rule-first conflict resolution in the wizard.** The wizard's
  *Resolve conflicts* step is now **tabbed — “By rule” (default) / “By
  resource”**. The rule view collapses all 332 conflicting resources into the
  handful of **rule overlaps** actually causing them (e.g. *Payments Platform ∩
  Audit & Compliance*), shows both clashing rules with the weak one flagged, and
  lets you resolve the whole cluster in one click — with a Compass recommendation
  toward the stronger ownership rule, a progress bar, and Undo. The old
  per-resource list is preserved under the second tab for granular control.
  Applied to **both** the main prototype's wizard view (`onboarding-v2.html`)
  and the standalone `onboarding-wizard.html` so they behave identically.
- **2026-08-04 — Wizard is now the main prototype; Cards is a page inside it.**
  `onboarding-v2.html` is now a single prototype that opens on the **guided
  Wizard** (Review groups → Resolve conflicts → Map & finish) by default, with
  the original **Cards** flow moved to a separate in-app page. Switch between
  them from the sidebar (Onboarding → *Wizard flow* / *Cards flow*) — both share
  one shell, one 14,400-resource engine, and the same rule-editing plumbing, so
  editing a rule in the wizard behaves exactly like it does in the cards flow.
  The wizard's finish step links straight into the Consumption dashboard.
  Live: https://oshal7.github.io/Tag-management/onboarding-v2.html
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
