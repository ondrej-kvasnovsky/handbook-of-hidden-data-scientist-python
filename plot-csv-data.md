# Plot and Normalize CSV Data

Create CSV file with the following content and name it "AAPL.csv". It contains stock information for few days. You can get more data on [https://finance.yahoo.com/quote/AAPL/history?p=AAPL. ](https://finance.yahoo.com/quote/AAPL/history?p=AAPL)

```
Date,Open,High,Low,Close,Volume,Adj Close
2017-01-20,120.449997,120.449997,119.730003,120.00,29479900,120.00
2017-01-19,119.400002,120.089996,119.370003,119.779999,25295700,119.779999
2017-01-18,120.00,120.50,119.709999,119.989998,23644700,119.989998
2017-01-17,118.339996,120.239998,118.220001,120.00,34078600,120.00
2017-01-13,119.110001,119.620003,118.809998,119.040001,25938300,119.040001
2017-01-12,118.900002,119.300003,118.209999,119.25,27002400,119.25
2017-01-11,118.739998,119.93,118.599998,119.75,27418600,119.75
```

# Plot data

REad AAPL.csv file and pick 'Close' and 'Adj Close' column to plot. Then show the plot.

```
import pandas as pd
import matplotlib.pyplot as plt

def test_run():
    df = pd.read_csv("data/AAPL.csv")
    df[['Close', 'Adj Close']].plot()
    plt.show()

if __name__ == "__main__":
    test_run()
```

Here is the output. 

![](/assets/Screen Shot 2017-01-21 at 9.50.57 AM.png)

# Normalize data

We need normalize data in order to have all the values starting from the same point, so we can measure difference easily. 

```
import pandas as pd
import matplotlib.pyplot as plt

def test_run():
    df = pd.read_csv("data/AAPL.csv")
    twoColumnsDf = df[['Close', 'Adj Close']]
    twoColumnsDf = normalize_data(twoColumnsDf)
    twoColumnsDf.plot()
    plt.show()

def normalize_data(df):
    return df / df.ix[0, :]

if __name__ == "__main__":
    test_run()
```

Here is the output. Now you can see how stocks differ from each other because both lines start from 1. Better example would be to compare 'Adj Close' for multiple datasets \(like AAPL, GOOG, GLD, etc.\).

![](/assets/csv-pandas-normalized.png)

