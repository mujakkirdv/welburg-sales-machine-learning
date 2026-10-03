# 📊 Welburg Sales Machine Learning Project

### Customer Type Classification • Credited Amount Regression • Customer Segmentation

> **A practical Machine Learning project based on sales transaction data from Welburg Metal**

---

## 👨‍🎓 Student Information

| Information                 | Details                                                     |
| --------------------------- | ----------------------------------------------------------- |
| **Student Name**            | Mujakkir Ahmad                                              |
| **Program**                 | Post Graduate Diploma in Data Analysis and Machine Learning |
| **Institution**             | National University, Bangladesh                             |
| **Course**                  | Fundamentals of Machine Learning                            |
| **Python Version**          | Python 3.12.0                                               |
| **Development Environment** | Jupyter Notebook                                            |
| **Dataset**                 | `welburg_sales_dataset_2025.xlsx`                           |

---

## 📌 Project Overview

This project applies **Machine Learning techniques to Welburg sales transaction data** to understand customer behavior, analyze sales patterns, predict business-related outcomes, and identify customer segments.

The project covers both **Supervised** and **Unsupervised Machine Learning**.

### 🎯 Main Objectives

* Analyze sales transaction data.
* Understand customer and sales patterns.
* Predict **Customer Type**.
* Predict **Credited Amount**.
* Segment customers using clustering.
* Compare different Machine Learning algorithms.
* Evaluate model performance.
* Generate useful business insights.

---

# 🧠 Machine Learning Models

## 1. Supervised Learning — Classification

**Target Variable:** `Customer Type`

| Model                        | Purpose                      |
| ---------------------------- | ---------------------------- |
| K-Nearest Neighbors (KNN)    | Customer type classification |
| Decision Tree Classifier     | Customer type classification |
| Random Forest Classifier     | Customer type classification |
| Naive Bayes                  | Customer type classification |
| Support Vector Machine (SVM) | Customer type classification |
| Neural Network               | Customer type classification |

### Evaluation Metrics

* Accuracy
* Precision
* Recall
* F1-Score
* Confusion Matrix

---

## 2. Supervised Learning — Regression

**Target Variable:** `Credited Amount`

| Model                   | Purpose                    |
| ----------------------- | -------------------------- |
| Linear Regression       | Credited amount prediction |
| Decision Tree Regressor | Credited amount prediction |
| Random Forest Regressor | Credited amount prediction |

### Evaluation Metrics

* MAE
* MSE
* RMSE
* R² Score

---

## 3. Unsupervised Learning — Clustering

### K-Means Clustering

K-Means is used to identify groups of customers with similar sales characteristics.

### Techniques Used

* Feature scaling
* Elbow Method
* Silhouette Score
* K-Means Clustering
* PCA visualization

---

# 📂 Project Structure

```text
welburg-sales-machine-learning/
├── 📁 data/
│   └── 📊 welburg_sales_dataset_2025.xlsx
│
├── 📓 Welburg_Sales_ML_Project.ipynb
│
├── 📄 README.md
│
├── 📄 requirements.txt
│
├── 📄 Project_Report.docx
│
└── 📁 docs/
    └── Project Description and Rubrics.pdf
```

---

# 📋 Dataset Information

The dataset contains sales transaction information related to customers, sales executives, transactions, and financial values.

## Dataset Columns

| Column            | Description                                          | Type        |
| ----------------- | ---------------------------------------------------- | ----------- |
| `Invoice No`      | Unique invoice/transaction number                    | Categorical |
| `Invoice Date`    | Date of the transaction                              | Date        |
| `Customer Name`   | Customer name/identifier                             | Categorical |
| `Customer Type`   | Type/category of customer                            | Categorical |
| `Sales Executive` | Sales representative responsible for the transaction | Categorical |
| `Sales Zone`      | Sales territory/zone                                 | Categorical |
| `Product`         | Product involved in the transaction                  | Categorical |
| `Invoice Value`   | Total invoice value                                  | Numerical   |
| `Discount`        | Discount applied to the transaction                  | Numerical   |
| `Sales Amount`    | Sales amount after applicable adjustments            | Numerical   |
| `Sales VAT`       | VAT associated with the sale                         | Numerical   |
| `Sales Return`    | Returned sales amount                                | Numerical   |
| `Credited Amount` | Credited/received amount                             | Numerical   |
| `Payment Method`  | Method used for payment                              | Categorical |
| `Remarks`         | Additional transaction information                   | Text        |

> **Note:** The exact column names should remain consistent with the final Excel dataset used in the notebook.

---

# 🔍 Exploratory Data Analysis

The project includes several EDA techniques.

### 📈 Distribution Analysis

Histograms and KDE plots are used to understand the distribution of numerical sales variables.

### 📦 Outlier Detection

Box plots are used to identify potential outliers in:

* Invoice Value
* Discount
* Sales Amount
* Sales VAT
* Sales Return
* Credited Amount

### 🔗 Correlation Analysis

A correlation heatmap is used to examine relationships between numerical sales variables.

### 📊 Categorical Analysis

Categorical variables such as:

* Customer Type
* Sales Executive
* Sales Zone
* Payment Method
* Product

are analyzed to understand their distributions and patterns.

---

# ⚙️ Machine Learning Workflow

