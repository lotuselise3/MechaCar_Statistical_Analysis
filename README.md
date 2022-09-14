# MechaCar_Statistical_Analysis

## Overview
- Load, clean up, and reshape datasets using tidyverse in R.
- Visualize datasets with basic plots such as line, bar, and scatter plots using ggplot2.
- Generate and interpret more complex plots such as boxplots and heatmaps using ggplot2.
- Plot and identify distribution characteristics of a given dataset.
- Formulate null and alternative hypothesis tests for a given data problem.
- Implement and evaluate simple linear regression and multiple linear regression models for a given dataset.
- Implement and evaluate the one-sample t-Tests, two-sample t-Tests, and analysis of variance (ANOVA) models for a given dataset.
- Implement and evaluate a chi-squared test for a given dataset.
- Identify key characteristics of A/B and A/A testing.
- Determine the most appropriate statistical test for a given hypothesis and dataset.
<img width="1406" alt="AutoRUs" src="https://user-images.githubusercontent.com/68654746/190219800-317c4278-811f-45f1-8c6b-d2ebf62a9b60.png">

## Purpose
AutosRUs’ newest prototype, the MechaCar, is suffering from production troubles that are blocking the manufacturing team’s progress. In this challenge, you’ll help AutosRUs review the production data for insights that may help the manufacturing team. 

## Objectives: 
- Perform multiple linear regression analysis to identify which variables in the dataset predict the mpg of MechaCar prototypes
- Collect summary statistics on the pounds per square inch (PSI) of the suspension coils from the manufacturing lots
- Run t-tests to determine if the manufacturing lots are statistically different from the mean population
- Design a statistical study to compare vehicle performance of the MechaCar vehicles against vehicles from other manufacturers. For each statistical analysis, you’ll write a summary interpretation of the findings

### Deliverable 1: Linear Regression to Predict MPG
*The MechaCar_mpg.csv dataset contains mpg test results for 50 prototype MechaCars. The MechaCar prototypes were produced using multiple design specifications to identify ideal vehicle performance. Multiple metrics, such as vehicle length, vehicle weight, spoiler angle, drivetrain, and ground clearance, were collected for each vehicle. Using your knowledge of R, you’ll design a linear model that predicts the mpg of MechaCar prototypes using several variables from the MechaCar_mpg.csv file.*

