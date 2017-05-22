# Support Vector Machine

[SVM](https://en.wikipedia.org/wiki/Support_vector_machine) is trying to find biggest distance between the points, so there is as much separation as possible. That said, SVM works well with less data where the separation is obvious \(there are big margins between the data points\). So, SVM does not work well for data sets with a lot of points and with data sets with a lot of noice.

Taken from [An Idiot’s guide to Support vector machines \(SVMs\)](http://web.mit.edu/6.034/wwwbob/svm.pdf): ![](/assets/Screen Shot 2017-05-21 at 9.50.59 PM.png)

> * SVMs maximize the margin \(Winston terminology: the ‘street’\) around the separating [hyperplane](https://en.wikipedia.org/wiki/Hyperplane).
>
> * The decision function is fully specified by a \(usually very small\) subset of training samples, the support vectors.
>
> * This becomes a Quadratic programming problem that is easy to solve by standard methods
>
> General input/output for SVMs just like for neural nets, but for one important addition...
>
> **Input**: set of \(input, output\) training pair samples; call the input sample features _x1, x2...xn_, and the output result _y_.Typically, there can be lots of input features _x\(i\)_.
>
> **Output**: set of weights w\(or _w\(i\)_\), one for each feature, whose [linear combination](https://en.wikipedia.org/wiki/Linear_combination) predicts the value of _y_.\(So far, just like neural nets...\)
>
> **Important difference**: we use the optimization of maximizing the margin \(‘street width’\) to reduce the number of weights that are nonzero to just a few that correspond to the important features that ‘matter’ in deciding the separating line \([hyperplane](https://en.wikipedia.org/wiki/Hyperplane)\)...these nonzero weights correspond to the support vectors \(because they ‘support’ the separating hyperplane\)

Nice video explaining SVM is [here](https://www.youtube.com/watch?v=_PwhiWxHK8o).

![](/assets/svm1.png)

## Outliers

What should SVM do with this data set? It should ignore that outlier. These points are called outliers.

![](/assets/svm2.png)

Here is an example from [SVM documentation](http://scikit-learn.org/stable/modules/generated/sklearn.svm.SVC.html).

```
import numpy as np
X = np.array([[-1, -1], [-2, -1], [1, 1], [2, 1]])
y = np.array([1, 1, 2, 2])
from sklearn.svm import SVC
clf = SVC()
clf.fit(X, y)

print(clf.predict([[-0.8, -1]]))
```

The result is:

```
[1]
```

## Not separable data and kernel parameter

In case the data are no separable at the first sight, we can calculate a new feature. We need to create a linear line.

![](/assets/svm-newfeature.png)

We do not have to calculate new features. We can change 'kernel' parameter to force SVM to create linear separator. There are other parameters we can configure for SVM. There are to more that are important, it is C and gamma.

## C parameter

Here is what C does. Bigger C value causes more points to be correctly separated, but it also costs more. There must be a balance between algorithm accuracy and speed.

![](/assets/svm-c.png)

## Overfitting

If the lines separating data points are too complex, it is called overfitting. The black curve on the chart below is example of overfitting. The green line, show how the good separation could look like. We can change C, gamma or kernel to tune separation and get rid of overfitting \(do not take all the data too seriously\).

![](/assets/svm-overfitting.png)

## Visualize hyperplane

Here is a nice example from documentation. First we generate 5 points for each label. Then we use linear SVC and fit the created points. Then see how separation line is calculated, together with another two lines that make margin easily observable. Hyper plane has always one less dimension than the space it exists \(e.g. for 2D system, 1D line is hyperplane\).

```
import numpy as np
import matplotlib.pyplot as plt
from sklearn import svm

np.random.seed(0)
X = np.r_[np.random.randn(5, 2) - [2, 2], np.random.randn(5, 2) + [2, 2]]
Y = [0] * 5 + [1] * 5
print X
print Y

# fit the model
clf = svm.SVC(kernel='linear')
clf.fit(X, Y)

# get the separating hyperplane
w = clf.coef_[0]
a = -w[0] / w[1]
xx = np.linspace(-5, 5)
yy = a * xx - (clf.intercept_[0]) / w[1]

# plot the parallels to the separating hyperplane that pass through the
# support vectors
b = clf.support_vectors_[0]
yy_down = a * xx + (b[1] - a * b[0])
b = clf.support_vectors_[-1]
yy_up = a * xx + (b[1] - a * b[0])

# plot the line, the points, and the nearest vectors to the plane
plt.plot(xx, yy, 'k-')
plt.plot(xx, yy_down, 'k--')
plt.plot(xx, yy_up, 'k--')

plt.scatter(clf.support_vectors_[:, 0], clf.support_vectors_[:, 1],
            s=80, facecolors='none')
plt.scatter(X[:, 0], X[:, 1], c=Y, cmap=plt.cm.Paired)

plt.axis('tight')
plt.show()
```

Here is the chart with the separation lines and another two "margin" lines.

![](/assets/svm-separation-lines.png)

Here is the data used in the chart.

```
Features: 
[[-0.23594765 -1.59984279]
 [-1.02126202  0.2408932 ]
 [-0.13244201 -2.97727788]
 [-1.04991158 -2.15135721]
 [-2.10321885 -1.5894015 ]
 [ 2.14404357  3.45427351]
 [ 2.76103773  2.12167502]
 [ 2.44386323  2.33367433]
 [ 3.49407907  1.79484174]
 [ 2.3130677   1.14590426]]

Labels:
[0, 0, 0, 0, 0, 1, 1, 1, 1, 1]
```



