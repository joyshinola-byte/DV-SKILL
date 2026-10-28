# AAPL Stock Data Understanding & Exploratory Analysis

## Project Overview

This project focuses on understanding and exploring **Apple Inc. (AAPL) stock market data** using Python. The dataset contains daily stock price information such as Open, High, Low, Close, and Volume.

The project uses **Pandas** for data handling and **Matplotlib** for data visualization.

## Objectives

The main objectives of this project are:

* To load the AAPL stock dataset.
* To understand the structure of the dataset.
* To examine the first and last records.
* To check the number of rows and columns.
* To identify the available columns.
* To understand the data types and dataset information.
* To visualize Open, High, Low, and Close prices.
* To visualize the trading volume.
* To calculate and visualize 20-day and 50-day moving averages.
* To understand the overall stock price movement.

## Technologies Used

* **Python**
* **Google Colab**
* **Pandas**
* **Matplotlib**
* **Microsoft Excel** for the input dataset

## Dataset

The project uses an **AAPL stock dataset** stored in Excel format.

The dataset contains the following important attributes:

| Column | Description                  |
| ------ | ---------------------------- |
| Date   | Date of stock trading        |
| Open   | Opening price of the stock   |
| High   | Highest price during the day |
| Low    | Lowest price during the day  |
| Close  | Closing price of the stock   |
| Volume | Number of shares traded      |

## Data Loading

The dataset is loaded using Pandas:

```python
df = pd.read_excel('/content/drive/MyDrive/DV SKILL /AAPL.xlsx')
```

## Data Understanding

The following functions are used to understand the dataset:

```python
df.head()
df.tail()
df.shape
df.columns
df.info()
```

These functions help to view the records, identify the size of the dataset, check column names, and understand the data types.


**Data Visualization**

**1. AAPL OHLC Prices**

The Open, High, Low, and Close prices are plotted to understand the daily stock price movement.

plt.plot(df['Date'], df['Open'], label='Open')
plt.plot(df['Date'], df['High'], label='High')
plt.plot(df['Date'], df['Low'], label='Low')
plt.plot(df['Date'], df['Close'], label='Close')

**2. Trading Volume**

Trading volume is visualized to understand how the number of traded shares changes over time.

plt.plot(df['Date'], df['Volume'])

**3. Moving Averages**

Two moving averages are calculated:

20-Day Moving Average
50-Day Moving Average
df['MA20'] = df['Close'].rolling(20).mean()
df['MA50'] = df['Close'].rolling(50).mean()

Moving averages help to observe the general direction of the closing price over different time periods.

**Project Output**

The project produces the following visualizations:

AAPL OHLC Price Chart
AAPL Trading Volume Chart
AAPL Closing Price with 20-Day and 50-Day Moving Averages

These visualizations help in understanding stock price and trading volume patterns.

**Conclusion**

This project provides a basic exploratory analysis of AAPL stock data. The analysis helps to understand the dataset structure, stock price movements, trading volume, and moving average trends.

The project can be further extended by calculating daily price change, daily percentage return, return distribution, mean, variance, standard deviation, and detecting anomalous trading days.
