# Donut Trader 0.1.1 — Fabric 1.21.11

Download `donut-trader-1.21.11-noapi.jar` using GitHub's **Download raw file** button, then place it in your Minecraft `mods` directory. Requires Fabric Loader 0.19.5 or newer and Fabric API for Minecraft 1.21.11. Remove any older Donut Trader JAR first.

This build uses auction listings without requiring an API key. Total purchase budget: 10,000,000 coins; minimum estimated net margin: 15%. Existing installations can run `/dt local` to select listing mode, then `/dt start` to observe. `/dt stop` stops the bot.

**Automatic trading starts disabled.** Auction/confirmation screen layout, price parsing, allowed items and actual fees must be configured and verified first. Open `/ah`, close it, and use `/dt inspect` to write the most recently observed screen to `config/donut-trader-inspect.txt`. The confirmation screen needs its own inspection as well.

Listing prices do not establish completed sales or guaranteed profit. This JAR was compiled against Minecraft/Fabric dependencies and passed pricing/configuration tests; it has not been tested making real trades on DonutSMP.

`SHA256SUMS` contains the download checksum.
