# Support Vector Machine

[SVM](https://en.wikipedia.org/wiki/Support_vector_machine) is trying to find biggest distance between the points, so there is as much separation as possible.

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



