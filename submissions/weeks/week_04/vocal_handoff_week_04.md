# 🦋 Week 4 Handoff — pmahlin

## 1. Summary of Completed Runs
- We successfully set up and configured the modular Stage/Library architecture for Week 4's Scoreboard.
- Set workspace identity to `pmahlin`.
- Evaluated a power-law drift model ablation (`drift-power_law_custom`) which was physically expected to decelerate non-exponentially over the cycle.
- Evaluated standard width ablations (`width-latitude`, `width-amplitude`), profile shape ablations (`shape-weibull`), and direct emission without threshold (`emission-direct`).

## 2. Model Performance Standings
- **Best Honest Model:** `width-amplitude` with a paired gain of **+0.6981 +/- 0.3009** nats per hemicycle-year over the baseline, performing better in 15 out of 18 folds.
- The width dependency on cycle amplitude is clearly the dominant honest predictor of held-out wing shape.

## 3. Protocol Verification and Metrics
- Checked the protocol metrics under 3 distinct violations to find that:
  - Fitting amplitude on own events (Bound 1) artificially buys **~0.28 nats/hc-yr**.
  - Wing-specific shape parameter (Bound 3) artificially buys **~1.94 nats/hc-yr**.
  - True prediction must remain frozen under the protocol map, which is why we enforce fingerprint hash `5e55384fbc54`.

## 4. Next Week Alignment
- Verified physical plausibility using simulated butterfly diagrams on Held-out Cycle 19, which showed that the `width-amplitude` configuration reduces latitude spread errors and structures centroid drift naturally.
