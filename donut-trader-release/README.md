# Donut Trader 0.2.0 — Fabric 1.21.11

[**Download the automatic trading JAR**](donut-trader-1.21.11-auto-0.2.0.jar?raw=true).

Remove older Donut Trader JARs from your Minecraft `mods` folder and install this JAR. Requires Minecraft Java **1.21.11**, Fabric Loader **0.19.5+**, and Fabric API for **1.21.11**. On DonutSMP run:

```text
/dt auto
```

`/dt stop` stops; `/dt status` reports progress; `/dt market` reports the public price source. No API key, Python process, manual screen profile, or old `/dt arm` sequence is needed for AUTO. The mod does not start trading by itself when Minecraft launches.

## Behavior and limits

AUTO searches standard commodities, scans up to three pages per item, checks at least five matching live peer listings, buys a qualifying stack and relists it. Total cumulative purchase budget is **10,000,000 coins**, including previously reserved purchases. Minimum estimated net margin is **15%**; AUTO assumes at least **10%** selling fees for calculations. The actual server fee and eventual sale price are not verified by that estimate.

The public [DonutSMP Terminal snapshot](https://donutsmpterminal.com/snapshots/latest.json) supplies AH unit-price references (array index 2). It only caps resale estimates downward; live matching listings are also required. The snapshot expires six hours after its capture timestamp. Its prices are asking-price references, not completed sales. No static price list is embedded.

The purchase budget is persisted before clicking. Compact prices such as `$2.5M` are treated as ranges, with the upper bound reserved. Native Minecraft confirmation dialogs require exact item/count and bounded price evidence. Delivery and hotbar moves require server inventory updates. A relist is only reported after a new matching row appears in Your Items; inventory disappearance alone is insufficient. Existing identical inventory stacks are skipped, and multi-page personal listings or unrecognized screens stop the transaction rather than guessing.

A confirmed listing is **not a completed sale or realized profit**. Direct-delivery purchases retain the visible quote upper bound as estimated cost; exact account debits are not independently measured. Unknown post-purchase states remain recorded in `config/donut-trader-ledger.json` and block a blind retry. Do not delete that file to work around an unresolved transaction. Existing older-version budgets are migrated to minor currency units; do not run an older JAR against the migrated ledger.

## Validation

Fabric/Minecraft compilation, **54 tests**, and a read-only live public-source probe passed. The probe found 1,408 usable references in the 21 October 2026 05:45 UTC snapshot. Tests cover decimal and compact prices, budget migration, the supplied 45-listing layout, native dialog evidence, authoritative inventory acknowledgements, and new-listing conditions. **Actual account purchases and relisting on DonutSMP were not exercised in this build environment.**

UI research reference: [pinned AuctionExitExecutor](https://github.com/0utsights/donut-auction-flipper/blob/bc14d4ef5a5382e7bfca32125272e1f9dd87430c/minecraft/client-mod/src/main/java/net/donutnetwork/client/AuctionExitExecutor.java). Public price-source information: [DonutSMP Terminal](https://donutsmpterminal.com/info/about-us).

`SHA256SUMS` contains download checksums. Previous JARs are retained as historical artifacts; install only the 0.2.0 JAR.
