# Project 5.1

## WealthC as the target variable

### Linear Regression:  

#### Unstandardized features:
Training: 0.73597  
Testing: 0.73517  
MSE Training: 0.44256  
MSE Testing: 0.44356  

#### Standardized features:

Training: 0.73596  
Testing: 0.73517  
MSE Training: 0.44259  
MSE Testing: 0.44356  

Here we can see that standardizing the features the set did not have any meaningful impact on the training or testing R^2 results of the linear regression

### Ridge Regression:

Optimal alpha value: 2.22222222  
Training score for this value: 0.736  
Testing score for this value: 0.735  

![WCRidge](https://user-images.githubusercontent.com/70855947/117192326-9542d800-adaf-11eb-9a2f-b7527c177279.png)

### Lasso Regression:

Optimal alpha value: 0.000277
Training score for this value: 0.736
Testing score for this value: 0.735

![WCLasso](https://user-images.githubusercontent.com/70855947/117192400-ad1a5c00-adaf-11eb-849e-552bb06b5dcd.png)


## WealthI as the target variable

### Linear Regression:

#### Unstandardized features:  

Training: 0.82596  
Testing: 0.82513  
MSE Training: 1748904156.35407  
MSE Testing: 1753514701.91972  

#### Standardized Features:  

Training: 0.82594  
Testing: 0.82512  
MSE Training: 1749096642.20336  
MSE Testing: 1753585858.54931  


### Ridge Regression:

Optimal alpha value: 142.632  
Training score for this value: 0.826  
Testing score for this value: 0.825  

![WIRidge1](https://user-images.githubusercontent.com/70855947/117192865-35006600-adb0-11eb-9f04-e9d6fcd61c3d.png)


### Lasso Regression:

Optimal alpha value: 1.500  
Training score for this value: 0.826  
Testing score for this value: 0.825  

![WILasso](https://user-images.githubusercontent.com/70855947/117193028-65480480-adb0-11eb-99cd-fdee2eb3d867.png)


