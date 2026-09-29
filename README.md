# Fortress / Gauntlet Wave Simulator & Comp Optimizer

An interactive web-based simulator and party composition optimizer for Fortress / Gauntlet skilling raids.

🔗 **Live Tool**: [https://adversaryicu.github.io/fortress-calculator/](https://adversaryicu.github.io/fortress-calculator/)

---

## Features

- **Live Combat Tick Engine**: Simulates front-wave damage mitigation (`DEF_K = 600`), 3-lane incoming enemy attacks with shield weighting (`1.5x`), and dynamic player deposit cycles.
- **Exhaustive Role Optimization**: Evaluates 350 valid party role multisets across host and clones to find the mathematical maximum survival depth.
- **Wave Scaling**: Models exact game health, defense, attack curves, and the 3-wave stack cap overrun mechanism.
- **Upgrade Sensitivity & Roadmap**: Ranks every skill by marginal wave ROI and highlights the #1 bottleneck holding your team back.
- **Interactive "What-If" Sandbox**: Sliders to test arbitrary skill levels in real-time.
- **Zero Dependencies**: Pure vanilla HTML/CSS/JavaScript with responsive dark UI.

---

## How to Use

1. Open the [Live Calculator](https://adversaryicu.github.io/fortress-calculator/).
2. Run the provided console audit snippet in your game DevTools (`F12` $\rightarrow$ Console).
3. Paste the audit JSON into Step 2.
4. Click **Run Simulation & Find Best Comp**!
