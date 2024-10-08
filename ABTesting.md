## Mobile Games A/B Testing - Cookie Cats

**Project description:** Project summary: Cookie Cats, a popular mobile puzzle game, imposes a ‘gate’, where players are forced to wait a significant amount of time or make an in-app purchase to progress, as players continue to progress the game. The A/B test was conducted to examine whether the ‘gate’ is better to be deployed in Level. 30 or Level. 40. 

### 1. Problem Statement

Cookie Cats is a hugely popular mobile puzzle game developed by Tactile Entertainment. It's a classic "connect three"--style puzzle game where the player must connect tiles of the same color to clear the board and win the level. It also features singing cats.
 <img src="images/Cookiecat_img.png?raw=true"/>

As players advance in the game, they'll encounter occasional gates that require a significant amount of waiting timeor making in-app purchases to proceed, boosting purchases and providing players a necessary pause, potentially enhancing their enjoyment and prolonging engagement. This time, the company wants to know where should they impose the first gate to the players to retain more users. They will initially divide players into two groups: one that encounters the gate at level 30 and the other at level 40. Their specific focus will be on evaluating the impact of this level difference on player retention. 

**The business question:** Is there an influence on player retention and the number of rounds played when we shift the gate in Cookie Cats from level 30 to level 40? In this analysis, we prioritize evaluating the issue based on the retention rate as the primary metric.

#### The dataset we are going to use:
The data was collected from 90,189 players who installed the game while the AB test was running.
The variables of the dataset are: 
- **'userid':** special number given to each player
- **'version':** the players were split into two groups: one called the control group, where players had a gate at level 30 (gate_30), and the other called the test group, where players had a gate at level 40 (gate_40).
- **'sum_gamerounds':** how many rounds of the game each player played in the first week after they installed the game.
- **'retention_1':** checked if players came back to play the game again after 1 day.
- **'retention_7':** checked if players came back after 7 days.

When a player got the game, they were randomly put into either the gate_30 or gate_40 group.

### 2. Designing the Hypothesis
 <img src="images/Cookiecat_Hypothesis.png?raw=true"/>

The key metric we are going to take into account is the retention rate. The experiment records the retention after 1 day and 7 days respectively and the retention rate for both will be evaluated.

This time, we are going to form the null hypothesis as H1: p0 = p1, which means that the control group, the group of players who encounter gates at Lv. 30, is not significantly different from the treatment group, th players meet the gate at Lv. 40. On the other hand, the alternative hypothesis is defined as H1: p0 =! p1 which equals that the control group is significantly different from the treatment group. 

Also, the alpha is defined as 0.05 and this indicates 95% confidence intervals.
Since the dataset has a large number of entries with 90,189 rows, the size is enough to drive a precise z-test here, therefore, we are not sampling the data this time.

#### Z-Statistics:
I am going to perform Z-test to examine the statistical significance of the hypothesis here. Z-Statistics is a statistical measure that quantifies how far a data point is from the mean (average) of a dataset in terms of standard deviations. It is commonly used in hypothesis testing, particularly in the context of normal distribution.

 <img src="images/ztest.png?raw=true" width="200" height="150"/>
 
The Z-statistic represents the number of standard deviations a data point is from the mean. A positive Z-score indicates that the data point is above the mean, while a negative Z-score indicates that it is below the mean. The magnitude of the Z-score reflects how extreme or unusual the data point is in comparison to the rest of the data.

The p-value is the probability associated with the observed Z-statistic(s). A smaller p-value indicates stronger evidence against the null hypothesis. If the p-value is smaller than a predetermined significance level (e.g., 0.05), you may reject the null hypothesis in favor of the alternative hypothesis.

### 3. Summary Statistics and Visualization
 <img src="images/Cookiecat_viz.png?raw=true"/>
 The summary statistics of the 'sum_gamerounds' of the dataset were as follows:
  <img src="images/Cookiecat_sumstats.png?raw=true"/>

After exploring the data, there were no missing values but some outliers in the dataset. 
The retention rates after 1 day are 44.8% (Gate 30) vs 44.2% (Gate 40) while 7-day retention rates are 19% (Gate 30) vs 18.2% for (Gate 40). Putting the date at lv.30 has slightly higher retention on the both day(s).

By plotting the total rounds of games that the players in both groups had gone through, it was found that fewer players were retained in the game as the game rounds progressed. also, 3994 players never played the game after installing the game(!).

### 4. Hypothesis Testing
 <img src="images/Cookiecat_results.png?raw=true"/>
Since we have a large number of dataset here, we can use z-test to compute the p-value and draw results.

As a result of z-test for 1-day retention data, following was found. The z statistic measures how many standard deviations the sample mean is away from the hypothesized population mean under the null hypothesis. z statistic here is positive and indicates that the score is higher than the mean. p-value is above the predefined significance level of 0.005 but is pretty close to it. The null is not strictly rejected but it would be better to put the gate in the lv 30.

 For the 7-days retention rate, the p-value is way below the 0.05 significance level and the null is clearly rejected. Also, z statistics is larger than 1 day retention, indicating a larger standard deviation away from the mean. The gate should stay in the Lv 30 to retain the users for 7 days.

### 5. Evaluate the results/Business recommendations
**Let's go back to the business question**: does moving the first gate in Cookie Cats from level 30 to level 40 affect player retention and a number of rounds? This time, we set the retention rate as the primary metric to assess the problem.

By performing z-test, the null hypothesis, which defined as both groups do not have significant differences in retention rate, was rejected, particularly for 7-day retention rate. While the 1-day retention rate does not have a significant difference between both level, the significance level was not so far from the threshold of 0.05 and not strongly denied. The 7-day retention was clearly higher for the lv 30 group with a retention rate between 18.7 - 19.4% for the control group with a 95% confidence level.

**The business suggestion that can be made from this result is**: the gate should stay in Lv. 30 to retain the customer for both 1 day and 7 days, especially for the 7-day retention rates.

Additional insights found from examining the data were:
- There were no missing values but some outliers in the dataset.
- 3994 players never played the game after installing.
- As the game rounds progress, fewer players are retained in the game



