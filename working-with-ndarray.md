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



