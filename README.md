# Comparing-ML-Classifiers
Compare the results of k-nearest neighbors, logistic regression, decision trees, and support vector machines to a business problem.

# 📘 **README.md — Bank Marketing Classification Project**  
### *UC Berkeley — Machine Learning & AI Professional Certificate*  
### *Module 17: Practical Application — Comparing Classifiers*

---

## 📌 **Practical Application Overview**

This module applies multiple machine learning classification models to the **Bank Marketing Dataset**, with the goal of predicting whether a customer will subscribe to a term deposit. The work follows the full modeling workflow:

1. Data preparation and preprocessing  
2. Train/test split  
3. Baseline model creation  
4. Logistic Regression modeling  
5. Additional models (KNN, Decision Tree, SVM)  
6. Model comparison  
7. Model improvement strategies  
8. Final conclusions and recommendations  

This repository contains:

- A Jupyter Notebook with all analysis steps  
- Visualizations (confusion matrices, ROC curves, PR curves)  
- A comparison table of all models  
- This README summarizing the full project  

---

## 📂 **Repository Structure**

```
├── README.md
├── notebook.ipynb
├── CRISP-DM-BANK.pdf
├── Ask.md
├── plots/
│   ├── Logistic_Regression_confusion_matrix.png
│   ├── Logistic_Regression_roc_curve.png
│   ├── Logistic_Regression_precision_recall_curve.png
│   ├── KNN_confusion_matrix.png
│   ├── KNN_roc_curve.png
│   ├── KNN_precision_recall_curve.png
│   ├── Decision_Tree_confusion_matrix.png
│   ├── Decision_Tree_roc_curve.png
│   ├── Decision_Tree_precision_recall_curve.png
│   ├── SVM_confusion_matrix.png
│   ├── SVM_roc_curve.png
│   ├── SVM_precision_recall_curve.png
└── data/
    └── bank-additional-full.csv
    ├── bank-additional.csv
    ├── bank-additional-names.txt
```

---

# 🧠 **Problem Summaries & Methods**

---

## **Problem 6 — Train/Test Split**

A stratified 70/30 split was used to preserve the class imbalance in the target variable (`y`).  
This ensures that both training and test sets reflect the true distribution of “yes” vs “no”.

---

## **Problem 7 — Baseline Model**

The baseline classifier predicts the **majority class (“no”)** for all observations.

- Baseline accuracy ≈ **88–90%**

Any model must exceed this to be considered useful.

---

## **Problem 8 — Logistic Regression Model**

A Logistic Regression model was trained using a preprocessing pipeline:

- Numerical features → StandardScaler  
- Categorical features → OneHotEncoder  

**Performance:**

- Accuracy: **0.9013**  
- F1 Score: **0.33**  
- AUC: **0.803**

**Interpretation:**  
High accuracy but low F1 indicates difficulty identifying the minority class.  
AUC shows good ranking ability.

---

## **Problem 9 — Model Scoring**

The primary metric requested was **accuracy**:

> **Logistic Regression Accuracy = 0.9013**

This exceeds the baseline and demonstrates meaningful predictive value.

---

## **Problem 10 — Model Comparisons**

Four models were trained using default hyperparameters:

| Model | Train Time (sec) | Train Accuracy | Test Accuracy |
|-------|------------------|----------------|----------------|
| Logistic Regression | 0.3563 | 0.8997 | **0.9013** |
| KNN | 0.0749 | 0.9109 | 0.8955 |
| Decision Tree | 0.3495 | **0.9962** | **0.8410** |
| SVM | **475.7894** | 0.9047 | **0.9026** |

### **Interpretation**

- **Logistic Regression**: Strong accuracy, fast training, stable generalization.  
- **KNN**: Competitive but slightly lower test accuracy.  
- **Decision Tree**: Severe overfitting (train ≈ 1.0, test ≈ 0.84).  
- **SVM**: Highest test accuracy but extremely slow training time.  

**Best balance of performance and efficiency:**  
➡️ **Logistic Regression**

---

## **Problem 11 — Improving the Model**

Several strategies can improve performance:

### **1. Hyperparameter Tuning**
- **KNN**: tune `n_neighbors`, `weights`, `metric`  
- **Decision Tree**: tune `max_depth`, `min_samples_split`, `min_samples_leaf`  
- **Logistic Regression**: tune `C`, `penalty`, `solver`  
- **SVM**: tune `C`, `gamma`, `kernel`  

### **2. Adjusting the Evaluation Metric**
Because the dataset is imbalanced:

- Accuracy is misleading  
- F1, Recall, and AUC provide deeper insight  
- Business context favors **recall** (finding likely subscribers)

### **3. Model Selection**
Given the baseline results:

- Logistic Regression and SVM are the strongest candidates  
- SVM requires tuning to reduce training time  
- Decision Tree needs regularization  
- KNN may improve with optimized `k`

---

# 📊 **Visualizations**

For each model, the following were generated and saved:

- Confusion Matrix  
- ROC Curve + AUC  
- Precision–Recall Curve  

These visualizations help diagnose:

- Overfitting  
- Class imbalance effects  
- Ranking ability  
- Precision/recall tradeoffs  

All plots are stored in the `plots/` directory.

---

# 🏁 **Final Conclusions**

1. **Logistic Regression** provides the best balance of accuracy, speed, and generalization.  
2. **SVM** slightly outperforms Logistic Regression in accuracy but is computationally expensive.  
3. **KNN** performs reasonably well but is sensitive to the choice of `k`.  
4. **Decision Tree** overfits heavily and requires regularization.  
5. **Accuracy alone is insufficient** due to class imbalance; AUC and F1 provide more meaningful insights.  
6. **Future improvements** should focus on:
   - Hyperparameter tuning  
   - Class balancing (SMOTE, class weights)  
   - Feature engineering  
   - Threshold optimization  

---