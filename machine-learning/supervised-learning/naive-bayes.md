# Naive Bayes

Naive [Bayes](https://en.wikipedia.org/wiki/Naive_Bayes_classifier) is [algorithm](http://stackoverflow.com/questions/10059594/a-simple-explanation-of-naive-bayes-classification) to find decision surface. Naive Bayes is good for text learning. See an example below. Who wrote the email that contains Love and Life words? It si Sara. If words would be Life and Deal, it would be Chris. Why is it called Naive? Because it is calculated based on probabilities \(e.g. word frequency\).

![](/assets/text-learning.png)

Here is another example with easier data to understand. We have drawn a line that divides two sets of data points \(based on what Gaussian Naive Bayes would do\). When we add a new point on chart in order to predict into what category it falls, it will be into the surface below the line.

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

# Accuracy

We should verify what is the accuracy of our algorithm usage. For the first example, we will create features and labels. Then we create test data. Then we calculate accuracy. For the following example, the output will be 1.0 \(which is 100% accuracy\). It is because we used the same data points for testing we used for learning.

```
import numpy as np
from sklearn.naive_bayes import GaussianNB
from sklearn.metrics import accuracy_score

features = np.array([[-1, -1], [-2, -1], [-3, -2], [1, 1], [2, 1], [3, 2]])
labels = np.array([1, 1, 1, 2, 2, 2])

clf = GaussianNB()
clf.fit(features, labels)

features_test = [[-1, -1], [1, 1]]
labels_test = [1, 2]
pred = clf.predict(features_test)

accuracy = accuracy_score(pred, labels_test)
print accuracy
```

We should tease the algorithm and give it features and labels that were not used for learning. Like here.

```
import numpy as np
from sklearn.naive_bayes import GaussianNB
from sklearn.metrics import accuracy_score

features = np.array([[-1, -1], [-2, -1], [-3, -2], [1, 1], [2, 1], [3, 2]])
labels = np.array([1, 1, 1, 2, 2, 2])

clf = GaussianNB()
clf.fit(features, labels)

features_test = [[-1, 1], [1, 1]] # I changed one number here, in the first array, from -1 to 1
labels_test = [1, 2]
pred = clf.predict(features_test)

accuracy = accuracy_score(pred, labels_test)
print accuracy
```

For this one, the accuracy is 0.5 because we said that the first data point is 1 but actually, it is falling into category 2.

