# Business Report: E-commerce Customer Analysis (Practice Project)

## 1. Data Source
The data used in this project is from open data sources and is intended solely for practice and demonstration purposes.

## 2. Project Structure
We divided the analysis into three main parts:

### Part 1: Exploratory Data Analysis (EDA)
- **Objective:** Understand the data structure, clean the data, and explore basic attributes such as transaction amounts and feature correlations.
- **Data Preprocessing**: Summary of Steps
    1. Filled missing values in the "Returns" column with zero. Approximately 20% of the rows had missing values, which were assumed to indicate "no return."
    2. Removed duplicate columns. "Customer Age" and "Age" were identical, so "Age" was dropped from the dataset.
    3. Verified the uniqueness of churn values for each customer. We checked whether the churn status of a customer varied over time and found that each customer had a unique churn value, **indicating their churning status remained consistent throughout the data timeframe.**
    4. Converted data types to appropriate formats for each column. For example, "Payment Method" was converted to a categorical type, and "Age" to an integer.
- **[EDA] Descriptive Statistics:** The analysis suggests that the dataset is artificially generated and does not reflect real-world data patterns.
    1. The correlation matrix indicates that most features are independent of each other.
    ![Correlation Matrix](image-2.png)
    2. The distribution of Total Purchase Amount is nearly uniform.
    ![Total Purchase Amount Distribution](image-3.png)

- **Summary:** 
  - Significant efforts were made to ensure data quality and consistency.
    1. Missing values in the "Returns" column were filled with zero, duplicate columns were removed, 
    2. and data types were standardized for each feature.
    3. Additionally, we verified that each customer had a consistent churn status throughout the dataset.
  - These preprocessing steps established a clean and reliable foundation for subsequent analysis, ensuring that the results and insights drawn from the data are based on accurate and well-structured information.

### Part 2: Transaction Analysis

#### Question 1: Are there relationships between 'Payment Method' and 'Total Purchase Amount'?
- Plots and t-tests indicate that customers using credit cards tend to spend differently compared to those using cash or PayPal.
- However, after accounting for credit card transaction fees, higher average purchase amounts may not necessarily lead to increased profitability.
- Average Total Purchase Amount by Payment Method:
![Average Total Purchase Amount by Payment Method](<image-0.png>)

#### Question 2: Does the data exhibit seasonality?
- No significant seasonality was detected based on the F-test results.
- The analysis of total purchase amounts by month shows no substantial variation.
![Total Purchase Amount by Month](image.png)
- ANOVA F-statistic: 0.62, P-value: 0.97  
  This indicates no significant difference in total purchase amounts across months.

#### Question 3: Can returns be predicted based on other features?
- Models evaluated: Logistic Regression, XGBoost, LightGBM, Random Forest.
- **Result:** All models achieved an AuC of approximately 0.5, indicating performance no better than random guessing.
    - The available features may not sufficiently explain or predict returns.
    - Returns could be influenced by factors not captured in the dataset, such as customer behavior, product quality, or external market conditions.
- Model performance comparison:
![Model Performance](image-1.png)

**Summary:**  
The transaction analysis revealed limited relationships between payment methods and purchase amounts, no evidence of seasonality, and no predictive power for returns using the available features. This suggests that the dataset lacks key variables necessary for deeper transactional insights.

#### Question 1: Can customer churn be predicted based on the features?
1. **Step 1:** Transformed the data into a customer-level DataFrame with unique customer IDs, including:
    - Frequency, total, and average purchase amount by payment method.
    - Count and amount of purchases by product category.
2. **Step 2:** Trained and evaluated models to predict customer churn.
3. **Results:**
    - Even after aggregating data to the customer level, models were unable to predict churn effectively (AuC 0.5–0.51).
    - Possible reasons include:
        - Insufficient features to capture churn behavior.
        - An unclear or inconsistent definition of churn.
        - Lack of sufficient historical data to identify churn patterns.
    - ![Churn Model Performance](image-4.png)

#### Question 2: Can transaction data be segmented with unsupervised learning methods to identify distinct customer groups?
- Since supervised models could not predict churn or returns well, unsupervised learning was explored for customer segmentation.
- **Methods applied:**
    - K-Means
    - Hierarchical Clustering
    - DBSCAN
- **Result:** No clear, meaningful, or actionable customer segments were identified. Clusters mainly differed in Recency, Frequency, and Monetary value, with little differentiation based on demographic features.
  - Example of K-Means clustering:
  - Average values for each segment: ![K-Means Segment Averages](image-5.png)
  - Segments primarily differed by total purchases: ![Segment Differences](image-6.png)

#### Question 3: RFM Model Application
- The traditional RFM (Recency, Frequency, Monetary) model was applied to classify customers.
- This segmentation can inform marketing strategies, such as offering different discount levels to each segment.
- The effectiveness of these strategies can be further validated through A/B testing in real-world scenarios.

**Summary:**  
Customer-level analysis revealed that neither supervised nor unsupervised learning methods could effectively predict or segment customer behavior with the available features. However, applying the RFM model provides a practical approach for basic customer segmentation and targeted marketing, even when more advanced methods are limited by the dataset.

## Conclusion

While the dataset appears artificial with independent features and clear patterns, it serves as a valuable resource for practicing fundamental data analysis and modeling techniques. Real-world data is often more complex, but foundational analytical methods remain essential for exploring and understanding new datasets.

This analysis provided a comprehensive review of an e-commerce customer dataset, focusing on data preprocessing, transaction-level insights, and customer-level modeling. Through rigorous data cleaning and validation, we established a reliable foundation for analysis. Our findings indicate that, although the dataset is well-structured, it lacks the depth and complexity of real-world data, which limits the predictive power of both supervised and unsupervised models for returns and churn.

Despite these limitations, the application of traditional segmentation methods such as the RFM model offers practical value for basic marketing strategies. Overall, this project demonstrates essential analytical techniques and highlights the importance of rich, relevant features for advanced predictive modeling in real business scenarios.