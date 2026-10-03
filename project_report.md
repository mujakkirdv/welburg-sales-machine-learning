# Welburg Sales Machine Learning Project
## Customer Type Classification, Credited Amount Regression & Customer Segmentation

**Student:** Mujakkir Ahmad  
**Registration No.:** 25868400020  
**Program:** Post Graduate Diploma in Data Analytics  
**Institution:** National University, Bangladesh  
**Course:** Fundamentals of Machine Learning  
**Academic Year:** 2025–2026  
**Programming:** Python 3.12.0  
**Dataset:** `welburg_sales_dataset_2025.xlsx`

---

## Abstract

This project applies fundamental machine learning techniques to Welburg sales transaction data to investigate customer behavior and sales-related business problems. The notebook contains 5,000 transaction records and 18 original columns covering the full period from January to December 2025. Three machine learning tasks were developed. First, supervised classification was used to predict Customer Type across Retailer, Wholesale, Dealer, Corporate, and Online categories. Six classification algorithms were compared: K-Nearest Neighbors, Decision Tree, Random Forest, Naive Bayes, Support Vector Machine, and Neural Network. Second, supervised regression was used to estimate Credited Amount using Linear Regression, Decision Tree Regressor, and Random Forest Regressor. Third, unsupervised K-Means clustering was applied to customer-level aggregated transaction features for customer segmentation. The data was checked for missing values and duplicates, date features were engineered, identifiers and free-text fields were excluded from baseline models, and numerical and categorical preprocessing was implemented through pipelines. The best classification model by weighted F1 was Decision Tree (0.4793), while Linear Regression produced the strongest regression performance with an R² of 0.6991 and RMSE of 49,940.92. K-Means selected two clusters with a silhouette score of 0.3229. The results demonstrate how practical sales data can be transformed into an academic machine learning workflow for classification, prediction, and segmentation.

---

# 1. Introduction and Business Problem

Welburg sales transactions contain customer, sales, payment, geographic, and operational information. My practical experience with Welburg Metal involved sales and account-related activities and handling information associated with customers and sales executives. This business context motivated the use of machine learning to explore whether transaction characteristics can support customer classification, credited-amount estimation, and customer segmentation.

The project addresses three questions:

1. **Classification:** Can the customer type be predicted from transaction characteristics?
2. **Regression:** Can the credited amount be estimated from available transaction characteristics?
3. **Segmentation:** Can customers be grouped according to similar transaction behavior?

These questions provide a practical way to demonstrate the three fundamental machine learning approaches used in this project: supervised classification, supervised regression, and unsupervised clustering.

### Objectives

- Understand the structure and quality of sales transaction data.
- Perform exploratory data analysis and identify important patterns.
- Prepare numerical and categorical variables for machine learning.
- Compare six classification algorithms for Customer Type prediction.
- Compare three regression algorithms for Credited Amount prediction.
- Segment customers using K-Means clustering.
- Evaluate and interpret model performance.
- Identify limitations and propose future improvements.

---

# 2. Dataset Description

The notebook reports **5,000 records and 18 columns**, covering transactions from **1 January 2025 to 31 December 2025**. All 18 columns were complete in the executed notebook: there were no missing values and no duplicate rows.

### Main Dataset Variables

| Variable | Description |
|---|---|
| Date | Transaction date |
| Transaction ID | Unique transaction identifier |
| Invoice No | Invoice identifier |
| Customer Name | Customer identifier/name |
| Customer Type | Retailer, Wholesale, Dealer, Corporate, or Online |
| Executive | Sales executive |
| Sales Zone | Geographic sales area |
| Sales Channel | Factory, Depot, or Warehouse |
| Invoice Value | Invoice value |
| Discount | Discount applied |
| Sales Amount | Sales amount after discount |
| Sales VAT | VAT amount |
| Sales Return | Returned sales value |
| Credited Amount | Credited/payment amount |
| Payment Method | Bank, Cash, Bkash, or Nagad |
| Bank Name | Bank/payment provider |
| Remarks | Transaction notes |
| Month Name | Month of transaction |

The customer-type distribution is: Retailer 1,386; Wholesale 1,355; Dealer 1,132; Corporate 634; and Online 493 transactions.

### Data Originality and Privacy

The university project guideline requires a student-created/generated dataset rather than a dataset downloaded from a public repository. The final submission should document the actual source/collection method honestly. Sensitive customer or business information should be anonymized or excluded before public sharing.

---

# 3. Data Preprocessing and Exploratory Analysis

The dataset was first inspected using Pandas. Data types, missing values, duplicates, descriptive statistics, and customer-type frequencies were checked. The executed notebook found zero missing values and zero duplicate rows.

The date variable was converted into a date type and transformed into useful features:

- Year
- Month Number
- Quarter
- Day of Week

Identifier columns such as Transaction ID, Invoice No, and Customer Name were excluded from baseline predictive models because they do not provide meaningful behavioral information. The Remarks field was also excluded from the baseline models because it is free text.

### Preprocessing Pipeline

Numerical features were processed using median imputation and standardization. Categorical variables were processed using most-frequent imputation and one-hot encoding. The transformations were implemented inside Scikit-learn pipelines so that preprocessing was learned from the training data rather than directly from the test data.

### Exploratory Data Analysis

EDA included:

- Distribution plots for numerical sales variables.
- Box plots for identifying potential outliers.
- Correlation analysis among numerical variables.
- Customer-type distribution.
- Customer-type sales summaries.
- Customer-level aggregation for clustering.

