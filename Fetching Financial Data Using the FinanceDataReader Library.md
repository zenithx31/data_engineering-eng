# 📚 What is FinanceDataReader?

FinanceDataReader is a Python library that helps you easily collect and analyze financial data.

With this library, you can retrieve a wide range of financial data including:
- Korean stock prices
- US stock prices
- Cryptocurrency prices
- Commodity futures
- Various indices
- Exchange rates
- Stock listings and more

---

## 📚 Installation

To install FinanceDataReader, make sure Python and pip are installed.  
Then, run the following command:

```bash
$ pip install -U finance-datareader
```

---

## 📚 Getting Stock Listings

### 1. Get all listed stocks on the Korean Exchange

```python
import FinanceDataReader as fdr

df_sample = fdr.StockListing('KRX')
print(df_sample)
```

### 2. Filter specific stock (e.g., Samsung Electronics)

```python
import FinanceDataReader as fdr

df_sample1 = fdr.DataReader(symbol='005930', start='2023') # From 2023 to present
df_sample2 = fdr.DataReader(symbol='005930', start='20230101', end='20231031') # From Jan 1 to Oct 31, 2023
df_sample3 = fdr.DataReader(symbol='005930') # From listing date to present
print(df_sample1.head())
print(df_sample2.head())
print(df_sample3.head())
```

---

### 3. Get S&P 500 company listings

```python
import FinanceDataReader as fdr

df_sp500 = fdr.StockListing('S&P500')
print(df_sp500)
```

---

### 4. Plot stock price graph (e.g., Samsung Electronics)

```python
import FinanceDataReader as fdr
import matplotlib.pyplot as plt

df_sample = fdr.DataReader(symbol='005930') # Samsung Electronics

df_sample['Close'].plot()
plt.show()
```

---

## 📚 Full Listings - `StockListing()` function

Available stock listings using `StockListing()`:

- **Korea Exchange**: ‘KRX’, ‘KOSPI’, ‘KOSDAQ’, ‘KONEX’, ‘KRX-DELISTING’, ‘KRX-ADMINSTRATIVE’
- **US Exchanges**: ‘NASDAQ’, ‘NYSE’, ‘AMEX’, ‘S&P500’
- **Global Exchanges**: ‘SSE’, ‘SZSE’, ‘HKEX’, ‘TSE’, ‘HOSE’, etc.

---

## 📚 Price Data - `DataReader()` function

Available price data using `DataReader()`:

- **Korean stocks**: ‘005930’, ‘000660’, ‘068270’
- **US stocks**: ‘AAPL’, ‘AMZN’, ‘GOOG’
- **Korean indices**: ‘KS11’, ‘KQ11’, ‘KS200’
- **US indices**: ‘DJI’, ‘IXIC’, ‘US500’, ‘RUT’, ‘VIX’
- **Exchange rates** (supported: ‘KRW’, ‘EUR’, ‘CNY’, ‘JPY’, ‘CHF’):  
  ‘USD/KRW’, ‘USD/EUR’, ‘CNY/KRW’, ‘EUR/CNY’
- **Cryptocurrencies** (supported: ‘BTC’, ‘ETH’, ‘USDT’, ‘BNB’, ‘USDC’, ‘XRP’, ‘BUSD’, ‘ADA’, ‘SOL’, ‘DOGE’):  
  ‘BTC/USD’, ‘BTC/KRW’, ‘ETH/USD’, ‘ETH/KRW’
- **Commodities**: ‘CL=F’, ‘BZ=F’, ‘NG=F’, ‘GC=F’, ‘SI=F’, ‘HG=F’
- **Others**: ‘ETF/KR’, ‘US5YT’

---

## 🔗 References

- ▶ **[FinanceDataReader User Guide](https://financedata.github.io/posts/finance-data-reader-users-guide.html)**
- ▶ **[FinanceDataReader API Info (GitHub)](https://github.com/FinanceData/FinanceDataReader/wiki/)**
