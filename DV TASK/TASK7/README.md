**Student Performance Data Analysis**

**Overview**

This project focuses on analyzing student performance using Python and Pandas. The analysis includes data cleaning, 
categorical feature standardization, statistical analysis of subject scores, calculated performance features, and identification of extreme performance outliers.


**Objectives**

Clean and standardize categorical features. Analyze student performance in Mathematics, Reading, and Writing. 
Calculate statistical measures such as mean, median, standard deviation, and quartiles. Create calculated features for total marks and percentage. Detect extreme performance outliers across subject areas. Understand the overall distribution of student scores. Dataset Dataset: StudentsPerformance.csv

The dataset contains student information and their scores in:

Math Score Reading Score Writing Score

**Categorical Features**

Gender Race/Ethnicity Parental Level of Education Lunch Test Preparation Course

**Technologies Used**
Python Pandas NumPy Matplotlib Google Colab

**Data Cleaning**

The categorical columns were cleaned by:

Removing unwanted spaces using strip() Converting categorical values into lowercase using lower() 
Checking unique values after cleaning Checking for missing values

**Statistical Analysis**

The following statistical measures were calculated for each subject:

Mean Median Standard Deviation Q1 (25th Percentile) Q2 (50th Percentile) Q3 (75th Percentile)

**Conclusion**

This project helps to understand students' academic performance and identify useful patterns from the data.

