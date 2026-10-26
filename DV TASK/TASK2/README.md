TASK 2

Retail Sales Visualization, Relationship Analysis & Business Insights

1. Project Overview
This project analyzes a retail sales dataset using Python and data visualization techniques. The main focus is to understand sales, profit, discount, product categories, and relationships between numerical variables.

2. Libraries Used
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

Explanation
Pandas is used for data loading and data analysis.
NumPy is used for numerical operations.
Matplotlib is used to create basic plots.
Seaborn is used for statistical visualizations.

4. Loading the Dataset
df = pd.read_csv("/content/drive/MyDrive/big data analysis/samplesuperstore.csv")
Explanation
The Sample Superstore CSV file is loaded using Pandas and stored in the DataFrame df.

The dataset contains 10,194 records and initially has 21 columns.

4. Viewing the Dataset
df.head()

Explanation
head() displays the first five rows of the dataset. It helps understand the structure and type of information available.

The dataset contains fields such as Order ID, Order Date, Ship Date, Customer information, Region, Category, Sales, Quantity, Discount, and Profit.

5. Dataset Information
df.info
Explanation
This is used to inspect the DataFrame information, including columns and data types.

6. Descriptive Statistics
df.describe()
Explanation
describe() provides statistical information for numerical columns such as:

Count
Mean
Standard deviation
Minimum
25th percentile
Median
75th percentile
Maximum
The average Sales is approximately 228.23 and the average Profit is approximately 28.67.

7. Date Conversion
df["Order Date"] = pd.to_datetime(df["Order Date"])
df["Ship Date"] = pd.to_datetime(df["Ship Date"])
Explanation
The Order Date and Ship Date columns are converted into datetime format so that date-based calculations can be performed.

8. Checking Data Types
df.dtypes
Explanation
This code displays the data type of every column.

After conversion, Order Date and Ship Date are stored as datetime values, while Sales, Discount, and Profit are numerical values.

9. Creating Delivery Days
df["Delivery Days"] = (df["Ship Date"] - df["Order Date"]).dt.days
Explanation
A new column called Delivery Days is created by calculating the number of days between the Order Date and Ship Date.

This helps analyze delivery duration.

10. Checking Product Categories
print(df["Category"].unique())
Output
['Office Supplies' 'Furniture' 'Technology']
Explanation
This identifies the unique product categories available in the dataset.

The three categories are:

Office Supplies
Furniture
Technology
11. Checking Missing Values
print(df.isnull().sum())
Explanation
This checks the number of missing values in every column.

The analysis shows that there are no missing values in the dataset.

Part 1: Sales Analysis and Bar Plots
12. Sales Distribution
plt.figure(figsize=(6,4))
plt.hist(df["Sales"], bins=20)
plt.title("Distribution of Sales")
plt.xlabel("Sales")
plt.ylabel("Frequency")
plt.show()
OUTPUT: image

Explanation
A histogram is used to understand how Sales values are distributed across the dataset.

bins=20 divides the Sales values into 20 groups.

Analysis
This visualization helps understand the frequency and distribution of sales values.

13. Total Sales by Category
category_sales = df.groupby("Category")["Sales"].sum()
print(category_sales)
Explanation
groupby() groups the data according to Category and sum() calculates the total Sales for each category.

Result
Furniture          754747.7613
Office Supplies    731893.3140
Technology         839893.2790
Analysis
Technology has the highest total sales among the three categories.

14. Sales by Category Bar Plot
plt.figure(figsize=(6,4))
plt.bar(category_sales.index, category_sales.values)
plt.title("Sales by Category")
plt.xlabel("Category")
plt.ylabel("Sales")
plt.show()
OUTPUT: image

Explanation
This bar chart visually compares total sales between Furniture, Office Supplies, and Technology.

Analysis
Technology has the highest sales compared with the other categories.

15. Profit by Category
sns.barplot(
    data=df,
    x="Category",
    y="Profit"
)

plt.title("Profit by Category")
plt.xlabel("Category")
plt.ylabel("Profit")
plt.show()
OUTPUT:

image
Explanation
This Seaborn bar plot compares Profit across different product categories.

x="Category" displays categories on the X-axis.
y="Profit" displays profit on the Y-axis.
sns.barplot() creates the bar plot.
Analysis
This visualization helps compare the profitability of different product categories.

