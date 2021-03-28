# Midterm corrections


###  Data Management and DoKFold Function

```
from sklearn.datasets import fetch_california_housing  

data = fetch_california_housing()
X = data.data
X_names = data.feature_names
y = data.target

X = data.data
X_names = data.feature_names
X_df = pd.DataFrame(data = X, columns=X_names)
XMI = np.array(X_df.iloc[:,0:1])
y = data.target
y_names = data.target_names
y_df = pd.DataFrame(data = y, columns=y_names)

full_df = pd.concat([y_df, X_df], axis =1)

lin_reg = LinearRegression()

```


``` 
def DoKFold(model, X, y, k, standardize=False, random_state=146):
   
    from sklearn.model_selection import KFold
    
    if standardize:
        from sklearn.preprocessing import StandardScaler as SS
        ss = SS()

    kf = KFold(n_splits=k, shuffle=True, random_state=random_state)
    # kf = KFold(n_splits=k, shuffle=True)

    train_scores = []
    test_scores = []
    
    train_mse = []
    test_mse = []

    for idxTrain, idxTest in kf.split(X):
        Xtrain = X[idxTrain, :]
        Xtest = X[idxTest, :]
        ytrain = y[idxTrain]
        ytest = y[idxTest]

        if standardize:
            Xtrain = ss.fit_transform(Xtrain)
            Xtest = ss.transform(Xtest)

        model.fit(Xtrain, ytrain)

        train_scores.append(model.score(Xtrain, ytrain))
        test_scores.append(model.score(Xtest, ytest))
        
        ytrain_pred = model.predict(Xtrain)
        ytest_pred = model.predict(Xtest)
        
        train_mse.append(np.mean((ytrain - ytrain_pred)**2))
        test_mse.append(np.mean((ytest - ytest_pred)**2))

    return train_scores, test_scores, train_mse, test_mse

```




### Question 16: If the features are standardized, the correlations from the previous question do not change.

Prior to standardization to the correlation value between House Age for example and House Value was 0.105623.  
After standardizing the data the correlation value was -0.119034, thus there was a significant change.

```
from sklearn.preprocessing import StandardScaler as SS
ss = SS()
Xs = ss.fit_transform(X)
Xs_df = pd.DataFrame(X, columns = X_names)
Xsy_df = Xs_df.copy()
Xsy_df['y']=y
Xsy_df.corr()
```

#### Correction: 
The reason for the original error was that I standardized the entire data set using ss.fit_transform, including my target variable, thus I did not get this result.  

### Question 18: Linear Regression w a K-Fold

The results of the new linear regresstion with a k-fold were:  

Training: 0.60638
Testing: 0.60202

```
train_scores, test_scores, train_mse, test_mse = DoKFold(lin_reg,X,y,20,standardize = False)
print('Training: ' + format(np.mean(train_scores), '.5f'))
print('Testing: ' + format(np.mean(test_scores), '.5f'))
```

#### Correction: 
The reason for the original error was that I did not provide the DoKFold function with the the entire X feature set, only my XMI set (only feature was Med Income), for the midterm. This provided a lower R^2 value then the correct one. 

### Question 19: Ridge Regression 

The results of the new ridge regression were:  

Optimal alpha value: 25.80000
Training score for this value: 0.60627
Testing score for this value: 0.60201  

```
a_range = np.linspace(20, 30, 101)
k = 20

avg_tr_score=[]
avg_te_score=[]

for a in a_range:
    rid_reg = Ridge(alpha=a)
    train_scores,test_scores , train_mse, test_mse = DoKFold(rid_reg,X,y,k,standardize=True)
    avg_tr_score.append(np.mean(train_scores))
    avg_te_score.append(np.mean(test_scores))

idx = np.argmax(avg_te_score)
print('Optimal alpha value: ' + format(a_range[idx], '.5f'))
print('Training score for this value: ' + format(avg_tr_score[idx],'.5f'))
print('Testing score for this value: ' + format(avg_te_score[idx], '.5f'))
```

#### Correction:
The reason for this error was the same as #18, I used my XMI set instead of the whole X feature set. 

### Question 22: 	
Which of the above models estimates the smallest coefficient for the variable that is most correlated (in terms of the absolute value of the correlation coefficient) with the target?

Results:  
LinReg = 0.82961930428045, RidReg = 0.8288892465528181, LasReg = 0.8200140807502059

This shows that the Lasso Regression has the lowest coefficient for the median income variable.

```
lin_reg.fit(Xs,y)
rid_reg = Ridge(alpha = 25.8)
rid_reg.fit(Xs,y)
las_reg = Lasso(alpha = 0.00186)
las_reg.fit(Xs,y)
print('LinReg = ' + str(lin_reg.coef_[0])+ ', RidReg = ' + str(rid_reg.coef_[0])+ ', LasReg = ' + str(las_reg.coef_[0]))
```

#### Correction:
Here I was using the feature set which had not been standardized, which was giving me a very different set of coefficients for the MedInc variable.


### Question 23: MSE on the Ridge Regression for #19

Results for using MSE on the Ridge Regression:

Optimal alpha value: 26.10000
Training score for this value: 0.60627
Testing score for this value: 0.60201
MSE Training: 0.52427
MSE Testing: 0.52876

```
a_range = np.linspace(20, 30, 101)

k = 20

r_train = []
r_test = []
r_trn_mse =[]
r_tst_mse =  []

for a in a_range:
    rid_reg = Ridge(alpha=a)
    train_scores,test_scores , train_mse, test_mse = DoKFold(rid_reg,X,y,k,standardize=True)
   
    r_train.append(np.mean(train_scores))
    r_test.append(np.mean(test_scores))
    r_trn_mse.append(np.mean(train_mse))
    r_tst_mse.append(np.mean(test_mse))

idx = np.argmin(r_tst_mse)

print('Optimal alpha value: ' + format(a_range[idx], '.5f'))
print('Training score for this value: ' + format(r_train[idx],'.5f'))
print('Testing score for this value: ' + format(r_test[idx], '.5f'))
print('MSE Training: ' + format(r_trn_mse[idx], '.5f'))
print('MSE Testing: ' + format(r_tst_mse[idx], '.5f'))
```

#### Correction: 
1) I was still basing the determination for the alpha value on the R^2 coefficient scores  
2) I was taking the np.argmax of the ridge test w. MSE to determine the IDX variable, which was resulting in an incorrect alpha value.