![Del1](https://user-images.githubusercontent.com/68654746/190219733-9dfc4935-c074-472f-a24b-aab46d57bbde.jpg)
**QUICK LOOK**  
A brief summary of the linear regression can help determine the quality and spread of the MechaCar dataset.  The distribution of residuals shows a normal bell curve, and thus normal data, where the absolute value of the min and max are comparable |-19.47|~|18.58| and the median -.07 is close to zero.
Null Hypothesis: The slope of the linear model is zero. 
Alternative Hypothesis: The slope of the linear model is not zero. 

### mpg = 6.267*vehicle.length + 0.001245*vehicle.weight +  0.06877*spoiler.angle + 3.546*ground.clearance + -3.411*AWD + -104.0

*Compose a short interpretation of the multiple linear regression results*

**1. Which variables/coefficients provided a non-random amount of variance to the mpg values in the dataset?**

The vehicle length and ground clearance are both statistically likely to provide non-random amounts of variance to the model. A 95% level of confidence was predetermined, so the p-value should be compared to alpha of .05 level of significance to verify if a coefficient is statistically significant. 
- mpg: 0 < .05, statistically significant, non-random amount of variance
- vehicle length: 0 < .05, statistically significant, non-random amount of variance
- ground clearance: 0 > .05 statistically significant, non-random amount of variance

In conclusion, the vehicle length and vehicle ground clearance have a significant impact on miles per gallon on the MechaCar prototypes. Conversely, the vehicle weight, spoiler angle, and All Wheel Drive (AWD) all have p-Values that indicate a random or insignificant amount of variance with the dataset. However, the statistical significance of the intercept means that there are other variables and factors contributing to the variation in mpg and have not been included in our linear regression model. To better predict the mpg of MechaCar, additional variables such as horsepower should be collected and use in our analysis. 

**2. Is the slope of the linear model considered to be zero? Why or why not?**

Because the p-Value of 5.35e-11 is much smaller than the assumed significance level of 0.05%, that is evidence that the slope of this linear model is not zero.

The null hypothesis states that if there is no significant linear relationship, then each dependent value would be determined by random chance and our linear model would have a slope of zero.  We can assess the significance of the linear relationship between variables by comparing the p-value to the significance level. A p-value illustrates the likelihood that a similar result will be observed if the data is tested again and the significance level is the predetermined cut off for the hypothesis test. In our MPG regression analysis, the p-value is much less than our significance level of 0.05%, indicating that there is sufficient evidence to reject the null hypothesis and conclude that the slope of our linear model is not zero. 

**3. Does this linear model predict mpg of MechaCar prototypes effectively? Why or why not?**

The r-squared value (coefficient of determination) represents how well the linear model approximates future observations and data points, where the closer the r-squared value is to 1, the stronger the correlation. 

Our MechaCar summary statistics has a r-squared value of 0.7149, meaning roughly 71.49% of all mpg predictions will be accurate when using this linear model. Although the model performs sufficiently well with the current dataset, there may be other missing variables from our analysis that may be contributing to the variation in the mpg. Suggesting additional variables might be impactful to improve our MechaCar performance, our multiple regression model does predict mpg of MechaCar prototypes relatively effectively. 

### Deliverable 2: Summary Statistics on Suspension Coils
*The MechaCar Suspension_Coil.csv dataset contains the results from multiple production lots. In this dataset, the weight capacities of multiple suspension coils were tested to determine if the manufacturing process is consistent across production lots.*

**Manufacturing Lot Summary** *(The suspension coil’s PSI continuous variable across all manufacturing lots)*
![Del2_total_summary](https://user-images.githubusercontent.com/68654746/190235783-4593c965-ea05-49c3-a820-b6ec092609e1.jpg)

**Summary by Manufacturing Lot Number**  *(The following PSI metrics for each lot: mean, median, variance, and standard deviation)*
![Del2_lot_summary](https://user-images.githubusercontent.com/68654746/190235796-7f1f8508-ad63-4085-bcca-4148a5e213fe.jpg)

**QUICK LOOK**
Based on the above summary statistics, the Suspension Coils dataset is normally distributed, where the mean and median are close in value, 1498.78 PSI and 1500 PSI respectively. Additionally, the dataset has a small variance of 62.294 PSI, indicating that data points tend to be close to the mean. Another good description of the spread while staying consistent with the unit of measurement is taking the square root of the variance, or also known as the standard deviation. Std_Dev_PSI is 7.893, which also proves that the data points tend to be closer to the mean and have a small spread.

**1. The design specifications for the MechaCar suspension coils dictate that the variance of the suspension coils must not exceed 100 pounds per square inch. Does the current manufacturing data meet this design specification for all manufacturing lots in total and each lot individually? Why or why not?**

Yes, because the variance for all manufacturing lots is 62 < 100, the current data is within the expected design specifications of under 100 PSI. However, when reviewing the data by specific lot number, Lot 3 has a high variance of 170 > 100 and does not meet the design specifications. Whereas, Lot 1 and Lot 2 have significantly lower variance, 1 and 7 respectively. The total across all manufacturing lot meets the design specifications, however, Lot 3 is disproportionately causing the variance at the full lot level.

![Del2_total_boxplot](https://user-images.githubusercontent.com/68654746/190246317-56fb1a1e-b8ed-40f2-9b07-15613eed9438.jpg)

<img width="543" alt="del2_boxplot" src="https://user-images.githubusercontent.com/68654746/190242244-912a58d4-6d7e-4bf9-acea-2c1c6ea5c91f.png">

### Deliverable 3: T-Test on Suspension Coils
*Using your knowledge of R, perform t-tests to determine if all manufacturing lots and each lot individually are statistically different from the population mean of 1,500 pounds per square inch.*

**QUICK LOOK**
A one-sample t-test is used to assert if there is a statistical difference between the means of a sample dataset and the population dataset. Therefore, a one-sample t-test was performed if the suspension coil’s pounds-per-inch (PSI) results are statistically different from the mean population results of 1,500 PSI. 

**T-test for all Lots**

![Del3_t_test](https://user-images.githubusercontent.com/68654746/190247522-d12998d3-affc-4a17-b892-603a751796bc.jpg)

All Manufacturing Lots: p-value = 0.6028, alpha = .05
As analayzed in the summary statistics above, the true mean of the sample is 1498.78 and falls within the 95% confidence interval. However, a p-Value of 0.603 is greater than the common significance level of 0.05, so there is not enough statistically evidence to reject the null hypothesis. The mean of all manufacturing lots is statistically similar to the presumed population mean of 1500 and normality can be assumed.

**T-test for Lot 1**

![Del3_lot1](https://user-images.githubusercontent.com/68654746/190251153-05ec4c51-5c68-44a8-8b2c-583365afd4f7.jpg)

Lot 1: p-value = 1, alpha = .05
1 > .05, which means Lot 1 is not statistically significant from the normal distribution and normality can be assumed. The mean falls within the 95% confidence interval.

**T-test for Lot 2**

![Del3_lot2](https://user-images.githubusercontent.com/68654746/190256594-87ee450f-5dbe-4ad1-8840-6f10794da872.jpg)

Lot 2: p-value = .6072, alpha = .05

.60 > .05, which means Lot 2 is not statistically significant from the normal distribution and normality can be assumed. The mean falls within the 95% confidence interval.

**T-test for Lot 3**

![Del3_lot3](https://user-images.githubusercontent.com/68654746/190256869-7bd76049-72bc-49b3-a5a3-ee304a5ca3f7.jpg)

Lot 3: p-value = .04168, alpha = .05
.04 < .05, which means it is statistically significant from the normal distribution and normality cannot be assumed. However, the mean falls within the 95% confidence interval.

Because the overall manufacturing, Lot 1, and Lot 2 all show a normal distribution, there is not sufficient evidence to reject the null hypothesis, which means the sample mean and population mean are statistically similar.

### Deliverable 4: Design a Study Comparing the MechaCar to the Competition

*Write a short description of a statistical study that can quantify how the MechaCar performs against the competition. In your study design, think critically about what metrics would be of interest to a consumer: for a few examples, cost, city or highway fuel efficiency, horse power, maintenance cost, or safety rating.*


**1. What metric or metrics are you going to test?**
We may collect the following metrics from comparable models across all major manufacturers:
- safety rating
- engine (Electric, Hybrid, Gasoline / Conventional)
- horsepower
- highway fuel efficiency
- current selling price **[Dependent Variable]**
- resale value
- average annual cost of ownership (maintenance costs)

**2. What is the null hypothesis or alternative hypothesis?**
Null hypothesis (H0): MechaCar is priced correctly based on its performance of key factors for its genre
Alternative hypothesis (H1): MechaCar is NOT priced correctly based on performance of key factors for its genre.

**3. What statistical test would you use to test the hypothesis? And why?**
I would use a multiple linear regression statistical summary because it would best show how the variables impact and have the highest correlation/predictability with the list selling price of MechaCar compared to their competitors.

**4. What data is needed to run the statistical test?**
A random sample of n > 30 for MechaCar and their competitor with comparable models across several different manufacturers over the last 3 years.
