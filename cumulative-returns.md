# Cumulative Returns



![](/assets/cumulative-return.png)

```
import os
import pandas as pd
import matplotlib.pyplot as plt

def symbol_to_path(symbol, base_dir="data"):
    return os.path.join(base_dir, "{}.csv".format(str(symbol)))

def get_data(symbols, dates):
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

def plot_data(df, title="Stock prices", xlabel="Date", ylabel="Price"):
    ax = df.plot(title=title, fontsize=12)
    ax.set_xlabel(xlabel)
    ax.set_ylabel(ylabel)
    plt.show()

def compute_cumulative_returns(df):
    return ((df / df.ix[0].values) - 1)

def test_run():
    dates = pd.date_range('2012-01-01', '2012-12-31')  # one month only
    symbols = ['SPY', 'XOM']
    df = get_data(symbols, dates)
    plot_data(df)

    daily_returns = compute_cumulative_returns(df)
    plot_data(daily_returns, title="Cumulative returns", ylabel="Cumulative returns")

if __name__ == "__main__":
    test_run()
```

Here is the chart with original data. 

![](/assets/cumulative-original-data.png)

And here is the one showing cumulative percentage.

![](/assets/cumulative-percentage.png)

