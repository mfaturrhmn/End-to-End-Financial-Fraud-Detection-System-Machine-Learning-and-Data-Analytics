# End-to-End-Financial-Fraud-Detection-System-Machine-Learning-and-Data-Analytics
End-to-end Machine Learning &amp; Data Analytics project for financial transaction security. Built with Python, Scikit-Learn (Logistic Regression), and deployed as an interactive web app to detect fraudulent activities accurately.
# 🚀 End-to-End Financial Fraud Detection System
*Machine Learning & Data Analytics Project for Transaction Security*

## 📌 Project Overview
Kejahatan finansial seperti penipuan transaksi (*fraud*) merupakan salah satu ancaman terbesar dalam dunia perbankan digital. Proyek ini dirancang untuk membangun sistem deteksi penipuan otomatis berbasis *Machine Learning* yang mampu mengenali pola transaksi mencurigakan secara akurat. 

Proyek ini mencakup seluruh siklus hidup data (*Data Science Lifecycle*):
1. Pengunduhan dataset skala besar secara otomatis.
2. Eksplorasi Data Mendalam (*Exploratory Data Analysis - EDA*).
3. Rekayasa Fitur (*Feature Engineering*).
4. Pemodelan Machine Learning (*Logistic Regression* dengan penanganan *imbalanced data*).
5. Evaluasi Performa Model & *Deployment* ke Aplikasi Web Interaktif.

---

## 📊 1. Data Exploration & Analysis (EDA)
* **Dataset Source:** Dataset transaksi finansial publik dari Kaggle (`amanalisiddiqui/fraud-detection-dataset`)[cite: 1].
* **Ukuran Data:** Terdiri dari **6.362.620 baris** transaksi dan **11 kolom** fitur[cite: 1, 3].
* **Temuan Utama (Key Insights):**
  * **Class Imbalance:** Terdapat ketidakseimbangan kelas yang ekstrem. Transaksi normal (`0`) berjumlah ~6,35 juta, sedangkan transaksi penipuan (`1`) hanya berjumlah 8.213 baris[cite: 3]. Tingkat rasio penipuan keseluruhan (*fraud rate*) sangat kecil, yaitu **0.13%**[cite: 3].
  * **Transaction Types:** Berdasarkan analisis, jenis transaksi yang paling sering muncul adalah `CASH_OUT` dan `PAYMENT`[cite: 1, 3]. Namun, risiko penipuan tertinggi mutlak terkonsentrasi pada tipe **`TRANSFER` (~0.77%)** dan **`CASH_OUT` (~0.18%)**[cite: 1, 5].

---

## ⚙️ 2. Feature Engineering & Preprocessing
* **Derived Features:** Menambahkan fitur selisih perubahan saldo sebelum dan sesudah transaksi untuk akun pengirim (`balanceDiffOrig`) dan akun penerima (`balanceDiffDest`) guna mendeteksi anomali pengurasan saldo[cite: 6, 7].
* **Data Transformation:** Menerapkan transformasi logaritmik (`np.log1p`) untuk meredam kemiringan ekstrem (*skewness*) pada nominal transaksi, serta normalisasi fitur menggunakan `StandardScaler` dan `OneHotEncoder`[cite: 6, 11, 12].
* **Pipeline Integration:** Menggabungkan seluruh tahapan prapemrosesan ke dalam *Scikit-Learn Pipeline* agar pemrosesan data menjadi konsisten[cite: 12].

---

## 🤖 3. Machine Learning Modeling
* **Algorithm:** *Logistic Regression* dengan parameter `class_weight='balanced'` untuk memberikan bobot khusus pada kelas minoritas (fraud)[cite: 12].
* **Train-Test Split:** Membagi data dengan rasio **70:30** serta menerapkan parameter `stratify=y` agar proporsi kelas fraud tetap terjaga[cite: 11].
* **Model Evaluation Metrics:**
  * **Akurasi Keseluruhan:** Mencapai **94.77%** pada data uji[cite: 12].
  * **Recall (Fraud Class):** Mencapai **94%**, memastikan bahwa sistem mampu mendeteksi sebagian besar kasus penipuan dan meminimalisir lolosnya pelaku kejahatan[cite: 12].
* **Model Persistence:** Model yang telah dilatih diekspor menggunakan pustaka `joblib` dengan nama file `fraud_detection_pipeline.pkl`[cite: 12].

---

## 💻 4. Application Deployment & Preview
Model machine learning telah diintegrasikan ke dalam antarmuka aplikasi web interaktif (*Fraud Detection App*) di mana pengguna dapat menguji parameter transaksi secara langsung:
* **Normal Transaction:** Mengembalikan status *“No Fraud Detected”* (Prediksi 0)[cite: 15].
* **Suspicious/Fraud Transaction:** Mengembalikan peringatan *“Fraud Detected!”* (Prediksi 1)[cite: 14].

---

## 🛠️ Tech Stack & Tools
* **Programming Language:** Python[cite: 1]
* **Data Analysis:** Pandas, NumPy[cite: 1]
* **Data Visualization:** Matplotlib, Seaborn[cite: 1]
* **Machine Learning:** Scikit-Learn[cite: 1, 11, 12]
* **Model Saving:** Joblib[cite: 12]
* **Environment:** Google Colab[cite: 1]

---

## 📂 Repository Structure
```text
├── Fraud_Detection_Project.ipynb     # Jupyter Notebook / Google Colab script
├── fraud_detection_pipeline.pkl      # Trained machine learning model pipeline
└── README.md                         # Project documentation
