# Stocks
 Repo for analyzing historical stock and market data
 
 ### Data sources:
 - Yahoo Finanance API
 - I built a function to access yahoo finance through the python `yfinance` module and return a pandas dataframe with OHLCV (open, high, low, close, volume) data:  
```python
def get_yf_data(ticker, start='2018-01-01', end=date.today()):
    '''
    Calls Yahoo Finance API and retrieves historical data for given ticker and time period
    
    Args:
        ticker(string): string, stock ticker
        start (string): start date, default 2018-01-01
        end (datetime object): end date, default today's date
        
    Returns:
        pandas.DataFrame: new pandas dataframe with the OHLC data for the given ticker and time period
    '''
    # get historical data
    temp = yf.Ticker(ticker)
    df = temp.history(start=start, end=end)
    # make columns lowercase (compatibility with technical_indicators_lib)
    df.columns = map(str.lower, df.columns)
    df.is_copy = False
    
    return df
```

 
 ### Technical Indicators:
 - https://github.com/kunalkini15/technical_indicators_lib/blob/master/technical_indicators_lib/indicators.py

### Analysis
- So far I have modified the above technical indicators library and used it to calculate dozens of additional data features for several indices and individual stocks
- I used `plotly` to plot candlestick charts for various tickers

### Next Steps
- I plan to build a back tester and use it to test and implement various ML-powered investing strategies, with the big picture goal being to automate a portion of my portfolio
