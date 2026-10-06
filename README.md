# Fortress Raid Wave Simulator & Comp Optimizer

An interactive, client-side combat simulator, party composition solver, and upgrade roadmap engine for Fortress / Gauntlet skilling raids.

**Live Tool**: [https://adversaryicu.github.io/fortress-calculator/](https://adversaryicu.github.io/fortress-calculator/)

---

## Overview

The **Fortress Wave Simulator** bridges the gap between player skilling stats and deep raid survival. Instead of guessing party configurations, this tool runs live tick-by-tick combat and logistical delivery simulations using your character's exact stats, unlocks, and movement speeds to determine the mathematical optimal team setup and highest-ROI skill upgrades.

---

## Key Features

### 100% Client-Side & Private
- **Zero External Telemetry**: All combat iterations, party solvers, and audit data processing execute strictly inside your local browser memory.
- **Open Source**: Full source code is inspectable in this repository.

### Dynamic In-Game Data Extractor
- Extract your real account stats with a single copy-paste in DevTools (`F12` -> Console).
- **No Hardcoded Values**: Dynamically evaluates live bonuses:
  - **Dynamic Movement Speeds**: Evaluates Vigor levels, effective level gear/pets/capes/tools, telescope and shiny telescope relics, swift beacons, enchanted compasses, milestone banners, ledgers, raid tree talents, and collector bonuses for both Host and Clones (`0.9x`).
  - **Real Node Path Distances**: Measures precise arena traversal distances using in-game pathfinding or live map node coordinates (`ClientState.getPathDistance` / `ClientState.nodesData`).
  - **Action Rates & Haste**: Factors in exact gather/refine success rates, double gather %, item save %, action times, and Gauntlet 10x haste.
  - **Dynamic Bag Capacity**: Automatically counts base slots plus unlocked satchels.
  - **Robust Clipboard Pipeline**: Uses multi-stage fallback (DevTools native `copy()`, offscreen textarea selection, and modern Clipboard API).

### Combat Tick & Delivery Simulation Engine
- **Tick-by-Tick Combat**: Models front-wave damage mitigation (`DEF_K = 600`), 3 attack damage lanes (Melee, Range, Magic) with shield defense weighting (`1.5x`), and wave health depletion.
- **Overrun Mechanics**: Simulates wave timeouts, DPS checks, Fortress health attrition, and the lethal 3-wave stack cap overrun rule.
- **Logistical Cycle Modeling**: Simulates continuous deposit deliveries from the Host and Clones based on individual cycle and travel times.

### Exhaustive 350-Composition Solver
- Iterates and tests all **350 valid party role multisets** across the 5 combat roles:
  - **Health** (Fish + Cook)
  - **Melee Force** (Mine + Smith)
  - **Range Force** (Forage + Craft)
  - **Magic Force** (Invoke + Imbue)
  - **Defense** (Farm + Brew)
- Identifies the provably optimal composition to maximize wave depth.
- Displays a head-to-head comparison between the optimal setup and the standard balanced composition (1 of each role).

### Dynamic In-Raid Task-Swap Simulator & Optimizer
- **Mid-Raid Role Transition Engine**: Models the game's actual mechanic where the **Host** can switch to any other role during the fortress run, while **Clones** remain locked to their assigned roles.
- **Deposit & Wave Trigger Detection**: Automatically simulates and checks whether swapping after **X deposits** or **after Wave X** unlocks an extra cleared wave.
- **Frontload vs. Sustain Analysis**: Identifies high-value transition tactics (e.g., frontloading early damage with Melee/Range to melt initial waves, then swapping to Health to absorb late-wave boss scaling).
- **Interactive Sandbox Playground**: Includes a dedicated simulator panel to test custom swap triggers (start role, target role, deposit/wave conditions, and clone presets) with live timeline updates.
- **3-Way Strategy Comparison**: Compares **Standard**, **Optimal Static**, and **Dynamic Host-Swap** configurations side-by-side with full delivery share and timeline logging.

### Rare Loot Drop Probability Engine
- Derives odds from the official Gauntlet loot formulas (`GAUNTLET_RARE_DROP_BASE = 0.0002381`, `GAUNTLET_RARE_CAP_L = 64` plateau).
- **Cumulative Run Probability**: Calculates your total cumulative odds of receiving at least one rare drop across your run (e.g. `4.0% Overall`, `~1 in 25 runs`).
- **All 7 Reward Tiers**: Displays individual activation status and per-run drop chances for every tier:
  - **Tier 1 (Feeble)**: Unlocks Wave 1
  - **Tier 2 (Dire)**: Unlocks Wave 21
  - **Tier 3 (Savage)**: Unlocks Wave 41
  - **Tier 4 (Fell)**: Unlocks Wave 61
  - **Tier 5 (Ancient)**: Unlocks Wave 81
  - **Chaos C6 (Chaos)**: Unlocks Wave 101
  - **Chaos C7 (High Chaos)**: Unlocks Wave 121
- **Peak Rate**: Displays the drop roll chance on the highest cleared wave alone.

### Upgrade Sensitivity & Roadmap
- **#1 Priority Bottleneck**: Automatically highlights the single biggest bottleneck holding your party back (e.g., an un-tiered skill cap limiting stat yield).
- **ROI Upgrade Table**: Projects wave gains and cycle improvements for leveling each skill (+1 Level, +5 Levels, or to the next Tier milestone), ranked by efficiency.

### Party Contribution & Wave Timeline
- **Team Delivery Breakdown**: Table showing trips completed, items processed, total stats contributed, and percentage share between the Host and Clones.
- **Wave-by-Wave Timeline**: Complete log of every wave survived, detailing spawn times, enemy HP, wave defense, remaining fortress health, and wipe causes.

### Zero Dependencies
- Pure vanilla HTML5, modern CSS, and vanilla JavaScript.
- Lightweight, fast-loading, offline-capable, and fully responsive on desktop and mobile.

---

## Getting Started

1. Open the [Fortress Raid Wave Simulator](https://adversaryicu.github.io/fortress-calculator/).
2. In your game browser tab, press `F12` to open DevTools and switch to the **Console** tab.
3. Paste the extractor snippet from **Step 1** and press `Enter`. The script audits your account and copies the JSON data to your clipboard.
4. Paste the JSON into **Step 2** on the simulator page.
5. Click **Run Simulation & Find Best Comp** to view your results, loot probabilities, and upgrade recommendations!

---

## License

MIT License. Free to use, modify, and distribute.
