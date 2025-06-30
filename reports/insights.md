# Business Report: E-commerce Customer Analysis (Practice Project)

## 1. Data Source
The data used in this project is from open data sources and is intended solely for practice and demonstration purposes.

## 2. Project Structure
We divided the analysis into three main parts:

### Part 1: Exploratory Data Analysis (EDA)
- **Objective:** Understand the data structure, clean the data, and explore basic attributes such as transaction amounts and feature correlations.

### Part 2: Transaction Analysis

#### Question 1: Are there relationships between 'Payment Method', 'Gender' and 'Total Purchase Amount'?
- Plots and t-tests suggest that customers using credit cards tend to spend differently compared to those using cash or PayPal.
- However, considering credit card transaction fees, higher average purchase amounts may not translate to higher profitability.

#### Question 2: Does the data exhibit seasonality?
- No significant seasonality was found after conducting an F-test.

#### Can returns be predicted based on other features?
- Models tried: Logistic Regression, XGBoost, LightGBM, Random Forest.
- **Result:** All models yielded an AuC around 0.5, indicating no better performance than random guessing.
    - The available features may not provide enough information to predict returns.
    - Returns may be influenced by factors not captured in the dataset, such as customer behavior, product quality, or external market conditions.

### Part 3: Customer-Level Analysis

#### Can customer churn be predicted based on the features?
1. **Step 1:** Transform features into a customer-level DataFrame with unique customer IDs, including:
    - Frequency, total, and average purchase amount by payment method.
    - Count and amount of purchases by product category.
2. **Step 2:** Train and evaluate models to predict customer churn.
3. **Results:**
    - Even after transforming data to customer-level features, models could not predict churn well (AuC 0.5–0.51).
    - Possible reasons:
        - Features may not be sufficient to predict churn.
        - The definition of churn may not be clear or consistent.
        - The dataset may lack enough historical data to capture churn patterns.

#### Can transaction data be segmented with unsupervised learning methods to identify distinct customer groups?
- Although supervised models could not predict churn or returns well, unsupervised learning was explored for customer segmentation.
- **Methods tried:**
    - K-Means
    - Hierarchical Clustering
    - DBSCAN
- **Result:** No clear, meaningful, or actionable customer segments were identified. Clusters mainly differed in Recency, Frequency, and Monetary value, with demographic features not considered.

#### RFM Model Application
- Applied the traditional RFM (Recency, Frequency, Monetary) model to classify customers.
- This segmentation can inform marketing strategies, such as offering different discount levels to each segment.
- Effectiveness can be tested through A/B testing in real-world scenarios.

## Conclusion
While the dataset appears artificial with independent features and clear patterns, it serves as a good practice resource for basic data analysis and modeling. Real-world data is often more complex, but foundational analytical methods remain valuable for exploring and understanding new datasets.