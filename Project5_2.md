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
|500|0.506|0.505|
|1000|0.501|0.499|
|5000|0.510|0.507| 



As we can see from the table, the 5000 tree run provided the most accurate results of all four runs.  

Additionally, tests were run to determine the minimum samples required to create the split in the internal nodes. For me, this was a value of 20, which produced a 
testing value of 0.502, very similar to the much larger value sizes.

## Re-classed wealthC target

Here we ran the same tests, however for the wealthC classes, 2 and 3 were merged together into one class (both went to class 3)

### KNN Classification

With the reclassed target, I got a testing value of 0.537 at 74 and then a value of 0.511 at 71 for the distance weighted KNN run.

![KNN2NS](https://user-images.githubusercontent.com/70855947/116033778-0821b580-a630-11eb-8592-3ca880f182b9.png)
![KNN2S](https://user-images.githubusercontent.com/70855947/116033788-1079f080-a630-11eb-954e-ce9753309ae0.png)

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

### Effects of re-classing the target:

Re-classing the target by merging classes 2 and 3 did not seem to have any major effects on the accuracy of the data based of the testing scores. This must be either because the differences in the features required to predict a value of 2 or 3 were significant enough that there was little error created in determining between values 2 and 3. A more likely possibility is that there simply were not enough observations for either 2 or 3 to make a large difference when merged. 


## Conclusion:

As far as which model is best suited for predicting wealth classes based off this data, my highest testing value of all was the KNN (no distance weights) without the reclasses data. This yielded a testing value of 0.561. This value only marginally better then many of the other models, which all seemed to perform consistanly decent in their testing values. 

