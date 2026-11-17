# Vocal Handoff: Week 05 — Neural Fields vs. Parametric Belts

## 1. Summary of Predictions and Actual Measurements

| Prediction Target | Stated Expectation / Mechanism | Actual Measured Value | Verdict |
|---|---|---|---|
| **In-sample Score Change** | Network's high capacity should yield a better (more negative) in-sample score than the baseline. | Baseline in-sample: -33.092 <br> Unconditional Neural: -30.802 | Incorrect (The single unconditioned field was short on amplitude alignment and lost in-sample due to underfitting/lack of wing coordinates). |
| **Held-out Score Change** | The flexible network will overfit heavily without structured regularizations, performing worse than the champion. | Champion: -65.999 <br> Neural Concat: -47.955 | Correct (Parametric model outscores the neural fields on held-out folds). |
| **Best Conditioning Variant** | Concat vs. FiLM: Concat should be more stable on a tiny dataset; FiLM has too many parameters. | Neural Concat: -47.955 <br> Neural FiLM: 1891.961 | Correct (FiLM collapsed completely due to parameter scale on 3 training wings). |
| **Dishonest Stopping Leak** | Stopping directly on the test set should inflate the score significantly (e.g., ~1 to 5 nats). | Honest Budget (6 epochs): -46.165 <br> Leaked Budget (211 epochs): -50.890 | Correct (Cheating on stopping purchased a massive fictitious +4.725 nats). |

## 2. Key Physical Disagreements

### The Waldmeier Effect (Timing vs. Strength)
* **Week 3 baseline:** Forced to have a flat slope (0.000 yr / unit log A) by design.
* **Champion:** Built a sliding gate that translates early for stronger cycles, fitting a slope of -1.706 yr / unit log A.
* **Neural Concat:** Left completely free to structure its temporal profile, it discovered a timing slope of -0.842 yr / unit log A on its own. Stronger wings peak earlier under a pure neural representation without explicit equations.

### Belt Center Latitude at Phase Peak (s=0)
* **Clock Gauge Expectation:** 15.0 degrees
* **Week 3 baseline:** 14.5 degrees
* **Champion:** 12.8 degrees
* **Neural Concat:** 16.2 degrees — The independent neural witness suggests sunspots peak slightly further poleward than the champion’s parametric constraints wanted.
