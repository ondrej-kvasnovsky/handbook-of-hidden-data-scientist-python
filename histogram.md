# Histogram

![](/assets/histogram.png)

The histogram is create from this data that you can see on this chart below.

![](/assets/histogram-data.png)

Then we transformed data into daily returns.

![](/assets/histogram-daily-return.png)

Now, we can take daily returns and transform it to histogram. We also add mean and standard deviation lines.

![](/assets/histogram-with-all.png)

Here is the code we used to generate the three charts above.

```
import pandas as pd
import matplotlib.pyplot as plt
from util import get_data, plot_data, compute_daily_returns


def test_run():
    dates = pd.date_range('2009-01-01', '2012-12-31')
    symbols = ['SPY']
    df = get_data(symbols, dates)
    plot_data(df)

    daily_returns = compute_daily_returns(df)
    plot_data(daily_returns, title="Daily returns", ylabel="Daily returns")

    daily_returns.hist(bins=20, color='c')

    mean = daily_returns['SPY'].mean()
    std = daily_returns['SPY'].std()
    kurtosis = daily_returns.kurtosis()
    print kurtosis  # if positive, we got fat tails, if negative, tails are skinny

    plt.axvline(mean, color='b', linestyle='dashed', linewidth=2)
    plt.axvline(std, color='r', linestyle='dotted', linewidth=2)
    plt.axvline(-std, color='r', linestyle='dotted', linewidth=2)
    plt.show()


if __name__ == "__main__":
    test_run()
```

We have moved some of the utility code into `util.py`.

```
import os
import pandas as pd
import matplotlib.pyplot as plt

def symbol_to_path(symbol, base_dir="data"):
    """Return CSV file path given ticker symbol."""
    return os.path.join(base_dir, "{}.csv".format(str(symbol)))

def get_data(symbols, dates):
    """Read stock data (adjusted close) for given symbols from CSV files."""
    df = pd.DataFrame(index=dates)
    if 'SPY' not in symbols:  # add SPY for reference, if absent
        symbols.insert(0, 'SPY')

    for symbol in symbols:
        df_temp = pd.read_csv(symbol_to_path(symbol), index_col='Date',
                              parse_dates=True, usecols=['Date', 'Adj Close'], na_values=['nan'])
        df_temp = df_temp.rename(columns={'Adj Close': symbol})
        df = df.join(df_temp)
        if symbol == 'SPY':  # drop dates SPY did not trade
            df = df.dropna(subset=["SPY"])
    return df

def plot_data(df, title="", set_xlabel="Date", ylabel="Price"):
    """Plot stock prices with a custom title and meaningful axis labels."""
    ax = df.plot(title=title, fontsize=12)
    ax.set_xlabel(set_xlabel)
    ax.set_ylabel(ylabel)
    plt.show()


def compute_daily_returns(df):
    """Compute and return the daily return values."""
    daily_returns = (df / df.shift(1)) - 1
    daily_returns.ix[0, :] = 0
    return daily_returns
```



