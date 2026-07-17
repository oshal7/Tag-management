# Compass — Lo-fi Wireframe

A clickable **low-fidelity wireframe** of **Compass**, the non-production cloud
cost attribution, showback, and self-serve tagging tool described in the product
PRD. It maps untagged non-prod AWS resources to the Product Line that owns them
using signal-based inference (the S1–S14 attribution engine), and presents finance
and engineering with a confidence-scored, evidence-backed view of who is spending
what in Dev/Test/QA.

This is a **design prototype for review, not production code** — there is no
backend, no data, no build step. It exists so you can see how the tool is
structured and how the screens hang together before anything real is built.

## Open it

Open `wireframe.html` in any browser:

```
open wireframe.html      # macOS
xdg-open wireframe.html  # Linux
```

Everything is self-contained in that one file (inline CSS + vanilla JS, no
external assets or network calls).

## What's in it

16 screens across the analytics surface and the set-up journey, navigable from
the left sidebar.

**Analytics (the reporting surface):**

1. **Product Cost Overview** — headline spend per product, coverage meter, trend
2. **Coverage & Confidence** — the estate split across confidence bands
3. **Product → Resource** — four views in tabs: Cost Treemap, Resource Explorer,
   Relationship Graph, Attribution Provenance
4. **Product Drill-down** — one product's accounts, drivers, and trend
5. **Resource Details** — deep object view with the full evidence trail
6. **Review Queue** — resolve ambiguous resources; apply decisions as rules
7. **Rules & Authoring** — prompt-to-rule + manual builder, shared live preview
8. **Shared / Overhead** — how unowned spend is split (S14) + the residual bucket
9. **Waste & Orphans** — idle/unattributed resources
10. **Signal Health** — diagnostics on the inputs that drive accuracy

**Set-up flow (discover → review → map):**

11. **Connect & Scope** — connect data sources; mark accounts prod vs non-prod
12. **Discovered Products** — the system proposes candidate products from the
    rules/strategies; rename, edit/delete rules, delete or create a product
13. **Product Rules** — per-product rules; tweak/delete, add via AI or builder
14. **Run Mapping** — animated loader linking resources to products
15. **Mapping Complete** — per-product cost, resource counts, unique/changed
16. **Product Workspace** — a product page with cost insights + three views:
    resource-type cards, a flat resource list, and a relationships view where
    moving a resource suggests its linked neighbors come with it

**Explorations (design iterations):**

17. **Product Details · layouts** — the same 3,214 resources shown four ways to
    compare how best to organize a huge list: a parent→child hierarchy tree,
    an Application/Service grouping, dependency clusters, and a cost map paired
    with a dense faceted list
18. **Resource 360** — a deep resource page: the full ownership ladder
    (Dept → Team → Product → Application → Service → Resource) with the signal
    behind each hop, attribution evidence, all tags & metadata, cost insights
    (run-rate, trend, breakdown, forecast, share), and a linked & shared panel
    that flags cross-product sharing (S14)

## Design intent

Deliberately lo-fi — grayscale boxes and monospace annotations keep attention on
layout and structure rather than visual polish. The **one** exception is color:
the four confidence bands (**auto-assigned**, **inferred**, **needs-review**,
**shared-overhead**) are colored throughout, because confidence visibility is the
product's core promise. Content uses realistic placeholder data (Payments,
Checkout, Search…) so each screen reads like the real tool.
