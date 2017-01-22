## Create N-Dimensional Array

We are going to explore what are the ways to create arrays using NumPy library.

## Create 1-dimensional array

```
import numpy as np

def test_run():
    print np.array([1, 2, 3])

if __name__ == "__main__":
    test_run()
```

Here is the ouput.

```
[1 2 3]
```

## Create 2-dimensional array

```
import numpy as np

def test_run():
    print np.array([(1, 2, 3), (2, 3, 4)])

if __name__ == "__main__":
    test_run()
```

Here is the output.

```
[[1 2 3]
 [2 3 4]]
```

## Create an empty array

Here we create 3 arrays. First one is 1-dimensional, second is 2-dimensional and third is 3-dimensional.

```
import numpy as np

def test_run():
    print np.empty(5)
    print np.empty((5, 4))
    print np.empty((5, 4, 3))

if __name__ == "__main__":
    test_run()
```

When we run the code it does return arrays with some values. These values represent what ever value which was present in that part of memory \(so, kind of random values\).

```
[  0.00000000e+000   3.10503637e+231   1.97626258e-323   9.88131292e-324
   1.48219694e-323]


[[  0.00000000e+000   0.00000000e+000   2.12481278e-314   2.78136354e-309]
 [  2.12461675e-314   2.12461675e-314   0.00000000e+000   2.14107926e-314]
 [  6.35862486e-321   0.00000000e+000   0.00000000e+000   0.00000000e+000]
 [  2.12497467e-314   9.73469813e-309   2.12501760e-314   2.12501760e-314]
 [  0.00000000e+000   2.14108224e-314   2.12199643e-314   0.00000000e+000]]


[[[  0.00000000e+000   0.00000000e+000   1.72922976e-322]
  [ -7.63277803e+283   2.12332385e-314   2.12278772e-314]
  [  0.00000000e+000   0.00000000e+000   0.00000000e+000]
  [  0.00000000e+000   0.00000000e+000   0.00000000e+000]]

 [[  1.65169957e-220   2.12342370e-314   2.14185236e-314]
  [ -3.39981117e-158   2.12575452e-314   2.16533381e-314]
  [  5.41141341e-041   2.12608880e-314   2.16533366e-314]
  [  0.00000000e+000   0.00000000e+000   0.00000000e+000]]

 [[ -3.67112871e-197   2.12332381e-314   2.16533378e-314]
  [  2.99382801e+052   2.12565003e-314   2.16533369e-314]
  [  0.00000000e+000   0.00000000e+000   0.00000000e+000]
  [  4.42201243e+096   2.12342394e-314   2.16533362e-314]]

 [[  1.79989302e-302   2.12608883e-314   2.16533350e-314]
  [  0.00000000e+000   0.00000000e+000   0.00000000e+000]
  [  3.00806175e+144   2.12607350e-314   2.14185242e-314]
  [ -6.64080621e+188   2.12565000e-314   2.16533372e-314]]

 [[  0.00000000e+000   0.00000000e+000   2.12497467e-314]
  [  2.78134232e-309   2.12499421e-314   2.12499421e-314]
  [  2.12501673e-314   2.14108224e-314   2.12199642e-314]
  [  0.00000000e+000   0.00000000e+000   0.00000000e+000]]]
```

## Create array with default values

Here we create array with number 1 present in all cells.

```
import numpy as np

def test_run():
    print np.ones((5, 4))

if __name__ == "__main__":
    test_run()
```

Here is the array with all the ones.

```
[[ 1.  1.  1.  1.]
 [ 1.  1.  1.  1.]
 [ 1.  1.  1.  1.]
 [ 1.  1.  1.  1.]
 [ 1.  1.  1.  1.]]
```

## Create typed array

We are going to create array of integers in this section.

```
import numpy as np

def test_run():
    print np.empty((3, 2), dtype=np.int_)

if __name__ == "__main__":
    test_run()
```

Now we have created array full of integers.

```
[[         0          0]
 [4301258756 4301322160]
 [4299901408          0]]
```

## Create array with random numbers

We need to use random module from numpy library.

```
import numpy as np

def test_run():
    print np.random.rand(3, 2)

if __name__ == "__main__":
    test_run()
```

Here is the array with random values.

```
[[ 0.88356865  0.72362337]
 [ 0.95050018  0.2568881 ]
 [ 0.14610116  0.92273639]]
```

## Random numbers using Gaussian \(normal\) distribution

We will use 50 as mean and 10 as standard deviation.

```
import numpy as np

def test_run():
    # mean 50
    # standard deviation 10
    print np.random.normal(50, 10, size=(3, 2))

if __name__ == "__main__":
    test_run()
```

Here is the output.

```
[[ 55.69211472  52.05373459]
 [ 31.19917659  52.00790108]
 [ 39.79686777  44.11232758]]
```

## Generate array of random integers in a specific range

```
import numpy as np

def test_run():
    print np.random.randint(0, 10, size=(3, 2))

if __name__ == "__main__":
    test_run()
```

Here is the output.

```
[[8 0]
 [1 9]
 [2 4]]
```



