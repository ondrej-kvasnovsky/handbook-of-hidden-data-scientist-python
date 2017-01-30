# Decision Trees

This is very popular algorithm in supervised machine learning.

## Linearly separable data

Are these data points linearly separable? They are not, which could suggest that decision trees are good for data sets that are not linearly separable.

![](/assets/decision-trees-separable.png)

If we set a good thresholds for wind and sun features, we could separate the data into 3 segments. The decision tree can be then created. See the following image.

![](/assets/decision-tree-windy-sunny.png)

This is what decision tree algorithm is doing for us. It finds these thresholds for us and creates the decision tree based on that.

Here is one more example which is using more realistic approach.

![](/assets/decision-tree-realone.png)

## Example

If you are running into some issues with graph visualization, check [stackoverflow](http://stackoverflow.com/questions/18438997/why-is-pydot-unable-to-find-graphvizs-executables-in-windows-8).

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



