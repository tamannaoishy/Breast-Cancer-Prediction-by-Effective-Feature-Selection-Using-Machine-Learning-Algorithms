# 🧠 Breast Cancer Classification Using Feature Selection

This project focuses on building machine learning models to classify breast cancer tumors (benign vs. malignant) using the Wisconsin Breast Cancer Dataset. It investigates three different feature selection strategies and compares classifier performances, **without applying PCA**.

---

## 📂 Dataset

- **Source:** [UCI ML Repository – Breast Cancer Wisconsin (Diagnostic)](https://archive.ics.uci.edu/ml/datasets/Breast+Cancer+Wisconsin+(Diagnostic))
- **Features:** 30 numeric features describing characteristics of cell nuclei.
- **Target:** Diagnosis (`M` = Malignant, `B` = Benign)

---

## 🧰 Project Workflow

1. **Data Preprocessing**
   - Removed the `id` column.
   - Encoded target variable (`M` → 1, `B` → 0).
   - Class distribution: Benign-357, Malignant - 212
   - Verified no missing values.

2. **Outlier Detection & Removal**
   - Used **Isolation Forest** to remove outliers.
   - Dataset reduced from 569 to 540 samples.
   - After outlier removal:
     diagnosis
     0  ->  350,
     1  ->  190

3. **Feature Scaling**
   - Standardized features using `StandardScaler`.

4. **Train-Test Split**
   - 80% training, 20% testing (stratified by target).

5. **Class Imbalance Handling**
   - Used **SMOTE** to balance classes in the training set.
   - Class distribution after SMOTE:
     Counter({0: 280, 1: 280})

6. **Feature Selection Techniques**
   - **ANOVA F-test**: Used `SelectKBest` with `GridSearchCV` to select optimal `k` features.20 features were selected as best features.
   - **RFE with RFECV**: Selected features recursively using cross-validation to determine optimal number.Optimal number of features: 19
   - **ExtraTreesClassifier**: Ranked features by importance and tuned to select best top-`k` features.Best number of features by ExtraTrees top-k tuning: 25

7. **Model Training & Evaluation**
   - Trained three classifiers:
     - **Logistic Regression**
     - **Random Forest**
     - **MLP Classifier**
   - Evaluated using:
     - Accuracy
     - Precision, Recall, F1-Score
     - ROC AUC
     - Confusion Matrix

8. **Result Comparison**
   - Compared the classification results across all feature selection methods and models.

---

## 📁 Files Structure

