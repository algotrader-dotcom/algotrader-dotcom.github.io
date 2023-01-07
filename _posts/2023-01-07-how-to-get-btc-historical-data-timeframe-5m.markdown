---
layout: post
title:  "How to get bitcoin historical data timeframe 5m"
date:   2023-01-07 15:37:22 +0700
categories: bitcoin
---
First, let’s go ahead and import a few Python libraries. If you don’t have these libs installed, now would be a great time to go ahead and do so.

<code>
import os
import numpy as np
import pandas as pd
from datetime import date
import pandas_ta as ta
import datetime
import yfinance as yf
</code>
Next, we will be calling the yfinance function ‘download()’ with parameters for start date, end date, period, interval and prepost market.

Please note that the maximum date range for retrieving minute period data for crypto is 7 days.

Here are the valid period parameters:

1d,5d,1mo,3mo,6mo,1y,2y,5y,10y,ytd,max
And these are the valid interval parameters:

1m,2m,5m,15m,30m,60m,90m,1h,1d,5d,1wk,1mo,3mo
For details about the input parameters for the Yahoo Finance download function, please refer to the documentation.

This is the function that performs the downloads based on the input parameters.

<code>
try:
    df = yf.download(symbol, start=start_date_str, end=today_date_str, period=period, interval=interval, prepost=prepost)
    #  Add symbol
    df["Symbol"] = symbol
    return df
except:
    print('Error loading stock data for ' + symbols)
</code>