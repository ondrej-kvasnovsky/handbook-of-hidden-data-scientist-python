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



