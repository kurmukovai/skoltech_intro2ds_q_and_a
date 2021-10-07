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

# Q&A-2 05.10.2021

### 1. Why do we normalize the data?

First, when we speak about data normalization, we typically mean feature-wise normalization, e.g. standard or z-scoring, min-max scaling:
  - X* = (X - mean(X)) / std(X) -> mean(X*) = 0, std(X*) = 1
  - min-max scoring: X* = (X - min(X)) / (max(X) - min(X))  min(X*)=0, max(X*)=1

Second, not all ML models will benefit from data normalization:
  - tree-based methods (*most likely*) will not be affected: Decision trees, Random Forest, Gradient boosting trees
  - distance-based methods might benefit from data normalization, e.g. K nearest neighbours
  - linear models, will *most likely* benefit from data normalization: Linear/Logistic regression, Support Vector Machine

the latter is due to the fact that gradient descent-like methods are much more stable and converge faster to good solutions if data are standartized.
### 2. What is `LinearRegression().intercept_` corresponds to?
  
This is `b` in Y = A * X + b, and A is stored in `LinearRegression().coef_`, see https://scikit-learn.org/stable/modules/generated/sklearn.linear_model.LinearRegression.html
  
### 3. Why intercept in linear model is always a number and not a vector?

Let's say you are solving a problem of predicting a price of a house, based on its square feet area, distance to the nearest subway and number of parking lots near by. Then, every observation (x) is a 3-dim vector, and for every observation you have a corresponding price of a house (y).

Now, linear model, literally "models" the dependence between `x`-s and `y`-s in a form of linear function: `y = a * x + b`. Remember that `y` is a number, and `x` and `a` are vectors, so the only way we end up with a correct sizes of all terms is for `b` to be a number. Imaging that `x` is a vector of zeros, then the interpretation of `b` is a "baseline" price of a house.

### 4. Why should we impute instead of dropping?

In my personal experience imputing with mean is never *very* good idea. You will have a separate seminar on imputing missing values. For now, imputing with "mean" is just for training purposes. And dropping is mostly a bad idea, since you are not guaranteed to have all features during inference, and you still want to be able to make predictions.

# Q&A-3 07.10.2021 TODO: add answers

1. Why to use KFold
2. Installing packages using pip in colab
3. random_state, what for? mainly for reproducibility
4. Why `X.iloc[train]` but `y[train]` ?
