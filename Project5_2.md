# Project 5.2

## Original wealthC as the target variable

### KNN Classification:

Here we ran two different KNNs, one without using distance as a weight and one with.  

Without distance as a weight I got a max testing score of 0.561 at a value of 55.  
![KNN1NS](https://user-images.githubusercontent.com/70855947/116032893-749bb500-a62e-11eb-8ffa-b591cf928459.png)  


With distance as a weight I got a max testing score of 0.512 at a value of 76.
![KNN1S](https://user-images.githubusercontent.com/70855947/116032930-83826780-a62e-11eb-8347-b8d2b4ccabca.png)


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

## Re-classed wealthC target

Here we ran the same tests, however for the wealthC classes, 2 and 3 were merged together into one class (both went to class 3)

### KNN Classification

With the reclassed target, I got a testing value of 0.537 at 74 and then a value of 0.511 at 71 for the distance weighted KNN run.

### Logistic Regression

Here the values were 0.551 for training and 0.549 for testing.

### Random Forest

Testing Values:
|Number of Trees| Scaled | Unscaled|
|-|-|-|
|100|0.516|0.486|
|500|0.510|0.492|
|1000|0.509|0.493|
|5000|0.507|0.489| 


