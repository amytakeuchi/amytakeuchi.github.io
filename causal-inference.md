# Causal Inference

I use causal inference and experimentation to estimate
the incremental impact of business interventions.

### Featured Projects

## Geo Incrementality Measurement — Causal Inference Pipeline
Built a production-style geo experiment pipeline across 60 markets, implementing five causal estimators in parallel (DiD, TBR, CUPED, CUPAC, Synthetic Control, Bayesian Hierarchical) to measure paid social incrementality. The core contribution is diagnosing and fixing systematic estimator failures — including a Synthetic Control scaling bug that collapsed RMSPE from 51,332 to 1,998 — rather than simply reporting a lift estimate. Three valid methods converged on 83K–94K incremental units against a 91.5K ground truth, with iROAS reported only when confidence intervals were available. End-to-end ownership from validity gating to business reporting layer.
<br>
<a href="https://github.com/amytakeuchi/Spillover-Aware-Geo-Incrementality-Experiment-Pipeline/tree/main">View code on Github</a>
<br>
Debugging write-up: <a href="https://medium.com/@a.takeuchi121/building-a-production-grade-geo-incrementality-system-how-synthetic-control-failed-by-18-and-bd497ebefa08"> Building a Production-Grade Geo Incrementality System: How Synthetic Control Failed by 18× — and What Fixed It →
</a>
<p align="center">
<img src="images/final_recommendation.png" width="800" title="ROI Analysis and Uncertainty">
</p>
<p align="center"><i>Summary of the Final Recommendation</i></p>

---
## Causal Price Elasticity Estimation — Double Machine Learning Pipeline
 Applied Double Machine Learning (DML) to 90,000+ weekly avocado price records across 54 U.S. markets to recover causally valid price elasticity and promotional demand multipliers — bypassing the endogeneity that invalidates standard regression for pricing decisions. Built the full two-stage pipeline from scratch: cross-fitted nuisance models with Fourier seasonality, geographic fixed effects, and channel-specific price controls, followed by OLS with HC3-robust standard errors and reliability flagging. A key debugging effort — identifying silent double-removal of geographic signal via the Frisch-Waugh-Lovell theorem — lifted nuisance R² by 94× (0.003 → 0.282), turning all six item × channel estimates from unreliable to green-flagged.
<br>
<a href="https://github.com/amytakeuchi/Avocado-Price-Elasticity-DML">View code on Github</a>
<br>
Debugging write-up: <a href="https://medium.com/@a.takeuchi121/debugging-a-broken-causal-pipeline-how-a-frisch-waugh-lovell-insight-lifted-r%C2%B2-from-0-003-to-0-282-88a1559341bf">Debugging a Broken Causal Pipeline: How a Frisch-Waugh-Lovell Insight Lifted R² from 0.003 to 0.282 →</a>
<p align="center">
<img src="images/price_elasticity.png" width="800" title="ROI Analysis and Uncertainty">
</p>
<p align="center"><i>Figure: Avocado Price Elasticity Estimation Results</i></p>
