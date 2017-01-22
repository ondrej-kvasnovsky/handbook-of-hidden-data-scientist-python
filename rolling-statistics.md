# Rolling Statistics

Rolling, e.g. moving average, means - we create a sliding window, e.g. 20 days, and calculate mean for each window separatelly.

## What statistic to use in order to find when to buy stocks?

We need to find the biggest value from the mean. So, it is rolling standard deviation.

![](/assets/rolling-std.png)

## Bollinger bands ®

Add two more STD moved by some number. When the data crosses one of those curves, we should think about sale or buy.

![](/assets/bollinger-bands.png)

Coding

