---
layout: post
title:  "How to get btc history data timeframe 5m"
date:   2023-01-07 15:37:22 +0700
categories: bitcoin
---
First step: We need to import some required libaries
<pre>
import os
import numpy as np
import pandas as pd
from datetime import date
import pandas_ta as ta
import datetime
import yfinance as yf
</pre>

In this post, we will use yfinance libarary to get bitcoin history data.
Please note that the maximum date range for retrieving minute period data for crypto is 7 days.

Valid `period` parameters: `1d,5d,1mo,3mo,6mo,1y,2y,5y,10y,ytd,max`

Valid `interval` parameters: `1m,2m,5m,15m,30m,60m,90m,1h,1d,5d,1wk,1mo,3mo`

For details about the input parameters for the Yahoo Finance download function, please refer to the documentation.

<pre>
symbol = "BTC-USD"
period = "1d"
interval = "5m"
try:
    df = yf.download(symbol, start=start_date_str, end=today_date_str, period=period, interval=interval, prepost=prepost)
    return df
except:
    print('Error loading stock data for ' + symbols)

print(df)
</pre>

Output: 

<pre>
           Open	High	Low	Close	Adj Close	Volume
Datetime						
2022-12-31 00:00:00+00:00	16603.673828	16608.998047	16603.673828	16608.707031	16608.707031	0
2022-12-31 00:05:00+00:00	16607.683594	16607.683594	16603.171875	16604.455078	16604.455078	11272192
2022-12-31 00:10:00+00:00	16600.306641	16600.306641	16595.078125	16595.078125	16595.078125	27757568
2022-12-31 00:15:00+00:00	16595.263672	16596.105469	16588.130859	16588.130859	16588.130859	18241536
2022-12-31 00:20:00+00:00	16587.199219	16591.791016	16587.199219	16591.367188	16591.367188	13036544
...	...	...	...	...	...	...
2023-01-06 23:35:00+00:00	16963.189453	16963.294922	16958.974609	16958.974609	16958.974609	4855808
2023-01-06 23:40:00+00:00	16954.878906	16955.052734	16952.363281	16952.363281	16952.363281	2331648
2023-01-06 23:45:00+00:00	16952.257812	16960.554688	16950.267578	16960.554688	16960.554688	5063680
2023-01-06 23:50:00+00:00	16960.546875	16961.738281	16958.941406	16958.941406	16958.941406	10934272
2023-01-06 23:55:00+00:00	16955.289062	16955.289062	16953.457031	16953.457031	16953.457031	4553728
2013 rows × 6 columns
</pre>