### Report: Classification of Medical Data

#### **Objective**
The analysis aims to classify medical conditions into five categories: `cirrhosis`, `fibrosis`, `hepatitis`, `no_disease`, and `suspect_disease` using patient-related data. The data includes variables like age, albumin levels, and other clinical markers.

---

### **Data Overview**
- **Dataset Size**: 615 rows and 13 columns.
- **Variables**: Mix of categorical and numerical data, including:
  - Numerical: `age`, `albumin`, `alkaline_phosphatase`, etc.
  - Categorical: `category` (target variable), `sex`.

#### **Data Preprocessing**
- **Missing Data Handling**:
  - Missing values in numerical columns (e.g., `albumin`, `cholesterol`) were replaced with their mean values.
- **Feature Encoding**:
  - One-Hot Encoding applied to categorical variable `sex`.
  - Label Encoding applied to the target variable `category`.
- **Outlier Detection**:
  - Boxplots used to detect potential outliers.
- **Feature Scaling**:
  - Standardized numerical features for model compatibility.

---

### **Exploratory Data Analysis**
- A correlation heatmap was generated to visualize relationships between numerical features.
- Histograms provided insights into the distribution of clinical variables.

---

### **Modeling**
The following models were implemented and evaluated:

#### **1. Logistic Regression**
- **Performance**:
  - Accuracy: **86.18%**
  - Precision: **89.61%**
  - Recall: **86.18%**
  - F1-Score: **85.59%**
- Confusion Matrix:
  - Most errors occurred in predicting minority classes (e.g., `cirrhosis` and `fibrosis`).

#### **2. Decision Tree**
- **Hyperparameter Tuning**:
  - Grid search optimized parameters like `max_depth`, `min_samples_split`, and `max_features`.
- **Performance**:
  - Accuracy: **85.36%**
  - Precision: **82.44%**
  - Recall: **85.36%**
  - F1-Score: **83.01%**

#### **3. LightGBM**
- **Performance**:
  - Accuracy: **86.99%**
  - Precision: **85.68%**
  - Recall: **86.99%**
  - F1-Score: **85.15%**

#### **4. XGBoost**
- **Performance**:
  - Accuracy: **90.24%**
  - Precision: **89.83%**
  - Recall: **90.24%**
  - F1-Score: **89.07%**
- Confusion Matrix:
  - XGBoost achieved the highest accuracy with better handling of minority classes compared to other models.

---

### **Predictions**
- Predictions for new patient data were tested using:
  - Logistic Regression.
  - Decision Tree.
  - XGBoost.
- Example:
  - Patient data predicted as `no_disease` using XGBoost and `fibrosis` using Logistic Regression.

---

### **Conclusion**
- **XGBoost emerged as the best-performing model** with an accuracy of **90.24%** and robust metrics across all classes.
- While Logistic Regression and LightGBM provided competitive results, they struggled with minority class predictions.
- The dataset displayed significant imbalances, affecting the performance of simpler models like Logistic Regression and Decision Tree.

---

### **Recommendations**
1. **Handle Imbalanced Data**:
   - Techniques like SMOTE or class-weight adjustments can further improve minority class predictions.
2. **Further Evaluation**:
   - Perform cross-validation to ensure model robustness.
   - Explore ensemble methods combining XGBoost with other classifiers.
3. **Model Deployment**:
   - Save the XGBoost model for real-world application using libraries like `pickle`.
4. **Feature Engineering**:
   - Include additional patient data or derived features to enhance model performance.
