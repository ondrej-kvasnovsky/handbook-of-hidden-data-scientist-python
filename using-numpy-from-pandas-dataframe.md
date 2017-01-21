# Using NumPy from pandas DataFrame

After we create DataFrame using pandas library, we might want to access data from the data frame directly. Here is how to do it.

```
import pandas as pd

def test_run():
    df = pd.read_csv("data/AAPL.csv")
    print df.values

if __name__ == "__main__":
    test_run()
```

Here is the output. Notice that it does not contain name of the columns. This table is really the content of data frame.

```
[['2017-01-20' 120.449997 120.449997 ..., 120.0 29479900 120.0]
 ['2017-01-19' 119.400002 120.089996 ..., 119.779999 25295700 119.779999]
 ['2017-01-18' 120.0 120.5 ..., 119.989998 23644700 119.989998]
 ..., 
 ['1980-12-16' 25.375 25.375 ..., 25.25 26432000 0.374879]
 ['1980-12-15' 27.375001 27.375001 ..., 27.25 43971200 0.404572]
 ['1980-12-12' 28.75 28.875 ..., 28.75 117258400 0.426842]]
```

## Navigating in N-Dimensional array

If we want to navigate to specific coordinates in this 2 dimensional array, we use brackets with indexes, like nd\[row, column\].

```
import pandas as pd

def test_run():
    df = pd.read_csv("data/AAPL.csv")
    nd = df.values
    print nd[0, 0]

if __name__ == "__main__":
    test_run()
```

Here is the output.

```
2017-01-20
```

## Sub array

If we would like to extract sub array from the nd array, we can provide ranges coordinates.

```
import pandas as pd

def test_run():
    df = pd.read_csv("data/AAPL.csv")
    nd = df.values
    print nd[0:5, 0:2]

if __name__ == "__main__":
    test_run()
```

Here is the sub array.

```
[['2017-01-20' 120.449997]
 ['2017-01-19' 119.400002]
 ['2017-01-18' 120.0]
 ['2017-01-17' 118.339996]
 ['2017-01-13' 119.110001]]
```

## Select all rows and some columns

Use just ":" as row parametr to select all rows.

```
import pandas as pd

def test_run():
    df = pd.read_csv("data/AAPL.csv")
    nd = df.values
    print nd[:, 0]

if __name__ == "__main__":
    test_run()
```

Here is the output. It contains all rows and just one row. 

```
[['2017-01-20']
 ['2017-01-19']
 ['2017-01-18']
 ['2017-01-17']
 ['2017-01-13']]
```

## Select last or second last row

We can navigate to rows from the bottom of the table using negative numbers. 

```
import pandas as pd

def test_run():
    df = pd.read_csv("data/AAPL.csv")
    nd = df.values
    print nd[-1, 0]

if __name__ == "__main__":
    test_run()
```

The output is the last value in column on 0th position.

```
2017-01-13
```

If we would use -2 as row parameter value, we would get this output. 

```
2017-01-17
```





