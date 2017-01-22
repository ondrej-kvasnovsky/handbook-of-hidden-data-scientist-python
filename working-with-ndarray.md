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
    print array.sum(0) # sum of columns
    print array.sum(1) # sum of rows

if __name__ == "__main__":
    test_run()
```

Here are the sums.

```
[3 5 7]
[6 9]
```

## Finding max, min and mean in an array

```
import numpy as np

def test_run():
    array = np.array([(1, 2, 3), (2, 3, 4)])
    print array

    print array.max(0) # max of first column
    print array.min(0) # min of first column
    print array.mean() # mean of all elements

if __name__ == "__main__":
    test_run()
```

Her are the values.

```
[[1 2 3]
 [2 3 4]]
[2 3 4]
[1 2 3]
2.5
```

There are more functions available, check [this page](https://docs.scipy.org/doc/numpy/reference/routines.math.html).

## Find index of max value

```
import numpy as np

def get_max_index(a):
    return np.argmax(a)


def test_run():
    a = np.array([9, 6, 2, 3, 12, 14, 7, 10], dtype=np.int32)  # 32-bit integer array
    print "Array:", a

    # Find the maximum and its index in array
    print "Maximum value:", a.max()
    print "Index of max.:", get_max_index(a)

if __name__ == "__main__":
    test_run()
```

Here is the output.

```
Array: [ 9  6  2  3 12 14  7 10]
Maximum value: 14
Index of max.: 5
```

## Slicing array

If you want to slice data, get some specific values of array, you can access it via indices.

```
import numpy as np

def test_run():
    array = np.array([(1, 2, 3), (2, 3, 4), (4, 5, 6)])
    print array
    print array[:, 0:3:2]

if __name__ == "__main__":
    test_run()
```

First argument ":" makes sure all rows are included. Second argument if more complex. 0 and 3 are saying what values to take. 2 is saying what will be skipped. Here is the output.

```
[[1 2 3]
 [2 3 4]
 [4 5 6]]
[[1 3]
 [2 4]
 [4 6]]
```

## Assigning values in array

```
import numpy as np

def test_run():
    array = np.array([(1, 2, 3), (2, 3, 4), (4, 5, 6)])
    print array
    array[0][0] = 100
    print  array

if __name__ == "__main__":
    test_run()
```

Here is the output.

```
[[1 2 3]
 [2 3 4]
 [4 5 6]]
[[100   2   3]
 [  2   3   4]
 [  4   5   6]]
```

Or you can assign value to whole row or column.

```
import numpy as np

def test_run():
    array = np.array([(1, 2, 3), (2, 3, 4), (4, 5, 6)])
    print array
    array[:, 0] = 100
    print  array

if __name__ == "__main__":
    test_run()
```

Here is the output.

```
[[1 2 3]
 [2 3 4]
 [4 5 6]]
[[100   2   3]
 [100   3   4]
 [100   5   6]]
```

Or you can set list of values to a row.

```
array[:, 0] = [0, 0,0]
```

## Indexing

```
import numpy as np

def test_run():
    array = np.random.rand(5)

    indices = np.array([1, 1, 2, 3])

    print array
    print array[indices]

if __name__ == "__main__":
    test_run()
```

Here is the output.

```
[ 0.22607416  0.94175441  0.45115583  0.3740176   0.53811653]
[ 0.94175441  0.94175441  0.45115583  0.3740176 ]
```

## Filtering data using conditions

Also called masking.

```
import numpy as np

def test_run():
    array = np.array([(20, 25, 10, 5), (10, 25, 10, 5)])

    print array

    mean = array.mean()
    print mean

    print array[array < mean]

if __name__ == "__main__":
    test_run()
```

Output.

```
[[20 25 10  5]
 [10 25 10  5]]
13.75
[10  5 10 10  5]
```



