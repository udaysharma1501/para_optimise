# 🍷 Optimizing SVM Classifiers on the UCI Wine Dataset

This project showcases the performance tuning of Support Vector Machine (SVM) models using a subset of the **UCI Wine Recognition Dataset**. The objective is to identify the best combination of hyperparameters to maximize classification accuracy—especially when working with a limited amount of training data.

---

## 📁 Dataset Information

- **Name**: Wine Recognition Dataset  
- **Source**: [UCI Machine Learning Repository](https://archive.ics.uci.edu/dataset/109/wine)
- **Number of Features**: 13  
- **Number of Samples**: 178  
- **Target Classes**: 3 (Wine class: 1, 2, 3)

---

## 🧪 Methodology

### 🔹 Data Loading
- The dataset is retrieved using the `ucimlrepo` Python package.
- Features (`X`) and labels (`y`) are extracted for processing.

### 🔹 Train-Test Split
- The process is repeated over 10 different random seeds.
- Each time, the dataset is split into **30% training** and **70% testing**.

### 🔹 Limited Training Regime
- To simulate real-world constraints, only **50 samples** are used from the training set in each run.

### 🔹 Hyperparameter Optimization (Random Search)
- For every 50-sample subset:
  - **100 random combinations** of SVM parameters are tested:
    - **kernel**: `'linear'`, `'poly'`, `'rbf'`, `'sigmoid'`
    - **C**: Random float in `[0.1, 10.0]`
    - **gamma**: Random float in `[0.001, 1.0]`
- Each combination is evaluated on the test set, and accuracy is recorded.
- The best combination per iteration is logged.

---

## 📈 Convergence Plot

This visualization illustrates how the best classification accuracy improves over 100 random trials for the most successful 50-sample subset.

![image](https://github.com/user-attachments/assets/302461ad-ab63-4e18-a263-a79a23ccce0b)

**Interpretation**:
- **X-axis**: Trial number (logged every 10 iterations)
- **Y-axis**: Highest accuracy found so far  
- The curve reflects the effectiveness of random search in discovering better-performing SVM configurations over time.

---

## 📌 Conclusion

- Accurate classification (above 95%) is achievable even with only 50 training samples.
- **`rbf`** and **`poly`** kernels frequently yield superior results.
- Random search proves to be a practical approach for SVM hyperparameter tuning, especially in low-data scenarios.
