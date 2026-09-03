[Go back to main page →](index.md)
# AI

Build AI-powered analytics workflows.

### Featured Projects
## AI-Powered Experiment Readout Generator
Built an automation pipeline turning raw A/B test results into stakeholder-ready decision readouts, routing each experiment to the correct significance test by metric type — two-proportion z-test for conversion metrics (click-through, retention, open rate), Welch's t-test for continuous metrics (order value, session duration) — then passing lift, confidence interval, and p-value to Claude to draft a plain-English summary and recommendation (ship / hold / kill). Includes inconclusive cases alongside clear wins to confirm the tool reasons about significance rather than defaulting to "ship it," with graceful degradation (template fallback if the LLM call fails) for unattended reliability.
<br>
<a href="https://github.com/amytakeuchi/experiment-readout-generator">View code on Github</a>
<br>
<p align="center">
<img src="images/ai_continuous.png" width="800" title="LLM-generated Experiment Summary">
 </p>

