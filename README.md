
# 🎓 Student Exam Score Prediction

This project predicts student exam scores based on behavioral and environmental factors such as study habits, sleep patterns, screen time, and more. Several regression models were trained and evaluated to identify the best-performing solution.

---

## 📁 Dataset

* **1,000 student records**
* **Features:**

  * `age`, `study_hours_per_day`, `social_media_hours`, `netflix_hours`
  * `part_time_job`, `attendance_percentage`, `sleep_hours`
  * `exercise_frequency`, `mental_health_rating`
  * `extracurricular_participation`, `diet_quality_encoded`, `internet_quality_encoded`
* **Target variable**: `exam_score`

### 📌 Preprocessing Steps

* Encoded categorical variables (`Yes/No`, quality levels)
* Dropped irrelevant columns (e.g., `gender`, `school_type`)
* Scaled numeric features where needed
* Split dataset into training and testing sets (80/20)

---

##  Modeling Approach

### Models Tested:

* Simple Linear Regression
* **✅ Multiple Linear Regression** *(Best Performer)*
* Random Forest Regressor
* XGBoost Regressor

### Evaluation Metrics:

* **R² Score** (coefficient of determination)
* **RMSE** (Root Mean Squared Error)

---

## 📊 Model Performance

| Model                          | R² Score | RMSE       |
| ------------------------------ | -------- | ---------- |
| Simple Linear Regression       | 0.67     | 9.20       |
| **Multiple Linear Regression** | **0.90** | **5.10** ✅ |
| Random Forest                  | 0.85     | 6.15       |
| XGBoost Regressor              | 0.88     | 5.60       |

> 🔁 *Cross-validated Multiple Linear Regression:*
> R² ≈ **0.896** | RMSE ≈ **5.38**

---

## ✅ Best Model: Multiple Linear Regression

* Easily interpretable coefficients  
* Fast and lightweight for training and prediction  
* No signs of overfitting (validated via residual analysis and cross-validation)

**Model Saved Using:**

```python
import pickle
with open('best_model_mlr.pkl', 'wb') as f:
    pickle.dump(model, f)
````

---

## 🧪 New Analysis: Feature Ablation

### 📁 `exam_score_modeling_no_study_hours.ipynb`

This additional notebook tests the model’s **robustness** by removing the most impactful feature: `study_hours_per_day`.

### 🔍 Why?

To evaluate how much models depend on this feature and how performance changes without it — a classic **feature ablation study**.

### 📉 Results (Without `study_hours_per_day`):

| Model                                       | R² Score | RMSE    |
| ------------------------------------------- | -------- | ------- |
| Multiple Linear Regression (No Study Hours) | \~0.72   | \~7.45  |
| Ridge Regression                            | \~0.15   | \~14.75 |
| Lasso Regression                            | \~0.16   | \~14.72 |

📌 **Conclusion:**
Model accuracy dropped significantly, proving that `study_hours_per_day` was a key predictor — but other features like `mental_health_rating` and `sleep_hours` still held predictive value.

---

## 📈 Key Insights

* 📘 `study_hours_per_day`, `sleep_hours`, and `mental_health_rating` were strong positive predictors.
* ⚠️ `social_media_hours` and `netflix_hours` had negative correlations with exam scores.
* ✅ Simpler linear models worked best for this data due to linear relationships.

---

## 🚀 How to Run the Project

### 1️⃣ Install dependencies:

```bash
pip install -r requirements.txt
```

### 2️⃣ Open notebook:

```bash
jupyter notebook
```

### 3️⃣ Load the saved model:

```python
import pickle
model = pickle.load(open('best_model_mlr.pkl', 'rb'))
predictions = model.predict(X_new)
```

---

## 📘 Visualizations Included

* 📈 Regression Line (Simple Linear Regression)
* 📊 Actual vs Predicted (Multiple Linear Regression)
* 🟢 Residual Analysis
* 🔥 XGBoost Feature Importance Plot
* 🧪 Ridge & Lasso Coefficient Comparison

---

## 👤 Author

**Marina Nicolai**
Machine Learning Practitioner
📎 [LinkedIn](https://www.linkedin.com/in/marinanicolaidev/) • 🖥 [GitHub](https://github.com/marinanicolai)

```

