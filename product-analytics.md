[← Go back to main page](index.md)

# Product & Marketing analytics
Understand users, retention, marketing performance, and experimentation.

---

## Featured Writing

### Before Metrics: How Product Analysts Structure Ambiguous Problems in Real Product Decisions

A framework for approaching ambiguous product problems before jumping into metrics — starting with the decision, defining the user behavior that matters, and connecting analysis to an actionable product decision.

[Read the Medium article →](https://medium.com/@a.takeuchi121/before-metrics-how-product-analysts-structure-ambiguous-problems-in-real-product-decisions-fe3e388df297)

---

### Featured Projects
---
## Marketing Funnel Analytics Dashboard
Delivered self-service Tableau dashboard analyzing seller acquisition funnel across 8K MQLs, 10 channels, and 25+ reps; uncovered social channel converting at half the funnel average and identified CRM instrumentation gap leaving 89.5% of lead drop-off unattributable by stage.
<br>
<a href="https://public.tableau.com/app/profile/amy7438/viz/OlistMarketingFunnelDashboard/Home">View dashboard on Tableau Public</a>
<p align="center">
<img src="images/Marketing_Dashboard.png" width="800" title="Interactive Dashboard covering Funnel Analysis, Cohort Analysis, Channel/Segment, Sales Rep performances, & Data Quality">
</p>

---
## Product Analytics: Customer Retention & Behavioral Segmentation Analytics
Analyzed 300K+ cardholder transactions using RFM, survival analysis, and clustering to diagnose churn, model reactivation timing, and segment customers for targeted retention strategy.
<br>
<a href="https://github.com/amytakeuchi/Fintech-Product-Analytics/blob/main/README.md">View code on Github</a>
<br>
<p align="center">
<img src="images/product_analytics.png" title="Clustering & Survival by cluster/At-Risk Revenue by Tier/Cohort dropoffs">
 </p>
 
---
## Mobile Game A/B Testing
Designed an end-to-end hypothesis testing framework on 90,000+ player records to determine whether a monetisation gate at Level 30 vs. 40 maximises Day-1 and Day-7 retention for a top-grossing mobile puzzle game. Applied a two-proportion z-test with Bonferroni correction, randomisation validity checks, and bootstrap confidence intervals — grounded in behavioral economics (hedonic adaptation). Gate 30 delivered a statistically significant +18.2% lift in Day-7 retention (p < 0.01, 95% CI excludes zero), yielding a clear product recommendation tied directly to long-term LTV.

### [Project Summary Page](/ABTesting)
<a href="https://github.com/amytakeuchi/AB-Testing/tree/main">View code on Github</a>
<br><br>
 <img src="images/Cookiecat_cover.png?raw=true"/>

 ---
## Bayesian Marketing Mix Modeling — Geo-Experiment Calibration
Built a production-grade Bayesian MMM in PyMC 5.0 on 156 weeks of spend data, featuring a custom fusion layer that uses Bayesian precision weighting to calibrate observational priors with experimental evidence — preventing over-correction from high-variance geo-tests. A trend component addition improved model R² by 58% (0.479 → 0.755), while geo-experiment calibration showed 0% R² change, redirecting a $500K experimentation budget toward data quality instead. The model identified TV at 85% saturation and, using 94% HDI uncertainty quantification, produced a risk-adjusted recommendation to reallocate spend toward high-ROI Search and YouTube.

<p align="center">
<img src="images/04_roi_by_channel_.png" width="800" title="ROI Analysis and Uncertainty">
</p>
<p align="center"><i>Figure: ROI by channel with 94% HDI and Posterior Distributions.</i></p>

<a href="https://github.com/amytakeuchi/Bayesian-MMM-Calibrated-with-Incrementality/blob/main/README.md#bayesian-marketing-mix-model-with-geo-experiment-calibration">View code on Github</a> <br>
Debugging write-up: <a href="https://medium.com/@a.takeuchi121/bayesian-mmm-case-study-why-model-specification-matters-more-than-you-think-e83408f79abb"> Bayesian MMM case study: Why Model Specification Matters More Than You Think →
 
---

## AI-Powered Experiment Readout Generator
Built an automation pipeline turning raw A/B test results into stakeholder-ready decision readouts, routing each experiment to the correct significance test by metric type — two-proportion z-test for conversion metrics (click-through, retention, open rate), Welch's t-test for continuous metrics (order value, session duration) — then passing lift, confidence interval, and p-value to Claude to draft a plain-English summary and recommendation (ship / hold / kill). Includes inconclusive cases alongside clear wins to confirm the tool reasons about significance rather than defaulting to "ship it," with graceful degradation (template fallback if the LLM call fails) for unattended reliability.
<br>
<a href="https://github.com/amytakeuchi/experiment-readout-generator">View code on Github</a>
<br>
<p align="center">
<img src="images/ai_continuous.png" width="800" title="LLM-generated Experiment Summary">
 </p>
