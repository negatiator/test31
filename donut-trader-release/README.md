# Donut Trader 0.1.2 — Fabric 1.21.11

Download **donut-trader-1.21.11-web-0.1.2.jar** with GitHub's Download raw file button. Remove older Donut Trader JARs from your Minecraft mods directory before installing. Requires Fabric Loader 0.19.5+ and Fabric API for Minecraft 1.21.11.

## Public web reference, no API key

This build reads the public [DonutSMP Terminal snapshot](https://donutsmpterminal.com/snapshots/latest.json), also used by the site's [All Items page](https://donutsmpterminal.com/all_items). It refreshes in the background at most once per five minutes while connected to DonutSMP. Run `/dt market` to see source status, usable item count and snapshot age. No separate Python process or DonutSMP API key is required.

The live integration check on 21 October 2026 received 1,408 usable AH unit-price references from a snapshot captured at **05:45 UTC / 08:45 Turkey time**. Example references in that snapshot: diamond 8,000; ancient debris 4,100,000; netherite ingot 12,100,000. These are reported asking-price references, not verified sales or permanent prices. No static price list is embedded in the JAR.

The site's schema is `[order, orderChange, AH, AHChange]`; this mod reads the AH column. A snapshot expires six hours after its own capture time, even if downloaded again. Individual item observation timestamps are not provided by the snapshot. [The source itself notes that captured prices may differ from the live auction house](https://donutsmpterminal.com/info/about-us).

The reference can only lower a resale estimate derived from current in-game listings. At least five matching live peer listings are still required, along with exact item components and stack counts. Custom items and enchanted variants are excluded from web pricing. Missing/expired references block automatic purchases while `useWebReference` is enabled. Total purchase budget remains 10,000,000 coins and minimum estimated net margin remains 15% after the configured fee.

## First use

1. Install the JAR and start Minecraft with Fabric.
2. On DonutSMP, run `/dt local` to disable any old official-API requirement, then `/dt market`. Default `useWebReference` is true, including when loading an older config that lacks this field.
3. Configure the actual auction title, price line, confirmation title/item/button slots, allowed items and real fee. Open `/ah`, close it, then `/dt inspect`; inspect the confirmation screen separately. `/dt start` only observes; `/dt stop` stops.
4. `/dt arm` requires a verified screen/fee profile, an allowed item list, a valid ledger and current web references. It does not turn on automatically at startup.

**Automatic trading remains disabled until the actual server screens and fee are configured and verified.** Minecraft/Fabric compilation, 17 Java tests and a read-only live source request passed. Actual purchases and relisting on DonutSMP have not been tested. A price comparison is not proof of a completed sale or guaranteed profit.

`SHA256SUMS` contains download checksums. Version 0.1.1 is retained for rollback; install only one version at a time.
