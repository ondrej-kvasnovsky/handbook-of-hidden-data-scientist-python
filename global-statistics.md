# Global Statistics

Let's see what is available in numpy library in order to do statistics on an n-dimensional array. First get CSV files for AAPL, GOOG, IBM and GLD, from this page: [https://finance.yahoo.com/quote/AAPL/history?p=AAPL. ](https://finance.yahoo.com/quote/AAPL/history?p=AAPL)

## Plot and calculate mean, std etc...

```
import os
import pandas as pd
import matplotlib.pyplot as plt

def symbol_to_path(symbol, base_dir="data"):
    return os.path.join(base_dir, "{}.csv".format(str(symbol)))

def get_data(symbols, dates):
    df = pd.DataFrame(index=dates)
    if 'SPY' not in symbols:
        symbols.insert(0, 'SPY')

    for symbol in symbols:
        path = symbol_to_path(symbol)
        newDf = pd.read_csv(path,
                        index_col='Date',
                        parse_dates=True,
                        usecols=['Date', 'Adj Close'],
                        na_values=['nan'])
        newDf = newDf.rename(columns={'Adj Close': symbol})
        df = df.join(newDf)
        df = df.dropna()

    return df

def plot_data(df):
    df.plot()
    plt.show()

def test_run():
    # Define a date range
    dates = pd.date_range('2010-01-22', '2012-01-26')

    # Choose stock symbols to read
    symbols = ['GOOG', 'IBM', 'GLD', 'AAPL']

    # Get stock data
    df = get_data(symbols, dates)

    print "Mean:"
    print df.mean()

    print "Median:"
    print df.median()

    print "Standard deviation:"
    print df.std()

    print "Sum:"
    print df.sum()

    plot_data(df)


if __name__ == "__main__":
    test_run()
```

Here is the output. First lets have a look at the image, so we have better understanding of what the data look like.

![](/assets/glob_stats_chart1.png)

Now we can check calculated numbers. Check standard deviation, the highest number is for Google, because their stocks are going up and down by a lot. Standard deviation is measure of deviation from the center, mean, of the data.

```
Mean:
SPY     106.943554
GOOG    276.460087
IBM     132.548075
GLD     138.086496
AAPL     41.414315
dtype: float64

Median:
SPY     107.265254
GOOG    274.101372
IBM     134.560650
GLD     135.410004
AAPL     43.072091
dtype: float64

Standard deviation:
SPY      8.521511
GOOG    25.374959
IBM     20.361991
GLD     20.455301
AAPL     8.075417
dtype: float64

Sum:
SPY      54327.325496
GOOG    140441.724183
IBM      67334.422350
GLD      70147.940030
AAPL     21038.471976
dtype: float64
```



