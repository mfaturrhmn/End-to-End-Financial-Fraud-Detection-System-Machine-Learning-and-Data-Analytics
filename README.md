# 🚀 End-to-End Financial Fraud Detection System
*Machine Learning & Data Analytics Project for Transaction Security*

## 📌 Project Overview
Financial crime, such as transaction fraud, is one of the largest threats in digital banking. This project is designed to build an automated fraud detection system using Machine Learning capable of accurately identifying suspicious transaction patterns.

This project covers the entire Data Science Lifecycle:
1. Automated large-scale dataset downloading.
2. In-depth Exploratory Data Analysis (EDA).
3. Feature Engineering.
4. Machine Learning modeling (Logistic Regression with imbalanced data handling).
5. Model performance evaluation and deployment into an interactive web application.

---

## 📊 1. Data Exploration & Analysis (EDA)
* **Dataset Source:** Public financial transaction dataset from Kaggle (`amanalisiddiqui/fraud-detection-dataset`).
* **Data Scale:** Consists of **6,362,620 rows** of transactions and **11 feature columns**.
* **Key Insights:**
  * **Class Imbalance:** Extreme class imbalance is observed. Normal transactions (`0`) account for ~6.35 million, while fraudulent transactions (`1`) total only 8,213 rows. The overall fraud rate is extremely low at **0.13%**.
  * **Transaction Types:** Based on analysis, the most frequent transaction types are `CASH_OUT` and `PAYMENT`. However, the highest fraud risk is strictly concentrated in **`TRANSFER` (~0.77%)** and **`CASH_OUT` (~0.18%)**.

---

## ⚙️ 2. Feature Engineering & Preprocessing
* **Derived Features:** Created balance difference features before and after transactions for both senders (`balanceDiffOrig`) and receivers (`balanceDiffDest`) to detect balance-draining anomalies.
* **Data Transformation:** Applied logarithmic transformation (`np.log1p`) to mitigate extreme skewness in transaction amounts, alongside feature scaling using `StandardScaler` and `OneHotEncoder`.
* **Pipeline Integration:** Combined all preprocessing steps into a Scikit-Learn Pipeline to ensure consistent data processing.

---

## 🤖 3. Machine Learning Modeling
* **Algorithm:** Logistic Regression with the `class_weight='balanced'` parameter to assign specialized weights to the minority class (fraud).
* **Train-Test Split:** Split the data with a **70:30** ratio utilizing the `stratify=y` parameter to maintain proportional representation of the fraud class.
* **Model Evaluation Metrics:**
  * **Overall Accuracy:** Reached **94.77%** on the test set.
  * **Recall (Fraud Class):** Reached **94%**, ensuring that the system successfully captures the vast majority of fraudulent cases and minimizes escaped perpetrators.
* **Model Persistence:** The trained model pipeline was exported using the `joblib` library and saved as `fraud_detection_pipeline.pkl`.

---

## 💻 4. Application Deployment & Preview
The machine learning model has been integrated into an interactive web application interface (Fraud Detection App) where users can dynamically test transaction parameters:
* **Normal Transaction:** Returns the status *“No Fraud Detected”* (Prediction 0).
* **Suspicious/Fraud Transaction:** Returns a warning alert *“Fraud Detected!”* (Prediction 1).

---

## 🛠️ Tech Stack & Tools
* **Programming Language:** Python
* **Data Analysis:** Pandas, NumPy
* **Data Visualization:** Matplotlib, Seaborn
* **Machine Learning:** Scikit-Learn
* **Model Saving:** Joblib
* **Environment:** Google Colab

---

## 📂 Repository Structure
```text
├── Fraud_Detection_Project.ipynb     # Jupyter Notebook / Google Colab script
├── fraud_detection_pipeline.pkl      # Trained machine learning model pipeline
└── README.md                         # Project documentation
