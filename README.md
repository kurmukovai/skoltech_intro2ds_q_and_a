# skoltech_intro2ds_q_and_a
Answers to questions from Q&amp;A live-sessions


# Q&A-1 04.10.2021 
### 1. How zip works?
zip allows you to combine containers of the same length into a container of pairs, so instead of

```
for i in range(len(container)):
  x = container1[i]
  y = container2[i]
  print(x, y)
```
you could write 
```
for x, y in zip(container1, container2):
  print(x, y)
```
You could zip arbitrary number of containers:
```
for x, y, z in zip(container1, container2, container3):
    print(x, y, z)
```
### 2. What `fit_intercept` stands for?

In linear model we look for a solution to the equation Y=w * X + b,  here w is a vector of model parameters: it attaches a single weight to every feature of the X, however b does not corresponds to any features of the X, it controls where the regression line intersects the OY axis. If b is equal to 0, then the line goes through the origin (0, 0). Thus, fit_intercept, controls whether you want to fit not only w but also b. Sometimes from domain knowledge you don't want to fit b, and enforce the regression solution to go through the origin, but typically you do want to also fit b (that's why by default, fit_intercept=True).

### 3. What are the alternatives to sklearn.linear_model?
  - Normal equation  
  - scipy, statsmodels
  - Implement a gradient descent -> numpy, pytorch, tensorflow

# Q&A-2 05.10.2021 TODO: add answers

### 1. Why normalize the data
X: n obs x m features

-  X* = (X - mean(X)) / std(X) -> mean(X*) = 0, std(X*) = 1 Z-scoring # Standard Normal Distribution = N(0, 1)
-  Robust normalization 
-  min-max scoring: X* = (X - min(X)) / (max(X) - min(X))  min(X)=0, max(X)=1

Linear models, will typically benefit from some kind of data normalization: Linear Reg, Logistic Reg, SVM, KNN 
Tree based models, in most cases, do not affected by a normalization: Decision trees, Random Forest, Gradient boosting trees


### 2. What is reg.intercept_ corresponds to?
### 3. Why intercept in linear model is always a number and not a vector?
### 4. Why should we impute instead of dropping?
