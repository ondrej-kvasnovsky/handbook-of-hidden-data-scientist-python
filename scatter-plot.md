# Scatter Plot

We are going to observe correlations and slope in this article. Notice how price changes for GLD on this chart. When you compare SPY vs XOM, there should be high slope and high correlation in the scatter chart. On the other hand, there should be lower slope and lower correlation for SPY vs GLD.

![](/assets/scatter-1.png)

Here is the code to generate two scatter charts for both situations.

```
import pandas as pd
import matplotlib.pyplot as plt
import numpy as np
from util import get_data, plot_data, compute_daily_returns

def test_run():
    dates = pd.date_range('2009-01-01', '2012-12-31')
    symbols = ['SPY', 'XOM', 'GLD']
    df = get_data(symbols, dates)
    plot_data(df)

    daily_returns = compute_daily_returns(df)
    plot_data(daily_returns, title="Daily returns", ylabel="Daily returns")

    daily_returns.plot(kind='scatter', x='SPY', y='XOM')
    beta_XOM, alpha_XOM = np.polyfit(daily_returns['SPY'], daily_returns['XOM'], 1)
    plt.plot(daily_returns['SPY'], beta_XOM * daily_returns['SPY'] + alpha_XOM, '-', color='r')
    plt.show()

    daily_returns.plot(kind='scatter', x='SPY', y='GLD')
    beta_GLD, alpha_GLD= np.polyfit(daily_returns['SPY'], daily_returns['GLD'], 1)
    plt.plot(daily_returns['SPY'], beta_GLD * daily_returns['SPY'] + alpha_GLD, '-', color='r')
    plt.show()

    # calculate correlation coefficient
    print daily_returns.corr(method='pearson')

if __name__ == "__main__":
    test_run()
```

Here is SPY vs XOM. Angle of the regression line is quite high, that means high slope. Distrubtion of points is kind of around the regression line, which means higher correlation.

![](/assets/scatter-high-slope-low-correlation.png)

Here is SPY vs GLD. Low slope \(angle of the linear regression line\) and distrubution of points is all over the chart, which means low correlation.

![](/assets/scatter-low-slope.png)

Here is the correlation in numbers. If we want to see correlation in numbers,  we can use `daily_returns.corr(method='pearson')` from NumPy.

```
SPY       XOM       GLD
SPY  1.000000  0.821369  0.076348
XOM  0.821369  1.000000  0.080527
GLD  0.076348  0.080527  1.000000
```



