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



