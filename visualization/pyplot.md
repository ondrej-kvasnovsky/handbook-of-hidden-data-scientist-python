# pyplot

Provides a MATLAB-like plotting framework. `pylab`combines pyplot with numpy into a single namespace.

### Visualization basics

We create X axis that start in 0 and goes to 5, with 0.1 steps. Then we create Y axis using SIN function where we pass X as input.

```
import numpy as np
import matplotlib.pyplot as plt

x = np.arange(0, 5, 0.1)
y = np.sin(x)
plt.plot(x, y)
plt.show()
```

### Here is the output. ![](/assets/Screen Shot 2017-05-19 at 10.33.16 AM.png)Scatter plot

Lets create a simple scatter plot to introduce basics of scatter plot.

```
import matplotlib.pyplot as plt

x = [1, 2, 3, 4]
y = [3, 4, 8, 6]

colors = (0, 0, 0)
plt.scatter(x, y, c=colors, alpha=0.5)

plt.title('Scatter plot')
plt.xlabel('x')
plt.ylabel('y')

plt.show()
```

![](/assets/Screen Shot 2017-05-19 at 12.14.35 PM.png)When we want to visualize different groups of points, we might want to color the points. 

```
import numpy as np
import matplotlib.pyplot as plt

N = 10
g1 = (0.6 + 0.6 * np.random.rand(N), np.random.rand(N))
g2 = (0.4 + 0.3 * np.random.rand(N), 0.5 * np.random.rand(N))
g3 = (0.3 * np.random.rand(N), 0.3 * np.random.rand(N))

data = (g1, g2, g3)
colors = ("red", "green", "blue")
groups = ("coffee", "tea", "water")

# Create plot
fig = plt.figure()
ax = fig.add_subplot(1, 1, 1, axisbg="1.0")

for data, color, group in zip(data, colors, groups):
    x, y = data
    ax.scatter(x, y, alpha=0.8, c=color, edgecolors='none', s=30, label=group)

plt.title('scatter plot')
plt.legend(loc=2)
plt.show()
```

![](/assets/Screen Shot 2017-05-19 at 12.17.19 PM.png)

