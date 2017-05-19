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

Here is the output. ![](/assets/Screen Shot 2017-05-19 at 10.33.16 AM.png)





