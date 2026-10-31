# VOCAL HANDOFF — WEEK 03

## Domain: Point Processes (Level 2)
* **Anchors:** intensity surface, emission function
* **Status:** deployed
* **Priors:** none
* **Key Insights:** We successfully migrated our 1D point-process intensity lambda(s) (representing events/year) into a 2D inhomogeneous Poisson process **intensity surface** Lambda(|lambda|, s) measuring events per degree of latitude per year over the region |latitude| in [0, 60] degrees. The intensity is modeled via an **emission function** utilizing a softplus buoyancy threshold over a latent field: Lambda(|lambda|, s) = c * softplus(B - B_crit)^alpha. Due to the change of units, the absolute likelihood scales of Week 02 and Week 03 are fundamentally incomparable.

## Domain: Statistical Inference (Level 2)
* **Anchors:** latent variable, gauge freedom, partial pooling, leave-one-cycle-out cross-validation, held-out log-likelihood, quadrature mesh
* **Status:** deployed
* **Priors:** none
* **Key Insights:**
  1. The magnetic field B(|lambda|, s) is modeled as a deterministic **latent variable** that cannot be observed directly but is inferred through emerging sunspot groups.
  2. We eliminated parameter degeneracies (**gauge freedom**) by locking B_crit = 1.0, alpha = 1.0, and the global temporal anchor mu_ref = 15 degrees.
  3. We used **partial pooling** to share the shape parameters (k, theta, mu_a, mu_b, and the spatial width parameters) across all 18 development wings while solving for individual peak field amplitudes a_hc dynamically. The scale parameter c was solved analytically in closed form.
  4. To score our models, we implemented **leave-one-cycle-out cross-validation** (LOCO CV) over 9 cycles, re-deriving the aligned clocks and shared parameters inside each training fold to calculate the unbiased **held-out log-likelihood** per hemicycle-year.
  5. We standardized a 201 x 241 node **quadrature mesh** (31 days in time, 0.25 degrees in latitude) and proved that coarse meshes systematically flatter sharper models by underestimating the integrated intensity subtractive term.

## Domain: Solar Cycle Physics (Level 2)
* **Anchors:** buoyancy threshold, drift track, belt width
* **Status:** deployed
* **Priors:** none
* **Key Insights:** Sunspots only emerge when the latent field exceeds a critical **buoyancy threshold**. The band's center moves along an exponential **drift track** mu(s) = mu_ref * exp(-s / mu_b) toward the equator with a decay timescale of mu_b = 8.02 +/- 0.11 years. We tested three **belt width** models using paired LOCO CV differences: a constant width (w0 = 6.50 degrees), an amplitude-dependent width (w(a_hc) = w0(a_hc/A_ref)^gamma), and a latitude-dependent width (w = w0 + w1*mu). Both variable-width models outperform the baseline. The amplitude-dependent width model yields the highest mean paired improvement (+0.70 nats/yr) but is highly skewed by Cycle 19N. The latitude-dependent width model (w = 4.84 + 0.11*mu) yields a more robust, stable gain (+0.14 nats/yr).
