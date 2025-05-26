
# 🎓 Student Exam Score Prediction

This project predicts student exam scores based on behavioral and environmental factors such as study hours, sleep, screen time, and more. Multiple machine learning models were trained and evaluated to identify the best-performing solution.


---

## 📁 Dataset

- 1,000 student records
- Features include:
  - `age`, `study_hours_per_day`, `social_media_hours`, `netflix_hours`
  - `part_time_job`, `attendance_percentage`, `sleep_hours`
  - `exercise_frequency`, `mental_health_rating`
  - `extracurricular_participation`, `diet_quality_encoded`, `internet_quality_encoded`
- Target variable: `exam_score`

### 📌 Preprocessing:
- Encoded categorical features
- Standardized numeric columns
- Train-test split (80/20)

---

## 🧠 Modeling Approach

### Models Tested:
- Simple Linear Regression
- **✅ Multiple Linear Regression** (Best)
- Random Forest Regressor
- XGBoost Regressor

### Metrics Used:
- **R² Score**
- **RMSE** (Root Mean Squared Error)

---

## 📊 Model Performance

| Model                     | R² Score | RMSE  |
|--------------------------|----------|-------|
| Simple Linear Regression | 0.67     | 9.20  |
| **Multiple Linear Regression** | **0.90** | **5.10** ✅ |
| Random Forest            | 0.85     | 6.15  |
| XGBoost                  | 0.88     | 5.60  |

> Cross-validated Multiple Linear Regression R² ≈ 0.896, RMSE ≈ 5.38

---

## ✅ Best Model

**Multiple Linear Regression**
- Interpretable coefficients
- Fast training and prediction
- No overfitting (confirmed via cross-validation)

Saved using:
```python
import pickle
with open('best_model_mlr.pkl', 'wb') as f:
    pickle.dump(model, f)
````

---

## 📈 Key Insights

* `study_hours_per_day`, `sleep_hours`, and `mental_health_rating` were top predictors.
* `social_media_hours` and `netflix_hours` negatively impacted performance.
* Simpler models can outperform complex ones when data is mostly linear.

---


## 🚀 How to Run

### 📦 Install dependencies:

```bash
pip install -r requirements.txt
```

### ▶️ Run notebook:

```bash
jupyter notebook
```

### 📥 Load trained model:

```python
import pickle
model = pickle.load(open('best_model_mlr.pkl', 'rb'))
predictions = model.predict(X_new)
```

---

## 📘 Example Visuals

* 📈 Regression Line (Simple Model)
* 📊 Actual vs Predicted (Multiple Regression)
* 🔍 Residual Analysis
* 🔥 XGBoost Feature Importance

---


## 👤 Author

**Marina Nicolai**
Machine Learning Practitioner | [LinkedIn](https://www.linkedin.com/in/marinanicolaidev/) | [GitHub](https://github.com/marinanicolai)

---


