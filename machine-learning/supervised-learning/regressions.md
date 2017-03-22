# Regressions

## Discreet vs Continuous learning

Here is an example of descreet data. Input is numerical, but out put is binary \(or dimensional or so to say, there is no order\).

![](/assets/regression-discrete.png)Here is continuous example, both input and output are numerical. For example, taller person weights more, this is called continous learning. ![](/assets/regression-continous.png)Here are few other examples to test your understanding of discreet and continuous learning. ![](/assets/regression-examples.png)Here is one more example. ![](/assets/regression-example2.png)

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

Error is length between regression line and actual position of the point. For this example, the distance between line and point is -18.75, therefore, the error is -18.75. ![](/assets/regression-error.png)What is a good criterion for a good fit? It is sum of all \|errors\| \(sum of all absolute values for all points\).

## Minimizing of sum square errors

The best regression is the one that minimizes SUM\( \|error\| \). m is slope and b is intercept. We can use these algorithms to minimize squeare error:

* Ordinary least square \(OLS\)
* Gradient descent

 ![](/assets/regression-min.png)

![](/assets/regression-min.png)

