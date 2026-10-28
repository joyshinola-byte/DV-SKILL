**Shopify Stock Visualization, Time-Series Analysis & Financial Insight**

**Project Overview**

This project focuses on visualizing and analyzing stock market data using Python. The dataset contains stock information such as Date, Open, High, Low, Close, and Volume.

For this project, the provided Excel spreadsheet contains **AAPL stock data**. The data is analyzed using Pandas, Matplotlib, and Seaborn in Google Colab.

The main purpose of this project is to understand stock price movement, trading volume, moving averages, daily returns, and high-volatility periods through visualization and basic statistical analysis.

**Objectives**

The main objectives of this project are:

* To visualize Open, High, Low, and Close stock prices over time.
* To visualize trading volume over time.
* To calculate and plot 20-day and 50-day moving averages.
* To calculate daily percentage returns.
* To generate histogram and KDE plots for daily returns.
* To understand the distribution of stock returns.
* To calculate mean, variance, and standard deviation of daily returns.
* To identify high-volatility periods.
* To prepare a simple financial summary of the stock.



## Dataset

### Dataset Used

**AAPL Stock Data**

**File Name**

`AAPL.xlsx`

**Main Columns**

* **Date** – Date of the stock record
* **Open** – Opening stock price
* **High** – Highest price during the day
* **Low** – Lowest price during the day
* **Close** – Closing stock price
* **Volume** – Number of shares traded



**Tools and Technologies**

* Python
* Google Colab
* Pandas
* Matplotlib
* Seaborn
* Microsoft Excel



**Data Loading**

The Excel dataset is loaded using Pandas.

```python
import pandas as pd

df = pd.read_excel('/content/drive/MyDrive/DV SKILL /AAPL.xlsx')
```

---

**1. OHLC Price Visualization**

Line plots are created for Open, High, Low, and Close prices.

This helps to understand how the stock price changes over time.

```python
plt.plot(df['Date'], df['Open'], label='Open')
plt.plot(df['Date'], df['High'], label='High')
plt.plot(df['Date'], df['Low'], label='Low')
plt.plot(df['Date'], df['Close'], label='Close')
```

---

**2. Trading Volume Visualization**

Trading volume is plotted over time to understand the changes in the number of shares traded.

```python
plt.plot(df['Date'], df['Volume'])
```

High trading volume can indicate increased market activity during particular periods.

---

**3. Moving Average Analysis**

20-day and 50-day moving averages are calculated using the daily closing price.

```python
df['MA20'] = df['Close'].rolling(20).mean()
df['MA50'] = df['Close'].rolling(50).mean()
```

The moving averages are plotted along with the daily closing price.

Moving averages help to understand the general trend of the stock price.

---

**4. Daily Percentage Return**

Daily percentage return is calculated using the closing price.

```python
df['Daily_Return'] = df['Close'].pct_change() * 100
```

Daily return shows the percentage change in the stock price from one trading day to the next.

---

**5. Histogram and KDE Plot**

A histogram and KDE plot are generated for daily returns.

```python
sns.histplot(df['Daily_Return'].dropna(), bins=30, kde=True)
```

The histogram shows the frequency of daily returns, while the KDE curve shows the overall distribution pattern.

This helps to check whether the returns are approximately normally distributed or have a wider/fat-tailed distribution.

---

**6. Financial Summary**

The following statistical values are calculated:

**Mean Return**

Mean return shows the average daily return of the stock.

**Variance**

Variance shows how much the daily returns vary around the mean.

**Standard Deviation**

Standard deviation measures the spread or volatility of daily returns.

```python
print("Mean Return:", df['Daily_Return'].mean())
print("Variance:", df['Daily_Return'].var())
print("Standard Deviation:", df['Daily_Return'].std())
```

---

**7. High-Volatility Periods**

High-volatility days are identified using the standard deviation of daily returns.

```python
volatility_limit = df['Daily_Return'].std()

high_volatility = df[
    abs(df['Daily_Return']) > volatility_limit
]

These periods show days where the stock return changed more than the calculated standard deviation.

A line plot is also used to visualize daily returns and identify high-volatility periods.

**Financial Insight**

The analysis provides information about:

* Overall stock price movement
* Trading activity
* Short-term and medium-term price trends
* Average daily return
* Return variation
* Stock volatility
* High-volatility trading periods
* Daily return distribution

The moving averages help in understanding the stock trend, while the return distribution and standard deviation help in understanding the stability and volatility of the stock.

**Conclusion**

This project helped to understand AAPL stock data using visualization and basic statistical analysis.

OHLC and volume line plots show the stock price and trading activity over time. The 20-day and 50-day moving averages help to understand price trends. The histogram and KDE plots show the distribution of daily returns. Mean, variance, and standard deviation provide basic information about stock return behavior.

The high-volatility analysis helps to identify periods when the daily stock return showed larger changes.

Overall, this project provides a simple visualization-based understanding of stock price movement, return distribution, and volatility.

