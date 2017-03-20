# Decision Trees

This is very popular algorithm in supervised machine learning. It is easy to overfit decision tree if there are many features and the decision tree gets complicated. 

Otherwise, it is easy to learn and visualize algorithm. 

## Linearly separable data

Are these data points linearly separable? They are not, which could suggest that decision trees are good for data sets that are not linearly separable.

![](/assets/decision-trees-separable.png)

If we set a good thresholds for wind and sun features, we could separate the data into 3 segments. The decision tree can be then created. See the following image.

![](/assets/decision-tree-windy-sunny.png)

This is what decision tree algorithm is doing for us. It finds these thresholds for us and creates the decision tree based on that.

Here is one more example which is using more realistic approach.

![](/assets/decision-tree-realone.png)

## Example

> If you are running into some issues with graph visualization, check [stackoverflow](http://stackoverflow.com/questions/18438997/why-is-pydot-unable-to-find-graphvizs-executables-in-windows-8).

First we create a data set like this.

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

Then we create decision tree, fit the data and try to predict a point.

```
import numpy as np
from sklearn import tree

np.random.seed(0)
features = np.r_[np.random.randn(5, 2) - [2, 2], np.random.randn(5, 2) + [2, 2]]
labels = [0] * 5 + [1] * 5
print features
print labels

clf = tree.DecisionTreeClassifier()
clf = clf.fit(features, labels)

print clf.predict([[2., 2.]])

tree.export_graphviz(clf, out_file='tree.dot')

import pydotplus
dot_data = tree.export_graphviz(clf, out_file=None)
graph = pydotplus.graph_from_dot_data(dot_data)
graph.write_pdf("tree.pdf")
```

Here is visualized decision tree. We can see that decision tree algorithm decided to split data on value 1.0058. What is less or equal 1.0058 is True and what is greater, is false.

![](/assets/decision-tree-simple.png)

## Min sample split

This chapter is about `min_sample_split`parameter. Lets look at example, we set value to 2 in the first one. In the second, we set it to 50 \(so, minimum value for split is 50\). Observe size of decision tree.

Here is the sample code.

```
import numpy as np
from sklearn import tree

np.random.seed(0)
size = 20
features = np.r_[np.random.randn(size, 2) - [2, 2], np.random.randn(size, 2) + [2, 2], np.random.randn(size, 2) + [4, 4]]
labels = [0] * size + [1] * size + [2] * size
print features
print labels

clf = tree.DecisionTreeClassifier(min_samples_split=2)
clf = clf.fit(features, labels)

print clf.predict([[2., 2.]])

tree.export_graphviz(clf, out_file='tree.dot')

import pydotplus
dot_data = tree.export_graphviz(clf, out_file=None)
graph = pydotplus.graph_from_dot_data(dot_data)
graph.write_pdf("tree.pdf")
```

Here is the decision tree created from that code.

![](/assets/decision-tree-minsplit2.png)

When we change min sample split value to 50, the tree becomes really small, because we are saying "do not split it unless the number of samples is 50" to the decision tree. And in this case, that condition is valid only for the root element.

```
import numpy as np
from sklearn import tree

np.random.seed(0)
size = 20
features = np.r_[np.random.randn(size, 2) - [2, 2], np.random.randn(size, 2) + [2, 2], np.random.randn(size, 2) + [4, 4]]
labels = [0] * size + [1] * size + [2] * size
print features
print labels

clf = tree.DecisionTreeClassifier(min_samples_split=50)
clf = clf.fit(features, labels)

print clf.predict([[2., 2.]])

tree.export_graphviz(clf, out_file='tree.dot')

import pydotplus
dot_data = tree.export_graphviz(clf, out_file=None)
graph = pydotplus.graph_from_dot_data(dot_data)
graph.write_pdf("tree.pdf")
```

![](/assets/decision-tree-minsplit50.png)

## Accuracy

We always want \(have to\) to check accuracy of the algorithm we used. Here is a sample how to do it for decision tree.

```
import numpy as np
from sklearn import tree

np.random.seed(0)
size = 80
features = np.r_[np.random.randn(size, 2) - [2, 2], np.random.randn(size, 2) + [2, 2]]
labels = [0] * size + [1] * size

test_size = 40
test_features = np.r_[np.random.randn(test_size, 2) - [2, 2], np.random.randn(test_size, 2) + [2, 2]]
test_labels =  [0] * test_size + [1] * test_size

clf = tree.DecisionTreeClassifier(min_samples_split=2)
clf = clf.fit(features, labels)

from sklearn.metrics import accuracy_score
pred = clf.predict(test_features)
accuracy = accuracy_score(pred, test_labels)
print accuracy
```

Here is the accuracy of randomly generated data, which is what we did in the code above. We have generated 80 training points and 40 test points. You can try to change values and see how accuracy changes.

```
0.975
```

## Entropy

Entropy controls how a decision tree decies where to split the data. Entropy is measure of impurity in a bunch of examples. Entropy is oposite of purity.

See this example, the dataset on the right side \(that contains only red X\) has higher purity.

![](/assets/decision-tree-purity.png)

Example how to calculate entropy.

![](/assets/dt-entropy.png)

Pslow is 2/4 \(2slow / 4total rows\) and the same for Pfast.

Here is the exact formula to calculate the entropy:

```
import math
print -0.5 * math.log(0.5, 2) - 0.5 * math.log(0.5, 2)

output: 1.0
```

## Information gain

Entropy is used in calculation to maximize information gain in the decision tree. Information gain is used to decide what value to take to make a split.

Here is how to calculate Pslow and Pfast \(for speed, which is the patent in this example\). For steep, there are two slow and one fast records, so Pslow is 2/3 and Pfast is 1/3. For flat the entropy is 0.

![](/assets/info-gain-x.png)

Now we calculate entropy of children \(grade feature\).

![](/assets/dt-information-gain.png)

Now we calculate weighted average of children 3/4 are going to fast branch \(it is 0.9184\). 1/4 goes for slow branch \(it is 0\).

![](/assets/info-gainx2.png)

Finally we can calculate information gain. The formula is: 1 - 3/4 \* 0.9184. And the information gain of grade feature is 0.3112.

Then we should calculate information gain for bumpiness \(entropy of bumpy is 1.0, entropy of smooth is 1.0\). So, when we calculate information gain of bumpiness, we get 0. We learned nothing based on bumpiness and therefore we do not want to split it based on bumpiness.

What would be information gain based on speed limit? The information gain is 1.0. Which means we get perfect purity based on speed limit and information gain is 1.0 \(the best we can get\) and this is where we want to make the split.

Default criterion in [scikit learn](http://scikit-learn.org/stable/modules/generated/sklearn.tree.DecisionTreeClassifier.html) is 'gini' but can be changed to 'entropy'.

## Bias-Variance Dilemma

Should your algorithm be more bias or more variance? There needs to be balance between bias and variance, so you need to tune your algorithm. 

High bias algorithm basically ignores data and it is easy to do generalization for them. High variance means high variance data and it is difficult to categorize data. We need to have an algorithm that is able to generalize but also take in \(learn from\) a new data. 

