 # Fraud Detection Project: Detailed Data Report

📌 1. Data Cleaning and Preprocessing
1.1. Datasets Used

    Fraud_Data.csv – e-commerce transaction data.

    IpAddress_to_Country.csv – IP address ranges mapped to country.

    creditcard.csv – anonymized credit card transactions.

1.2. Key Preprocessing Steps
➔ Datetime Conversion

    signup_time and purchase_time were converted from string to datetime format for accurate time-based feature generation.

➔ IP Address Cleaning

    IP addresses in Fraud_Data.csv had floating-point issues (e.g., 732758368.79972). These were:

        Converted to integers using .astype(int).

        Decimal parts were safely ignored as they don't affect the actual IP address range mapping.

➔ Missing Value Handling

    All features had 0 missing values.

    No imputation required.

➔ Duplicates

    Checked using .duplicated() method — no duplicate transactions found.

➔ Data Types Corrected

    Categorical columns (e.g. source, browser, sex) were type-cast for memory optimization.

    Numeric columns (purchase_value, age, ip_address) confirmed as numeric.

📌 2. Key Insights and Visualizations (EDA)
2.1. Class Imbalance Problem

    Fraudulent transactions (class = 1) represent only ~9.36% of total transactions:

        140

You said:
readme md and give which one is goog for imabalce syntichic or random
ChatGPT said:

Here’s a professional README.md template you can use, followed by guidance on Synthetic vs. Random sampling for class imbalance.
📄 README.md
📊 Fraud Detection Project: E-Commerce and Banking
🔍 Objective

Develop accurate fraud detection models for:

    E-commerce transactions (Fraud_Data.csv)

    Bank transactions (creditcard.csv)

Using:

    Geolocation analysis via IP-to-country mapping.

    Time-based and behavioral feature engineering.

    Handling class imbalance effectively.

📂 Data Sources
Dataset	Description
Fraud_Data.csv	E-commerce transactions with fraud labels.
IpAddress_to_Country.csv	IP address ranges mapped to countries.
creditcard.csv	Anonymized bank transactions (PCA features).
⚙️ Workflow
1️⃣ Data Cleaning & Preprocessing

    Converted signup_time and purchase_time to datetime.

    Converted IP addresses to integers.

    Merged IP address ranges to map transactions to country.

    Removed duplicates and validated data types.

2️⃣ Exploratory Data Analysis (EDA)

    Visualized:

        Fraud distribution (highlighting class imbalance).

        Fraud by country, browser, device.

        Fraud patterns over time (hour, day, time since signup).

    Key insight: Fraudsters often transact quickly after signup and cluster in certain geographies.

3️⃣ Feature Engineering

    time_since_signup (minutes): Faster purchases linked to higher fraud risk.

    ip_country: Geographic fraud trends.

    Device/browser/source-based features.

    Time-based features: hour_of_day, day_of_week.

4️⃣ Handling Class Imbalance

    Severe imbalance in both datasets (~90% legitimate vs. 10% fraud).

    Two strategies considered:

        Synthetic Oversampling (Recommended):
        Use SMOTE or ADASYN to generate realistic synthetic fraud samples based on feature space.

        Random Oversampling/Undersampling:
        Faster, but risks overfitting (oversampling) or information loss (undersampling).

🎯 Recommended Imbalance Handling

    ✅ Synthetic Oversampling (SMOTE or ADASYN) is preferred for this problem:

    Generates realistic fraud examples rather than simple duplication.

    Preserves all legitimate transaction data.

    Works well with small minority classes without overfitting.

    ❌ Random Oversampling risks overfitting due to repeated minority samples.

    ❌ Random Undersampling risks losing important patterns from legitimate transactions.

📈 Modeling Approach

    Models: Random Forest, XGBoost, LightGBM, Logistic Regression (baseline).

    Evaluation: Precision-Recall AUC, F1-score (due to imbalance), and ROC-AUC.

    Explainability: SHAP to understand model predictions.

📅 Project Timeline
Milestone	Date
Interim-1 Submission	20 July 2025
Interim-2 Submission	27 July 2025
Final Submission	29 July 2025
🤝 Team

    Yohannes Alemu

    Mentors: Mahlet, Rediet, Kerod, Rehmet

📌 References

    SMOTE paper: https://arxiv.org/abs/1106.1813

    SHAP: https://shap.readthedocs.io/

    Fraud detection best practices: https://towardsdatascience.com/fraud-detection

📢 Notes

    Fraud detection must minimize false negatives without overwhelming the system with false positives.

    Geolocation and time-based features are critical differentiators in our solution.
