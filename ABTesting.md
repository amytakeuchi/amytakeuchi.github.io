## Mobile Game Experimentation: Optimizing Progression Friction in Cookie Cats

### Executive Summary
I analyzed a large-scale A/B test (~90K users) to evaluate how progression friction (game “gates”) impacts player retention and engagement in a mobile game.

**Key result:**
- Moving the first gate from Level 30 → Level 40 decreases retention
- The effect is statistically significant for 7-day retention, a critical long-term engagement metric

Recommendation:
 → Keep the gate at Level 30 to maximize long-term player retention and downstream monetization potential

### 1. Business Context & Problem Framing
In free-to-play games like Cookie Cats, progression gates serve two key purposes:

- **Monetization lever** (in-app purchases to skip wait time)
- **Engagement control** (pacing player progression to avoid burnout)

However, gates introduce **friction**, which can negatively impact retention if poorly timed.

**Core Business Question**
*Where should the first gate be placed to optimize player retention and engagement?*

- **Control:** Gate at Level 30
- **Treatment:** Gate at Level 40

 <img src="images/Cookiecat_img.png?raw=true"/>

### 2. Experimental Design
- **Sample size:** 90,189 players (randomized)
- **Unit of analysis:** Player-level
- **Primary metrics:**
   - 1-day retention (short-term engagement)
   - 7-day retention (long-term engagement)
- **Secondary metric:**
Total game rounds played

This is a classic product tradeoff experiment:
*Reduce friction (later gate) vs. maintain structure (earlier gate)*

#### The dataset we are going to use:
The data was collected from 90,189 players who installed the game while the AB test was running.
The variables of the dataset are: 
- **'userid':** special number given to each player
- **'version':** the players were split into two groups: one called the control group, where players had a gate at level 30 (gate_30), and the other called the test group, where players had a gate at level 40 (gate_40).
- **'sum_gamerounds':** how many rounds of the game each player played in the first week after they installed the game.
- **'retention_1':** checked if players came back to play the game again after 1 day.
- **'retention_7':** checked if players came back after 7 days.

When a player got the game, they were randomly put into either the gate_30 or gate_40 group.

### 3. Hypothesis & Statistical Approach
- **Null hypothesis (H₀):** No difference in retention between Level 30 and Level 40
- **Alternative (H₁):** Retention differs between the two groups

Given the large sample size, I used a **two-proportion z-test** to evaluate differences in retention rates.
 <img src="images/Cookiecat_Hypothesis.png?raw=true"/>

Also, the alpha is defined as 0.05 and this indicates 95% confidence intervals. Since the dataset has a large number of entries with 90,189 rows, the size is enough to drive a precise z-test here, therefore, we are not sampling the data this time.

#### Z-Statistics:
I am going to perform Z-test to examine the statistical significance of the hypothesis here. Z-Statistics is a statistical measure that quantifies how far a data point is from the mean (average) of a dataset in terms of standard deviations. It is commonly used in hypothesis testing, particularly in the context of normal distribution.

 <img src="images/ztest.png?raw=true" width="200" height="150"/>
 
The Z-statistic represents the number of standard deviations a data point is from the mean. A positive Z-score indicates that the data point is above the mean, while a negative Z-score indicates that it is below the mean. The magnitude of the Z-score reflects how extreme or unusual the data point is in comparison to the rest of the data.

The p-value is the probability associated with the observed Z-statistic(s). A smaller p-value indicates stronger evidence against the null hypothesis. If the p-value is smaller than a predetermined significance level (e.g., 0.05), you may reject the null hypothesis in favor of the alternative hypothesis.

### 4. Summary Statistics and Visualization
 <img src="images/Cookiecat_viz.png?raw=true"/>
 The summary statistics of the 'sum_gamerounds' of the dataset were as follows:
  <img src="images/Cookiecat_sumstats.png?raw=true"/>

After exploring the data, there were no missing values but some outliers in the dataset. 
The retention rates after 1 day are 44.8% (Gate 30) vs 44.2% (Gate 40) while 7-day retention rates are 19% (Gate 30) vs 18.2% for (Gate 40). Putting the date at lv.30 has slightly higher retention on the both day(s).

By plotting the total rounds of games that the players in both groups had gone through, it was found that fewer players were retained in the game as the game rounds progressed. also, 3994 players never played the game after installing the game(!).

### 5. Hypothesis Testing & Key Finding
 <img src="images/Cookiecat_results.png?raw=true"/>
 Retention Impact
| Retention Impact | Metric | Gate @ Level 30 | Gate @ Level 40 | Impact |
| :--- | :--- | :--- | :--- | :--- |
| 1-day retention | Retention Rate | 44.8% | 44.2% | Slight decline |
| 7-day retention | Retention Rate | 19.0% | 18.2% | Meaningful decline |

**Statistical Significance**
- 1-day retention:
  - Not statistically significant at α = 0.05
  - Directionally negative
- 7-day retention:
  - Statistically significant decrease
  - Strong evidence that delaying the gate harms retention

### 6. Interpretation (What This Means for the Product)/Business recommendations
**Let's go back to the business question**: does moving the first gate in Cookie Cats from level 30 to level 40 affect player retention and a number of rounds? This time, we set the retention rate as the primary metric to assess the problem.
<br/>
At first glance, delaying the gate (Level 40) seems beneficial:
*“Let players enjoy more gameplay before friction”*
However, the data suggests the opposite:

**Key Insight**
- *Early gating (Level 30) improves long-term retention*

**Why this likely happens:**
- Introduces structured pacing early
- Reinforces habit formation loops
- Prevents content exhaustion / burnout
- Creates intentional breaks, increasing return probability

This highlights an important product principle:
*Not all friction is bad — well-timed friction can improve retention*

**Business Recommendation**
* Ship Decision: Keep the gate at Level 30

**Expected Impact**
- Higher 7-day retention (statistically validated)
- Stronger player lifecycle value (LTV)
- Improved monetization opportunities downstream

**Additional Insights**
- ~4.4% of users never engaged after install → onboarding opportunity
- Engagement drops sharply as rounds increase → typical funnel decay
- Heavy-tailed distribution of game rounds → presence of highly engaged “power users”