16. Sales Distribution by Category
sns.barplot(
    data=df,
    x="Category",
    y="Sales"
)

plt.title("Sales Distribution by Category")
plt.show()
OUTPUT: image

Explanation
This bar plot compares sales across different product categories.

data=df uses the retail sales dataset.
x="Category" displays product categories.
y="Sales" displays sales values.
sns.barplot() creates the bar plot.
Analysis
This visualization helps identify which product category has higher sales.

Part 2: Box Plots
17. Profit Distribution
sns.boxplot(
    data=df,
    y="Profit"
)

plt.title("Profit Distribution")
plt.ylabel("Profit")
plt.show()
OUTPUT:

image
Explanation
This box plot shows the overall distribution of profit values.

It helps identify:

Median
Spread of profit values
Variation
Outliers
Analysis
This visualization helps understand how profit values are distributed and whether there are unusual profit values.

18. Profit Variation Across Categories
sns.boxplot(
    data=df,
    x="Category",
    y="Profit"
)

plt.title("Profit Variation Across Categories")
plt.xlabel("Category")
plt.ylabel("Profit")
plt.show()
OUTPUT: image

Explanation
This box plot compares profit distribution across different product categories.

x="Category" displays categories on the X-axis.
y="Profit" displays profit values on the Y-axis.
Each box represents the profit distribution of a category.
Analysis
This visualization helps compare profitability, variation, median values, and outliers across categories.

Part 3: Discount vs Profit Analysis
19. Checking Discount Levels
df["Discount"].unique()
Explanation
This code displays all the unique discount levels available in the dataset.

Analysis
It helps identify the different discount values used in the sales records.

20. Impact of Discount on Profit
sns.scatterplot(
    data=df,
    x="Discount",
    y="Profit"
)

plt.title("Impact of Discount on Profit")
plt.show()
OUTPUT: image

Explanation
This scatter plot is used to analyze the relationship between Discount and Profit.

x="Discount" represents the discount level.
y="Profit" represents the profit.
Each point represents a sales record.
sns.scatterplot() creates the scatter plot.
Analysis
The visualization helps understand how profit changes at different discount levels.

It can be used to identify whether higher discounts are associated with lower profit and to observe the impact of discounting on profitability.

Part 4: Correlation Heatmap
21. Selecting Numerical Attributes
numeric_df = df.select_dtypes(
    include="number"
)
Explanation
This code selects only the numerical columns from the dataset.

Numerical attributes are required for correlation analysis because correlation is calculated between numerical variables.

22. Creating Correlation Matrix
corr = numeric_df.corr()
Explanation
The corr() function calculates the correlation between all selected numerical attributes.

Correlation shows the strength and direction of the relationship between numerical variables.

23. Correlation Heatmap
sns.heatmap(
    corr,
    annot=True
)

plt.title("Correlation Heatmap")
plt.show()
OUTPUT: image

Explanation
This heatmap provides a visual representation of the correlation matrix.

corr contains the calculated correlation values.
annot=True displays the correlation values inside the heatmap.
sns.heatmap() creates the heatmap.
Analysis
The correlation heatmap helps identify relationships between numerical attributes such as Sales, Quantity, Discount, and Profit.

24. Overall Analysis
The project uses bar plots, box plots, scatter plots, and a correlation heatmap to analyze retail sales data.

The analysis focuses on:

Sales distribution across categories
Total sales by category
Profit by category
Overall profit distribution
Profit variation across categories
Different discount levels
Impact of discount on profit
Correlation between numerical attributes
Delivery duration using Delivery Days

25. Business Insights
Technology has the highest total sales among the three categories.
Sales performance varies across different categories.
Profit distribution contains variation and outliers.
Profitability can be compared across product categories.
Different discount levels can have different effects on profit.
Higher discounts may affect profitability and should be analyzed carefully.
Correlation analysis helps identify relationships between numerical business attributes.

27. Conclusion
This project demonstrates how Python, Pandas, Matplotlib, and Seaborn can be used for retail sales analysis.

The project covers data loading, data exploration, preprocessing, sales analysis, bar plots, box plots, discount versus profit analysis, and correlation heatmap analysis.

These visualizations provide useful insights into sales performance, profit distribution, category-wise profitability, discount impact, and relationships between numerical variables.
