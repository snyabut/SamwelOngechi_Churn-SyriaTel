# **SyriaTel Customer Churn Prediction:**

**A Data-Driven Retention Strategy.**

**Author:** [Samwel Ongechi](https://www.linkedin.com/in/samwelnyabuti/)

**Tools Used:** Python, scikit-learn, pandas, seaborn, matplotlib, Jupyter Notebook  

**Dataset Source:** [SyriaTel Churn Dataset on Kaggle](https://www.kaggle.com/becksddf/churn-in-telecoms-dataset)



## **Project Overview**

In the highly competitive telecommunications industry, retaining existing customers is far more cost-effective than acquiring new ones. SyriaTel, a major telecom provider, seeks to reduce customer attrition by leveraging data-driven methods to anticipate churn (customers discontinuing service) and intervene before it happens.


This project is a data-driven initiative to help SyriaTel identify which customers are most likely to churn, understand the underlying behavioral patterns, and implement strategic actions to improve loyalty. I applied machine learning and data analytics to build a predictive model that guides business decision-making.


## **Business Problem**

Churn is costly. On average, it costs **5 to 10 times more** to acquire a new customer than to retain an existing one. Despite this, many telecom providers including SyriaTel lack systems to proactively identify customers at risk of leaving, hence, many  react to churn after it occurs.

SyriaTel’s Objective: Prevent churn by predicting it early and acting on the insights.

**Business Questions:**
1. Can we predict which customers are likely to churn based on their usage and service interaction patterns?
2. What are the main behavioral drivers of churn?
3. How can we use these insights to design better customer retention strategies?



## **Objectives**

- Develop a predictive model that accurately classifies customers as *churned* or *retained*.
- Identify key behavioral and service-related features that influence churn.
- Provide **practical, data-driven business recommendations** to reduce churn and improve customer satisfaction.
- Build a modular, interpretable solution suitable for deployment in SyriaTel’s retention workflow.



## **Dataset Summary**

- **Rows:** 3,333 customer records  
- **Columns:** 20 features  
- **Target Variable:** `churn` (True = churned, False = retained)  
- **Key Features:**  
  - Call duration and frequency (day, evening, night, international)  
  - Plan types (`international_plan`, `voice_mail_plan`)  
  - Customer service interactions (`customer_service_calls`)  

There were **no missing values**, and minimal preprocessing was required beyond encoding and standardization.



## **Methodology**

### 1. Exploratory Data Analysis (EDA)
- Churn rate is **~14.5%**, highlighting a **class imbalance** problem.
- Customers with **4+ customer service calls** were significantly more likely to churn.
- Those on an **international plan** exhibited disproportionately high churn.
- Surprisingly, **high daytime usage** (minutes) also correlated with higher churn.

### 2.  Feature Engineering
- Dropped redundant `*_charge` columns highly correlated with `*_minutes`.
- Created:
  - `total_minutes`: total usage across all time blocks
  - `inactive_vmail`: customers with a voice mail plan but 0 messages
  - `high_service_calls`: binary flag for customers with ≥4 service calls

### 3. Modeling Approach
- Used a preprocessing pipeline with `StandardScaler` and `OneHotEncoder`.
- Trained two models:
  - **Logistic Regression**: baseline, interpretable model
  - **Random Forest**: ensemble model capable of capturing complex relationships

### 4. Model Evaluation
- Evaluation metrics: **Precision**, **Recall**, **F1-score**, and **ROC AUC**
- **Random Forest** achieved:
  - **Precision (Churn):** 0.94
  - **Recall (Churn):** 0.72
  - **ROC AUC Score:** 0.93
- Logistic Regression underperformed, particularly in recall.



## Business Recommendations

Based on model insights, the following strategies are recommended:

### 1. Proactive Support Trigger
- **Flag customers after their 3rd customer service call.**
- Assign a **retention specialist** to intervene and resolve concerns before churn occurs.

### 2. International Plan Review
- Customers on the international plan are churning at elevated rates.
- Conduct a **full review**:
  - Run **customer satisfaction surveys**
  - Perform **competitor pricing analysis**
  - Redesign the plan to improve perceived value

### 3. Tiered & Predictable Pricing
- High-usage customers (especially daytime callers) are also at risk.
- Introduce **"Power User" plans**:
  - Capped billing or flat-rate options to prevent “bill shock”
  - Loyalty rewards for heavy users

These changes could **significantly reduce churn**, preserve revenue, and improve brand loyalty.

---

## **Limitations**

- No access to behavioral or financial data (e.g., **payment history**, **contract duration**, **location**, **income**).
- Predictive power may improve with **richer CRM integration** and **demographic segmentation**.

---

## **Future Work**

- Apply **SMOTE** or resampling techniques to address class imbalance during training.
- Explore **model interpretability tools** such as **SHAP** to explain individual predictions.
- Integrate churn predictions into a **real-time customer dashboard** for operational use.
