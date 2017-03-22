# Regressions

## Discreet vs Continuous learning

Here is an example of descreet data. Input is numerical, but out put is binary \(or dimensional or so to say, there is no order\).

![](/assets/regression-discrete.png)Here is continuous example, both input and output are numerical. For example, taller person weights more, this is called continous learning. ![](/assets/regression-continous.png)Here are few other examples to test your understanding of discreet and continuous learning. ![](/assets/regression-examples.png)Here is one more example. ![](/assets/regression-example2.png)

## Slope And Intercept

Slope says the angle of the line. Intercept says where the line is positioned. ![](/assets/slope-intercept.png)Here is another example showing slope and intercept. In SciKitt, coef\_\_ is slope. ![](/assets/slope-intercept-2.png)

## Code example

Here is an example how to train linear regression algorithm. We print out the slope \(coef\_\).

```
from sklearn import linear_model
reg = linear_model.LinearRegression()
reg.fit ([[0, 0], [1, 1], [2, 2]], [0, 1, 2])

reg.coef_
```



