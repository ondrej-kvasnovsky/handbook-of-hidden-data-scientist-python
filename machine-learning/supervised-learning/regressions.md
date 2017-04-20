# Regressions

## Discreet vs Continuous learning

Here is an example of descreet data. Input is numerical, but out put is binary \(or dimensional or so to say, there is no order\).

![](/assets/regression-discrete.png)Here is continuous example, both input and output are numerical. For example, taller person weights more, this is called continous learning. ![](/assets/regression-continous.png)Here are few other examples to test your understanding of discreet and continuous learning. ![](/assets/regression-examples.png)Here is one more example. ![](/assets/regression-example2.png)

Linear regression is meant for numerical results \(this chapter is only about linear regression\). Logistic regression is for discrete results \(used for classification\).

Both linear regression and logistic regression have the same drawbacks. Both have the tendency to “overfit,” which means the model adapts too exactly to the data at the expense of the ability to generalise to previously unseen data. Because of that, both models are often “regularised,” which means they have certain penalties to prevent overfit. Another drawback of linear models is that, since they’re so simple, they tend to have trouble predicting more complex behaviours.

## Slope And Intercept

Slope says the angle of the line. Intercept says where the line is positioned. ![](/assets/slope-intercept.png)Here is another example showing slope and intercept. In SciKitt, coef\_\_ is slope. ![](/assets/slope-intercept-2.png)

## Code example

Here is an example how to train linear regression algorithm. We print out the slope \(coef\_\) and intercept. Then you can access r-squared score for a dataset \(it is way to test regression algorithm\). Higher r-squared is, better the algoritm is performing \(maximum is 1.0\).

```
from sklearn import linear_model
reg = linear_model.LinearRegression()
reg.fit ([[0, 0], [1, 1], [2, 2]], [0, 1, 2])

reg.coef_
reg.intercept_
reg.score([[0, 0], [1, 1], [2, 2]], [0, 1, 2]) # here you should use test data (not training data like I did)
```

## How to evaluate linear regression errors

Error is length between regression line and actual position of the point. For this example, the distance between line and point is -18.75, therefore, the error for a point is -18.75. ![](/assets/regression-error.png)What is a good criterion for a good fit? It is sum of all \|errors\| \(sum of all absolute values for all points\).

## Minimizing of error using Sum Square Errors

The best regression is the one that minimizes SUM\( \|error\| \). m is slope and b is intercept. We can use these algorithms to minimize squeare error:

* Ordinary least square \(OLS\)
* Gradient descent![](/assets/regression-min.png)

Why is it good to think of regression as minimizing of square errors? It is because it increases accuracy by finding line that is just far enough from all the points in training dataset.

## SSE is not perfect

SSE is not perfect because it dependents on number of point in the training dataset.![](/assets/sse-isntperfect.png)

## R squared

R squared is better metric for evaluation of Regression if number of points in the dataset is changing. If the result of r-squared is close to 1, the regression line does good predicting job.![](/assets/r-squared.png)Here are few additional info for [Regression metrics](http://scikit-learn.org/stable/modules/model_evaluation.html#regression-metrics).

