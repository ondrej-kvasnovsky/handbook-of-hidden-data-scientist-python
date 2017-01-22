## Timing operations

Capture snapshot of operation execution.

## Time to create an array

```
import time
import numpy as np

def test_run():
    t1 = time.time()
    array = np.random.randint(0, 10, size=(3, 4))
    t2 = time.time()
    print "Time it took to generate random array: ", t2 - t1, " seconds"

if __name__ == "__main__":
    test_run()
```

Output is.

```
Time it took to generate random array:  1.38282775879e-05  seconds
```

## How fast is NumPy?

Lets compare "manual" going trough the array instead of using NumPy function.

```
import numpy as np
from time import time

def how_long(func, *args) :
    t0 = time()
    result = func(*args)
    t1 = time()
    return result, t1 - t0

def manual_mean(arr):
    sum = 0
    for i in xrange(0, arr.shape[0]):
        for j in xrange(0, arr.shape[1]):
            sum = sum + arr[i, j]
    return sum / arr.size

def test_run():
    nd1 = np.random.random((1000, 10000))

    res_manual, t_manual = how_long(manual_mean, nd1)

    res_numpy, t_numpy = how_long(np.mean, nd1)

    print res_manual
    print t_manual
    print res_numpy
    print t_numpy


if __name__ == "__main__":
    test_run()
```

Here is the result of measurement. Mean is the same, but times are significantly different. NumPy is just so much faster than manual processing of an array. For manual method, it takes about 5 seconds. 

```
0.499932014806
5.12550282478

0.499932014806
0.0108699798584
```



