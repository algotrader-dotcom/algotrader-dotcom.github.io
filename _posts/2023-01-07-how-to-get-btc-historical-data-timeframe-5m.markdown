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

Here are the valid `period` parameters: `1d,5d,1mo,3mo,6mo,1y,2y,5y,10y,ytd,max`

And these are the valid `interval` parameters: `1m,2m,5m,15m,30m,60m,90m,1h,1d,5d,1wk,1mo,3mo`

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
</pre>