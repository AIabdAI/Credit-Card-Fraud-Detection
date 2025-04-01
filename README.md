# 🧠 Credit Card Fraud Detection Project

**Author:** Abdallah A. M. Iqelan  
**Dataset:** [Credit Card Fraud Detection - Kaggle 2013](https://www.kaggle.com/mlg-ulb/creditcardfraud)  
**Objective:** Build a highly generalizable model for detecting fraudulent transactions, while analyzing model behavior through learning curves and data balancing techniques.

---

## 📌 1. Introduction

Credit card fraud is a serious issue in modern digital banking systems. This project utilizes the **CreditCard 2013 dataset**, which includes **284,807 transactions**, of which only **492 are fraud cases** (Class 1), representing an extreme imbalance (~0.17%).

Due to this imbalance, traditional metrics like accuracy are misleading. The goal of this project is to **improve generalization**, reduce overfitting, and ensure reliable performance on unseen data using **K-Fold Cross-Validation**, data preprocessing, and training behavior analysis.

---

## 🌲 2. Why Random Forest?

I selected **Random Forest Classifier** for this project because it is one of the **most effective algorithms for structured/tabular data**, like the credit card dataset used here.

### 🔹 Key reasons for choosing Random Forest:
- Robust to **imbalanced data** when combined with class weighting or resampling.
- Captures **non-linear relationships** and feature interactions.
- Handles **missing or noisy data** gracefully.
- Used by **top Kaggle competition winners** and data science professionals for structured datasets.

📌 In contrast, deep learning models like neural networks are more effective on **unstructured data** such as:
- Images (e.g., CNNs)
- Audio (e.g., RNNs)
- Text (e.g., Transformers)

For this financial dataset, Random Forest offered:
- High interpretability  
- Strong baseline performance  
- Fast training time  
✅ It was the ideal choice for this use case.

---

## 📊 3. Dataset Overview

- **Total transactions:** 284,807  
- **Fraudulent transactions (Class 1):** 492  
- **Normal transactions (Class 0):** 284,315  
- Features are anonymized (V1 to V28), plus `Time` and `Amount`.

---

## 🔁 4. Initial K-Fold Cross-Validation Check

To ensure that the model’s evaluation is **stable and not dependent on a particular split**, I applied **K-Fold Cross-Validation**. This helped verify that the dataset was fairly distributed and performance consistent across samples.

### 📋 CV Evaluation Metrics:

| Metric     | Average   |
|------------|-----------|
| Accuracy   | 0.9995    |
| F1 Score   | 0.8510    |
| ROC AUC    | 0.8831    |
| Precision  | 0.9574    |
| Recall     | 0.7663    |

✅ These results indicate that the model is stable across folds and that class distribution is preserved.

---

## 📈 5. Learning Curve Monitoring

### 🎯 Purpose:

The **training behavior curve** shows how the model reacts to **incrementally increasing training data**.

- **Training Error** starts low (memorization), may **increase slightly** if the model generalizes.
- **Validation Error** starts high, should **decrease** with improved learning.

> Monitoring this curve helps detect **overfitting, underfitting**, or signs of **healthy generalization**.

---

## 🔍 6. Phase 1: Before Any Data Cleaning

Trained the model on the raw dataset.

### 🔎 Observations:
- Training Error was **flat at zero** → overfitting.
- Validation Error showed **little improvement**.
- Model was **memorizing** due to **repetitive normal transactions**.

### 📉 Test Results:
- Accuracy: 0.9995  
- F1 Score: 0.8506  
- Precision: 0.9867  
- Recall: 0.7475  
- ROC AUC: 0.9533  

![image](https://github.com/user-attachments/assets/8775f7fa-5d9a-457d-acfe-ba8f75769c8a)


---

## ✂️ 7. Phase 2: Removing Duplicated Class 0 Samples

Cleaned repeated class 0 entries, keeping representative samples.

### 🔎 Observations:
- Training Error **began to rise** → model stopped memorizing.
- Validation Error **decreased** → better generalization.
- Model learned to **detect patterns** instead of memorizing outcomes.

### 📉 Test Results:
- Accuracy: 0.9996  
- F1 Score: 0.8619  
- Precision: 0.9398  
- Recall: 0.7959  
- ROC AUC: 0.9473  

![image](https://github.com/user-attachments/assets/59e4f686-9d63-47bc-abee-a1fe893c9f96)

🟢 **This was the best-performing configuration.**

---

## 🔁 8. Phase 3: Random Undersampling of Class 0

Removed 25% of class 0 data randomly.

### 🔎 Observations:
- Training Error became **flat again** → overfitting.
- Validation Error increased → performance drop.
- Model was biased again.

### 📉 Test Results:
- Accuracy: 0.9995  
- F1 Score: 0.8701  
- Precision: 0.9872  
- Recall: 0.7778  
- ROC AUC: 0.9470  

![image](https://github.com/user-attachments/assets/ab33dba3-b203-418a-84af-698c635f2a62)

🔴 **Conclusion:** Randomly removing normal data hurt generalization.

---

## 🧠 9. Key Findings

- The **learning curve** was vital in analyzing model behavior.
- Encouraging training error to **rise slightly** led to better generalization.
- **Best result** achieved by **removing duplicates** only.
- My approach **outperformed many public implementations on GitHub**, where models often overfit and lacked learning behavior analysis.

---

## 🏆 10. Final Conclusion

> 🔹 **The best model** was achieved by removing only duplicated class 0 entries while preserving dataset structure.

✅ This resulted in:
- Better generalization  
- Improved recall  
- Balanced performance

This project demonstrates expertise in:
- Data preparation  
- Model evaluation with K-Fold  
- Analyzing overfitting/generalization  
- Building high-performance fraud detection models under real-world conditions


