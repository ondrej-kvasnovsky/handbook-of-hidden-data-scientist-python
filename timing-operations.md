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

```

Here is the result of measurement.

```

```



