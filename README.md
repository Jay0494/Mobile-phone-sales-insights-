 **Project Title:** Driving 2025 Sales: A Data-Driven Strategy for Mr. Chang's Mobile Empire
 **Role:** Freelance Data Analyst
 **Objective:** Provide Mr. Chang, an entrepreneur with mobile phone shops in Pakistan, Bangladesh, Turkey, and India, with data-driven insights from his 2024 sales performance to inform and drive his 2025 sales strategy.

* **POWERBI LINK**:https://app.powerbi.com/3efc99ad-c5bc-4abb-a138-df66ae63a9cf

**Methodology:**
* **Business Understanding:** Collaborated with stakeholders to define key business questions around sales drivers and growth opportunities.
* **Data Preparation (Power Query):** Cleaned raw data, removed irrelevant columns, implemented a star schema (fact/dimension tables), and ensured correct data types.
* **Exploratory Data Analysis (Power BI & Python):** Analyzed overall performance metrics, temporal sales trends, revenue vs. purchase discrepancies, operating system contributions, geographical performance, brand performance, product attribute preferences (color, storage, value segment), and customer demographics.
* **Advanced Analytics (Python):** Conducted correlation studies, identifying a strong positive correlation (0.74) between sales and quantity purchased.
```python
import pandas as pd
import numpy as np

df = pd.read_excel(r"C:\Users\User\Downloads\Onyx Data - DataDNA Dataset Challenge - Mobile Phone Sales Dataset - May 2025.xlsx")


pd.set_option('display.max_columns', None)

df.info()


df.describe()
df.head(4)

# remove unwanted columns 
df = df.drop(['End of Month', 'Latitude', 'Longitude'], axis =1)
print(df)

df.head()
df.info()
# import libraries for statistical analysis
import scipy.stats as stats
import seaborn as sns 
import matplotlib.pyplot as plt

# Calculate Pearson correlation
corr, p_value = stats.pearsonr(df['Total_Revenue'], df['Units_Sold'])

# Print results
print(f"Pearson correlation coefficient: {corr:.4f}")
print(f"P-value: {p_value:.10f}")

if p_value < 0.05:
    print("There is a statistically significant correlation between Revenue and Quantity sold.")
else:
    print("There is no statistically significant correlation between revenue and quantity sold.")

# Plotting with consistent column names
sns.lmplot(x="Units_Sold", y="Total_Revenue", data=df, aspect=1.5)
plt.title(f"Sales vs Quantity (r={corr:.2f})")
plt.show()
```

**Key Insights:**

![Screenshot_20250525-190500_Power BI](https://github.com/user-attachments/assets/8d95056b-194b-4054-b25d-3725fb8bd436)

* **Strong Growth Months:** May, July, October (peak +32.01%), and December showed significant sales increases.
* **Sales Decline:** September experienced the greatest sales drop (-20.9%).
* **Revenue Discrepancy:** Increased purchases in March, April, and August did not correspond with revenue growth, suggesting issues with product mix or discounting.

![Screenshot_20250525-190632_Power BI](https://github.com/user-attachments/assets/7d8c03b5-572e-40ac-bc4c-2cdfa18e377b)

* **OS Dominance:** Android contributed 74.9% of revenue; iOS 25.08%.
* **Geographical Performance:** India (47.98%) and Turkey (37.33%) were top revenue contributors, while Pakistan (2.63%) and Bangladesh (12.06%) lagged.

![Screenshot_20250525-190714_Power BI](https://github.com/user-attachments/assets/03c8c9c2-680d-429e-b93a-95c0d51a8460)


* **Brand Performance:** Apple led in revenue (25.08%), while Xiaomi contributed the least (12.53%).
* **Product Preferences:** Black phones (22.4%) were most purchased. 128GB storage generated most revenue (34.9%), but 256GB and 64GB had higher purchase volumes. Medium (43.9%) and low-valued (44.46%) phones dominated purchases.
* **Customer Demographics:** Customers aged 26-33 were the primary purchasers, with females making up 50% of the customer base.

**Recommendations:**
Provided actionable recommendations focusing on:
* Capitalizing on peak sales months and mitigating dips.
* Optimizing product mix and pricing strategies to align revenue with purchase volume.
* Strategic growth in underperforming regions and leveraging top markets.
* Tailoring marketing to key demographics and product preferences.
* Ensuring optimal inventory based on sales-quantity correlation.

**Impact:** Transformed raw sales data into a clear, actionable roadmap, enabling Mr. Chang to make informed strategic decisions for sustained growth and increased profitability in 2025.