```text
                 ┌─────────────────────┐
                 │   Sales Dataset     │
                 └──────────┬──────────┘
                            │
                            ▼
                 ┌─────────────────────┐
                 │   Data Cleaning     │
                 └──────────┬──────────┘
                            │
                            ▼
                 ┌─────────────────────┐
                 │        EDA          │
                 │ Distribution/Boxplot│
                 │ Correlation/etc.    │
                 └──────────┬──────────┘
                            │
                            ▼
                 ┌─────────────────────┐
                 │ Feature Engineering │
                 └──────────┬──────────┘
                            │
             ┌──────────────┴──────────────┐
             │                             │
             ▼                             ▼
    ┌──────────────────┐          ┌──────────────────┐
    │ Supervised ML    │          │ Unsupervised ML  │
    └────────┬─────────┘          └────────┬─────────┘
             │                             │
      ┌──────┴──────┐                      │
      │             │                      ▼
      ▼             ▼                K-Means
 Classification  Regression          Clustering
      │             │
      ▼             ▼
 Customer Type   Credited Amount
 Prediction      Prediction
      │             │
      └──────┬──────┘
             │
             ▼
      Model Evaluation
             │
             ▼
      Model Comparison
             │
             ▼
       Final Insights
```

---

# 🛠️ Technologies & Libraries

### Programming Language

```text
Python 3.12.0
```

### Main Libraries

```text
Pandas
NumPy
Matplotlib
Seaborn
Scikit-learn
OpenPyXL
Joblib
Jupyter
```

---

# 💻 Installation

Clone the repository:

```bash
git clone https://github.com/mujakkirdv/welburg-sales-machine-learning.git
```

Move into the project directory:

```bash
cd welburg-sales-machine-learning
```

Create a virtual environment:

```bash
python -m venv venv
```

Activate the environment on Windows:

```bash
venv\Scripts\activate
```

Install dependencies:

```bash
pip install -r requirements.txt
```

Start Jupyter Notebook:

```bash
jupyter notebook
```

Then open:

```text
Welburg_Sales_ML_Project.ipynb
```

---

# 📦 Requirements

Create a `requirements.txt` file containing:

```text
pandas
numpy
openpyxl
matplotlib
seaborn
scikit-learn
jupyter
joblib
```

---

# 🔐 Data Privacy

The dataset is used for academic Machine Learning analysis.

Because the project is based on practical sales/account-related work experience, confidential business and customer information should not be publicly disclosed.

Before publishing the dataset to GitHub:

* Remove personal customer information.
* Remove phone numbers and email addresses.
* Remove confidential financial information where required.
* Anonymize customer identifiers.
* Follow company data-sharing policies.

> **Important:** If the original dataset contains confidential company information, do not upload the original Excel file to a public GitHub repository. Use an anonymized academic version instead.

---

# 📊 Project Results

The project compares multiple Machine Learning models to determine suitable approaches for:

### Classification

```text
Customer Type
      ↓
KNN
Decision Tree
Random Forest
Naive Bayes
SVM
Neural Network
      ↓
Performance Comparison
```

### Regression

```text
Credited Amount
      ↓
Linear Regression
Decision Tree Regressor
Random Forest Regressor
      ↓
Performance Comparison
```

### Clustering

```text
Customer Sales Features
          ↓
      K-Means
          ↓
 Customer Segments
```

---

# 🚀 Future Improvements

Future versions of this project may include:

1. Larger historical sales datasets.
2. More detailed product-level information.
3. Customer purchase history.
4. Payment delay analysis.
5. Sales forecasting.
6. Advanced hyperparameter tuning.
7. Time-aware model validation.
8. NLP analysis of transaction remarks.
9. Interactive Power BI or Streamlit dashboard.
10. Deployment of the final Machine Learning model.

---

# 📌 Academic Disclaimer

This project was developed for educational purposes as part of the **Fundamentals of Machine Learning** course at National University, Bangladesh.

The Machine Learning models are intended for academic analysis and should not be considered a replacement for professional business decision-making without further validation.

---

# 👨‍💻 Author

**Mujakkir Ahmad**

Post Graduate Diploma in Data Analysis and Machine Learning
**National University, Bangladesh**

### Skills Demonstrated

```text
Python
Pandas
NumPy
Data Cleaning
Data Visualization
Exploratory Data Analysis
Machine Learning
Classification
Regression
Clustering
Scikit-learn
Jupyter Notebook
Git & GitHub
```

---

# ⭐ Git & GitHub Commands

### Initialize Git

```bash
git init
```

### Check project files

```bash
git status
```

### Add files

```bash
git add .
```

### Create first commit

```bash
git commit -m "Initial commit - Welburg Sales ML Project"
```

### Connect GitHub repository

```bash
git remote add origin https://github.com/mujakkirdv/welburg-sales-machine-learning.git
```

### Rename branch to main

```bash
git branch -M main
```

### Push project

```bash
git push -u origin main
```

---

# 🔄 Future Git Updates

After making changes:

```bash
git add .
git commit -m "Update machine learning analysis"
git push
```

---

## ⭐ Project Summary

> **Welburg Sales Machine Learning Project** demonstrates the practical application of Machine Learning to sales transaction data using classification, regression, and clustering techniques. The project combines practical business experience with data analysis and Machine Learning to identify patterns, make predictions, and explore customer segmentation.

---

### Thank You

**Prepared by:**

### Mujakkir Ahmad

**Post Graduate Diploma in Data Analysis and Machine Learning**
**National University, Bangladesh**

