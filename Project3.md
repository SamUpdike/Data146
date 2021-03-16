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
#### Regressions with ZIP code data

With the zip codes appended from data the scores for the regressions were:

| KFold (10 folds) | Asking Price| Actual Price|
| :---             |    :----:   |         ---:|
| Training         | 0.281       | 0.339       |
| Testing          | 0.168       | 0.253       |


|Standardized KFold| Asking Price| Actual Price|
| :---             |    :----:   |         ---:|
| Training         | 0.281       | 0.340       |
| Testing          | 0.157       | 0.250       |


| Ridge Regression | Asking Price| Actual Price|
| :---             |    :----:   |         ---:|
| Training         | 0.280       | 0.338       |
| Testing          | 0.225       | 0.284       |


We can see clearly from these results that the inclusion of zip codes greatly improved the predictive power of each model, in all three instances from both data sets. Breaking it down further, the actual price models have a higher predictive power than their asking price counterparts. Dispite some experimentation with model parameters, I could not find significant differences between the models (Kfold, standardized, and a ridge regression) in training, however the ridge regression models seemed to have less over-fit models, as the difference between training and testing was the smallest for both datasets. One possible reason for this is certain zip codes could contain larger homes, yet not have a significant price changes, which could bring an issue with correlations between the feature variables.  

Regardless, all of these models are slightly over fit. In this case these models do a decent job of describing the data used to make the model (internal validity), however, when these models are applied to the greater Charleston housing market, they begin to suffer slightly in terms of accuracy (external validity).



### Question 6
#### Finally, consider the model that produced the best results. 

My best model is the ridge regression run on the actual price data with zip codes included. Again, this model is slightly overfit, and thus would suffer in terms of external validity. This could be due to the number of feature variables that are likely correleated with each other (bath and bedrooms, and squarefootage) used to create the model. If I were to create some models for Zillow, I feel that because the housing market must varry so greately between zip codes, it might be worth having a separate model run for each zip. Additionally, feature variables could be changed to include something like home age. This would not be nearly as correlated with squarefootage as the number of bed or baths, but could add valuble insight into the housing market.
