
Statistical Analysis on Data from Gallup World Research 

# Introduction***

This dataset from Kaggle is a small portion of a report from Gallup World Research on Wolrd Happiness in 2019 containing 
scores from 156 countries measuring 7 key variables. Each country had at least 1000 observations which were then computed into national averages for each variable. Missing values for this dataset were filled with a regression value based on the previous 3 years of data. 

---

# Variables 

Four out of the 7 variables are directly from the Gallup World Poll including: Happiness Score, Social Support, Freedom of Life Choices, and Perceptions of Corruption <br>
The remaining 3 out of 7 variables were collected outside of the Poll. GDP was calculated using Purchasing Power Parity (PPP) at 2017 international dollar prices. Life Expectancy was retrieved from the World Health Organization (WHO) and Generosity was calculated as the residual of the regression between the national average response of a designated question to GDP Per Capita <br>

# Analysis

---

## Residuals 

Utilizing Standardized, Studentized, and RStudent residuals, the two outlying countries were identified as Rwanda and Botswana (index 148 and 152). Removing these two countries would improve the residual plot but not improve the model; furthermore, there was an insufficient amount of non-statistical reasons to remove Rwanda and Botswana from the model. As such, the model proceeded with no removals of countries. The residual plot and histogram followed a random distribution and normal distribution indicating no transformation is necessary. 
<br> 

## Variable Selection 

Using faceted jitter plots from ggplot, we identified two regressors that did not follow a linear trend- Generosity and Perception of Corruption. After conducting forward and backward stepwise selection from the olsrr and MASS packages in R, and ols_step_all_possible() we were able to find all possible models and their corresponding adjusted R-squared and Mallow's CP values. This left two possible models, one with the lowest Mallow's CP and one with the highest adjusted R-squared value. One model included Generosity, and one without. After conducting forward and backward stepwise selection, we concluded that the model without Generosity was the best model. 
<br>

## Final Analysis 

Looking at the median scores to avoid outliers influencing the model too much, we identified Europe and North America to be the generally happiest regions in the world with Africa being the least happy by a significant margin. After using ggwordcloud to create a word cloud of the top 25 happiest countries, European countries dominated the list as happiest countries, as we had predicted. From our final model, we can tell that Freedom to Make Life Choices is the most influential variable in contributing to Happiness Score at an increase of 0.3479 units in Happiness Score per 1 unit increase in Freedom to Make Life Choices. Furthermore, Perception of Corruption was the least influential variable at 0.153 increase in Happiness Score per increase in Perception of Corruption 
