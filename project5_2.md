# Project 5.2

## Original wealthC as the target variable

### KNN Classification:

Here we ran two different KNNs, one without using distance as a weight and one with.  

Without distance as a weight I got a max testing score of 0.561 at an alpha value of 55.  

With distance as a weight I got a max testing score of 0.512 at an alpha value of 76.

Here I prefer the model without distance, as it performs marginally better, but is much less overfit than the other.

### Logistic Regression:

My logistic regression gave me a training value of 0.553 and a testing value of 0.547. This is a very close score to the KNN models, but is less overfit than the KNNs. 

### Random Forest Models

When running both random forest models, scaled and unscaled, I got similar results to the previous two methods. Additionally, there was little difference here between
the scaled and unscaled features. 

Testing Values:
|Number of Trees| Scaled | Unscaled|
|-|-|-|
|100|0.499|0.497|
|500|0.505|0.506|
|1000|0.499|0.501|
|5000|0.507|0.510|

As we can see from the table, the 5000 tree run provided the most accurate results of all four runs.  

Additionally, tests were run to determine the minimum samples required to create the split in the internal nodes. For me, this was a value of 20, which produced a 
testing value of 0.502, very similar to the much larger value sizes.

