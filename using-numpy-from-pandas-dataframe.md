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

Here is the output. Notice that it does not contain dates and name of the columns. This table is really the content of data frame. 

```
[['2017-01-20' 120.449997 120.449997 ..., 120.0 29479900 120.0]
 ['2017-01-19' 119.400002 120.089996 ..., 119.779999 25295700 119.779999]
 ['2017-01-18' 120.0 120.5 ..., 119.989998 23644700 119.989998]
 ..., 
 ['1980-12-16' 25.375 25.375 ..., 25.25 26432000 0.374879]
 ['1980-12-15' 27.375001 27.375001 ..., 27.25 43971200 0.404572]
 ['1980-12-12' 28.75 28.875 ..., 28.75 117258400 0.426842]]
```



