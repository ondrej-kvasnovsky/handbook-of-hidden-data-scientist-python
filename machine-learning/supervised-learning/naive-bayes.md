# Naive Bayes

Naive [Bayes](https://en.wikipedia.org/wiki/Naive_Bayes_classifier) is [algorithm](http://stackoverflow.com/questions/10059594/a-simple-explanation-of-naive-bayes-classification) to find decision surface. We have drawn a line that divides two sets of data points \(based on what Gaussian Naive Bayes would do\). When we add a new point on chart in order to predict into what category it falls, it will be into the first one. 

![](/assets/GaussianNB.png)

Have a look at this code \(training data and labels\) and then check the chart and the result of prediction. 

```
import numpy as np
from sklearn.naive_bayes import GaussianNB

features = np.array([[-1, -1], [-2, -1], [-3, -2], [1, 1], [2, 1], [3, 2]])
labels = np.array([1, 1, 1, 2, 2, 2])

clf = GaussianNB()
clf.fit(features, labels)

print(clf.predict([[-0.8, -1]])) 
```

Out put is following. So, we can see that coordinates \[-0.8, -1\] fall into category 1.

```
[1]
```



