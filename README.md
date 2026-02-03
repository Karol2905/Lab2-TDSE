
# Heart Disease Risk Prediction using Logistic Regression

---

## 📌 Repo Overview

### Exercise Summary

Implements logistic regression for heart disease prediction, covering:

* Exploratory Data Analysis (EDA)
* Logistic regression training from scratch
* Decision boundary visualization
* L2 regularization
* Deployment exploration using Amazon SageMaker Studio

This project demonstrates the full machine learning workflow from data analysis to cloud-based inference.

---

## 📊 Dataset Description

* **Dataset**: Kaggle Heart Disease Dataset
* **Source**: [https://www.kaggle.com/datasets/neurocipher/heartdisease](https://www.kaggle.com/datasets/neurocipher/heartdisease)
* **Samples**: 270 patients
* **Target Variable**:

  * `1` → Presence of heart disease
  * `0` → Absence of heart disease
* **Class Distribution**: ~55% presence rate

### Selected Features

* Age (29–77 years)
* Cholesterol (112–564 mg/dL)
* Resting Blood Pressure
* Maximum Heart Rate
* ST Depression
* Number of vessels fluoroscopically colored

All numerical features were normalized using z-score normalization.

---

## ⚙️ Model Overview

* Logistic regression implemented **from scratch**
* No use of `scikit-learn` for training
* Components implemented manually:

  * Sigmoid function
  * Binary cross-entropy cost
  * Gradient Descent optimization
* Train/Test split: **70/30 stratified**

---

## 📈 Results Summary

* Stable convergence of the cost function
* Comparable performance on training and test sets
* Recall emphasized due to medical relevance
* Regularization reduced coefficient magnitude without affecting F1-score

---

## 🔒 Regularization

L2 regularization was evaluated using:

```
λ ∈ {0, 0.001, 0.01, 0.1, 1}
```

The F1-score remained constant across all values of λ, while the norm of the
weight vector decreased as λ increased. This indicates that the unregularized
model already generalizes well, and regularization mainly improves numerical
stability.

---

## ☁️ Deployment Evidence (Amazon SageMaker)

### Deployment Process

The trained logistic regression model was deployed in a managed cloud environment using **Amazon SageMaker Studio**.

**Steps performed:**

1. Exported trained model parameters (`weights.npy`, `bias.npy`, `mu.npy`, `sigma.npy`)
2. Created a SageMaker Studio domain using the **single-user quick setup**
3. Launched JupyterLab inside SageMaker Studio
4. Uploaded model files to the cloud environment
5. Created a cloud-based inference notebook to test predictions

---

### 📸 Deployment Screenshots

The following screenshots document the deployment process:

1. **SageMaker Studio Environment**

   * `images/screen1.png`
   * `images/screen 3.png`
2. **Model Files Uploaded in JupyterLab**

   * `images/screen 4.png`
3. **Inference Output in SageMaker**

   * `images/screen 6.png`

---

### 🔍 Inference Test

**Sample Input:**

```
Age = 60
Cholesterol = 300
BP = 140
Max HR = 120
ST Depression = 2.3
Number of Vessels = 2
```

**Model Output:**

```
Heart disease probability ≈ 0.96 (high risk)
```

This demonstrates real-time inference capability in a cloud-based environment.

> *Note:* The model was executed within SageMaker Studio rather than a persistent REST endpoint, which is sufficient to demonstrate deployment and inference for this assignment.

---

## 🧠 Final Insights

* Logistic regression provides interpretable predictions for heart disease risk.
* Feature normalization and proper evaluation are critical for stable training.
* Regularization does not always improve metrics but enhances robustness.
* Cloud deployment bridges the gap between academic models and real-world systems.

---

## 📁 Repository Structure

```
├── heart_disease_lr_analysis.ipynb
├── sagemaker_inference.ipynb
├── Heart_Disease_Prediction.csv
├── weights.npy
├── bias.npy
├── mu.npy
├── sigma.npy
├── images/
└── README.md
```

---

## 👩‍💻 Author

* **Karol Estupiñan** –

