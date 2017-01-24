# Two Histograms on One Chart

If we want to compare two histograms, we need to plot then on one chart. Here is how to do it. We are using 'util.py' we have create in previous chapter. 

```
import pandas as pd
import matplotlib.pyplot as plt
from util import get_data, plot_data, compute_daily_returns

def test_run():
    dates = pd.date_range('2009-01-01', '2012-12-31')
    symbols = ['SPY', 'XOM']
    df = get_data(symbols, dates)
    plot_data(df)

    daily_returns = compute_daily_returns(df)
    plot_data(daily_returns, title="Daily returns", ylabel="Daily returns")

    daily_returns['SPY'].hist(bins=20, color='c', label="SPY")
    daily_returns['XOM'].hist(bins=20, color='b', label="XOM")

    plt.legend(loc="upper right")
    plt.show()

if __name__ == "__main__":
    test_run()
```

Here are the two histograms on one chart. 



