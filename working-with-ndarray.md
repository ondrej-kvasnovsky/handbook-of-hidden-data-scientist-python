## Working with NDArray

## Get shape of array

We can get shape of an array by accessing 'shape' property.

```
import numpy as np

def test_run():
    array = np.array([(1, 2, 3), (2, 3, 4)])
    print array.shape
    print len(array.shape)
    print array.shape[0]
    print array.shape[1]

if __name__ == "__main__":
    test_run()
```

Here we have printed out the shape of the array.

```
(2, 3)
2
2
3
```

## Get size of array

Size of array is returned as sum of all cells in the n-dimension array.

```
import numpy as np

def test_run():
    array = np.array([(1, 2, 3), (2, 3, 4)])
    print array.size

if __name__ == "__main__":
    test_run()
```

For our example, which contains 6 numbers, it prints out 6.

```
6
```

## Type of array

NumPy arrays are homogenous \(all the cells must have the same type\) and we can get that type for an array.

```
import numpy as np

def test_run():
    array = np.array([(1, 2, 3), (2, 3, 4)])
    print array.dtype

if __name__ == "__main__":
    test_run()
```

Here is the type of the array.

```
int64
```

## Make random numbers the same for every execution

We can set seed for random number generation. Which will make sure that the random numbers are generated always the same.

```
import numpy as np

def test_run():
    np.random.seed(100)
    array = np.random.randint(0, 10, size=(3,4))
    print array

if __name__ == "__main__":
    test_run()
```

So, everytime we run this code, we get the same result.

```
[[8 8 3 7]
 [7 0 4 2]
 [5 2 2 2]]
```

## Sum all elements in array

```
import numpy as np

def test_run():
    print array
    print array.sum()

if __name__ == "__main__":
    test_run()
```

Here is sum.

```
[[1 2 3]
 [2 3 4]]
15
```

## Sum of each column and row

```
import numpy as np

def test_run():
    array = np.array([(1, 2, 3), (2, 3, 4)])
    print array
    print array.sum(0)
    print array.sum(1)

if __name__ == "__main__":
    test_run()
```

Here are the sums.

```
[3 5 7]
[6 9]
```