The financial variables show substantial variation. For example, Invoice Value ranges from 5,300 to 499,500, while Credited Amount ranges from 0 to 496,012.38. These ranges support the need for scaling and careful interpretation of outliers.

---

# 4. Supervised Machine Learning

## 4.1 Classification — Customer Type

The classification target was **Customer Type**. The data was split into 4,000 training records and 1,000 testing records using an 80/20 stratified split.

The following models were evaluated:

- K-Nearest Neighbors (KNN)
- Decision Tree
- Random Forest
- Naive Bayes
- Support Vector Machine (SVM)
- Neural Network

### Classification Results

| Model | Accuracy | Precision | Recall | Weighted F1 |
|---|---:|---:|---:|---:|
| Decision Tree | 0.506 | 0.5193 | 0.506 | **0.4793** |
| Random Forest | 0.505 | **0.5292** | 0.505 | 0.4741 |
| SVM | **0.515** | 0.4991 | **0.515** | 0.4690 |
| KNN | 0.408 | 0.4099 | 0.408 | 0.4057 |
| Naive Bayes | 0.387 | 0.4179 | 0.387 | 0.3924 |
| Neural Network | 0.384 | 0.3875 | 0.384 | 0.3854 |

The Decision Tree produced the highest weighted F1 score (0.4793), so it was the strongest classifier according to the comparison criterion used in the notebook. SVM achieved the highest accuracy at 0.515, but its weighted F1 was lower than the Decision Tree. The classification results also show weaker performance for the Online class, indicating that the transaction features do not clearly separate all customer categories.

Five-fold cross-validation of the selected classification pipeline produced a mean weighted F1 of **0.4736**, providing an additional check of model stability.

---

# 5. Regression, Customer Segmentation and Conclusion

## 5.1 Regression — Credited Amount

The regression target was **Credited Amount**. To reduce direct target leakage, Sales Amount and Sales VAT were excluded from the regression predictors. Identifier and free-text fields were also excluded.

| Model | MAE | RMSE | R² |
|---|---:|---:|---:|
| **Linear Regression** | **34,376.03** | **49,940.92** | **0.6991** |
| Random Forest Regressor | 36,428.53 | 54,326.67 | 0.6439 |
| Decision Tree Regressor | 38,323.53 | 60,273.03 | 0.5617 |

Linear Regression performed best across all three reported regression metrics. Its R² of 0.6991 indicates that approximately 69.9% of the variation in the test-set Credited Amount was explained by the model features used in the notebook. The RMSE was approximately 49,940.92, showing that prediction errors remain substantial in monetary terms.

## 5.2 Unsupervised Learning — Customer Segmentation

For clustering, transaction records were aggregated at customer level using:

- Total Invoice Value
- Average Invoice Value
- Total Discount
- Total Sales Return
- Total Credited Amount
- Transaction Count
- Average Credited Amount

The features were standardized before K-Means clustering. Values of K from 2 to 8 were tested using inertia and silhouette score. The highest silhouette score occurred at **K = 2**, with a final silhouette score of **0.3229**.

The two-cluster result suggests that the customers can be separated into two broad groups based on their transaction-level behavior. The segmentation should be interpreted as exploratory rather than as definitive business labels.

## 5.3 Key Findings

1. Customer Type prediction is challenging using the available transaction characteristics alone.
2. Decision Tree provided the strongest classification result by weighted F1.
3. Linear Regression was the best model for Credited Amount prediction.
4. Customer-level aggregation created a useful basis for unsupervised segmentation.
5. K-Means selected two clusters under the tested silhouette criterion.
6. The project demonstrates that the same sales dataset can support multiple ML tasks.

## 5.4 Limitations

The main limitation is that the project uses one year of transaction data and the available variables do not represent every factor affecting sales and payment behavior. Customer Type classes are unequal, and the Online category showed relatively weak classification performance. Remarks were excluded from the baseline model even though they may contain useful business context. The models are academic prototypes and require additional validation before operational use.

Because the data is business-related, privacy and confidentiality must also be maintained. Public versions of the project should use anonymized data and should not expose sensitive customer or company information.

## 5.5 Future Work

Future work could include:

1. Adding more historical transaction records.
2. Adding product, quantity, customer-history, payment-delay, and return-history features.
3. Applying GridSearchCV or RandomizedSearchCV.
4. Using time-aware validation for future sales forecasting.
5. Applying NLP to the Remarks field after privacy review.
6. Building a Streamlit or Power BI sales analytics dashboard.
7. Developing customer-level predictive features from historical purchase behavior.
8. Testing additional clustering methods and validating cluster business meaning.

## 5.6 Conclusion

This project successfully demonstrates a complete fundamental machine learning workflow using Welburg sales transaction data. The analysis begins with data quality checks and exploratory analysis, followed by feature engineering and pipeline-based preprocessing. Supervised learning was applied to both classification and regression tasks, while K-Means was used for unsupervised customer segmentation.

The results show that no single algorithm is universally best. Decision Tree produced the highest weighted F1 for Customer Type classification, while Linear Regression gave the strongest Credited Amount regression performance. K-Means identified two broad customer segments with a silhouette score of 0.3229. These findings demonstrate how practical sales data can be converted into measurable machine learning tasks and provide a foundation for future sales analytics and decision-support systems.

## References

1. National University, Bangladesh. *Fundamentals of Machine Learning — Project Guidelines and Rubric*, 2025.
2. Scikit-learn documentation and API references used for model implementation.
3. Pandas documentation used for data loading and transformation.
4. Matplotlib and Seaborn documentation used for visualization.

---
**Prepared by: Mujakkir Ahmad**  
**National University, Bangladesh**
