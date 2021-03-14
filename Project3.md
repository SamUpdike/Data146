# Project 3

### Question 1
#### Linear regression model with price as a target and beds, baths and area (in square feet) as features.
This model performed poorly. With a training mean of 0.019 and a testing mean of -0.067 (model was run mulitple times and test score varied wildly). This was done with ten folds for the partition. Looking at these figures, I can assume that a combination of no. of beds, baths or the squarefootage of a home are not good indicators of an asking price.   



### Question 2 
#### Standardized features with a linear regression model:
With this model standardized, using StandardScalar and 10 folds, the model also performed poorly with: training at 0.020 and testing at -0.038. Because these scores are also terrible, we can assume that beds, baths, and square footage are not good indicators of price, and the difference in scales of these variables is not the cause of a poor score.

### Question 3
#### Ridge regression model:
The ridge regression scores were poor and similar to the standardized ones with a training score of 0.019 and a testing of -0.034. This regression also used standardized data. This result means that even if beds, baths, and squarefootage are highly correlated, this is not the reason for the lack of correlation between out features and target. 

### Question 4
#### Actual sales prices with the three previous model types/specifications:
With the actual sale prices the scores for the regressions were:
* KFold (10 folds) and OLS regression:
  * Training: 0.004
  * Testing: -0.033
* Standardized KFold:
  * Training: 0.004
  * Testing: -0.062
* Standardized Ridge Regression:
  * Training: 0.004
  * Testing: -0.055

These models did not perform any better than the data with the asking prices. Again, we can assume that the number of baths, bedrooms, and squarefootage are not precise in determining either asking or actual home prices in Charleston.  


### Question 5
#### Go back and also add the variables that indicate the zip code where each individual home is located within Charleston County, South Carolina. Train and test each of the three previous model types/specifications. What was the predictive power of each model? Interpret and assess your output.

### Question 6
#### Finally, consider the model that produced the best results. Would you estimate this model as being overfit or underfit? If you were working for Zillow as their chief data scientist, what action would you recommend in order to improve the predictive power of the model that produced your best results from the approximately 700 observations (716 asking / 660 actual)?
