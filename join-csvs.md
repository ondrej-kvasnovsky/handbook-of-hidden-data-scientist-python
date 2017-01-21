# Join CSVs

Create two CSV files with the following content and name it "AAPL.csv" and "GOOG.csv". It contains stock information for few days. You can get more data on [https://finance.yahoo.com/quote/AAPL/history?p=AAPL. ](https://finance.yahoo.com/quote/AAPL/history?p=AAPL)

```
AAPL.csv

Date,Open,High,Low,Close,Volume,Adj Close
2017-01-20,120.449997,120.449997,119.730003,120.00,29479900,120.00
2017-01-19,119.400002,120.089996,119.370003,119.779999,25295700,119.779999
2017-01-18,120.00,120.50,119.709999,119.989998,23644700,119.989998
2017-01-17,118.339996,120.239998,118.220001,120.00,34078600,120.00
2017-01-13,119.110001,119.620003,118.809998,119.040001,25938300,119.040001
2017-01-12,118.900002,119.300003,118.209999,119.25,27002400,119.25
2017-01-11,118.739998,119.93,118.599998,119.75,27418600,119.75
```

```
GOOG.csv

Date,Open,High,Low,Close,Volume,Adj Close
2017-01-20,806.909973,806.909973,801.690002,805.02002,1645000,805.02002
2017-01-19,805.119995,809.47998,801.799988,802.174988,912000,802.174988
2017-01-18,805.809998,806.205017,800.98999,806.070007,1293300,806.070007
2017-01-17,807.080017,807.140015,800.369995,804.609985,1362100,804.609985
2017-01-13,807.47998,811.223999,806.690002,807.880005,1090100,807.880005
2017-01-12,807.140015,807.390015,799.169983,806.359985,1351000,806.359985
2017-01-11,805.00,808.150024,801.369995,807.909973,1057900,807.909973
```

First, load data only certain data range. That is done by defining what column should be used for indexing, see `index_col`_ parameter in _`read_csv`_ function. Then we provide other parameters for read\_csv function \(check _[_read\_csv documentation_](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.read_csv.html)_ to find out what are these parameters doing\)._

```py
import pandas as pd

def test_run():
    start_date = '2017-01-01'
    end_date = '2017-01-30'

    dates = pd.date_range(start_date, end_date)

    df1 = pd.DataFrame(index=dates)

    dfSPY = pd.read_csv("data/SPY.csv",
                        index_col='Date',
                        parse_dates=True,
                        usecols=['Date', 'Adj Close'],
                        na_values=['nan']
                        )
    dfSPY = dfSPY.rename(columns={'Adj Close': 'SPY'})

    df1 = df1.join(dfSPY, how='inner') # left join by default
    df1 = df1.dropna() # drop rows with NaN values

    symbols = ['GOOG', 'IBM', 'GLD']
    for symbol in symbols:
        df_temp = pd.read_csv("data/{}.csv".format(symbol),
                              index_col='Date',
                              parse_dates=True,
                              usecols=['Date', 'Adj Close'],
                              na_values='nan')
        df_temp = df_temp.rename(columns={'Adj Close': symbol})
        df1 = df1.join(df_temp)
    print df1

if __name__ == "__main__":
    test_run()
```



