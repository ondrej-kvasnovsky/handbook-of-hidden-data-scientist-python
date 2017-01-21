# Read CSV

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

## Read and print all rows

Read all rows from CSV and print it out.

```
import pandas as pd

def test_run():
    df = pd.read_csv("data/AAPL.csv")
    print df

if __name__ == "__main__":
    test_run()
```

Here is the output when we run the code above. 

```
         Date        Open        High         Low       Close    Volume    Adj Close  
0  2017-01-20  120.449997  120.449997  119.730003  120.000000  29479900   120.000000  
1  2017-01-19  119.400002  120.089996  119.370003  119.779999  25295700   119.779999
2  2017-01-18  120.000000  120.500000  119.709999  119.989998  23644700   119.989998 
3  2017-01-17  118.339996  120.239998  118.220001  120.000000  34078600   120.000000
4  2017-01-13  119.110001  119.620003  118.809998  119.040001  25938300   119.040001
5  2017-01-12  118.900002  119.300003  118.209999  119.250000  27002400   119.250000
6  2017-01-11  118.739998  119.930000  118.599998  119.750000  27418600   119.750000 
```

## Read header, tail or range

Read only header, first two rows or specified range.

```
import pandas as pd

def test_run():
    df = pd.read_csv("data/AAPL.csv")
    print df.head(n=1)
    print df.tail(n=2)
    print df[2:3]

if __name__ == "__main__":
    test_run()
```

Here is the output. 

```
         Date        Open        High         Low  Close    Volume  Adj Close
0  2017-01-20  120.449997  120.449997  119.730003  120.0  29479900      120.0

         Date        Open        High         Low       Close    Volume    Adj Close
5  2017-01-12  118.900002  119.300003  118.209999  119.250000  27002400   119.250000
6  2017-01-11  118.739998  119.930000  118.599998  119.750000  27418600   119.750000 

         Date   Open   High         Low       Close    Volume   Adj Close
2  2017-01-18  120.0  120.5  119.709999  119.989998  23644700  119.989998
```



