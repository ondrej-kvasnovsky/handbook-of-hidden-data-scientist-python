# Support Vector Machine

[SVM](https://en.wikipedia.org/wiki/Support_vector_machine) is trying to find biggest distance between the points, so there is as much separation as possible.

![](/assets/svm1.png)

What should SVM do with this data set? It should ignore that outlier.

![](/assets/svm2.png)

Here is an example from svm documentation. 

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



