# Final_Project

# 📊 Podcast Listening Time Prediction

This project explores machine learning approaches to predict podcast episode listening time based on various episode metadata and features. Three ensemble models were developed and evaluated: **XGBoost**, **Random Forest**, and **LightGBM**.

---

## 🧠 Main Models

| Model         | File                                  | Description                                                                 |
|---------------|---------------------------------------|-----------------------------------------------------------------------------|
| XGBoost       | `predict_podcast_using_xgb-develop.ipynb` | Uses gradient boosting decision trees with extensive feature engineering and hyperparameter tuning. |
| Random Forest | `predict_podcast_using_rf_nf.ipynb`   | A robust baseline ensemble model known for its strong generalization.       |
| LightGBM      | `yasuko_LightGBM.ipynb`               | Fast, efficient, and scalable boosting model for large datasets.            |

---

## 🔍 Feature Engineering

### 1. Episode Number Extraction

- **Feature Name:** `Episode_Number`
- Extracted numeric episode order from `Episode_Title` (e.g., “Episode 12”)
- Motivation: Valuable ordering signal for user engagement

---

### 2. Podcast-Level Listening Trend

- **Feature Name:** `Podcast_Trend_Slope`
- Motivation: Listening time may vary depending on episode number for each podcast
- Method:
    - Calculated slope of Episode Number vs Listening Time using `np.polyfit`
    - Used **K-Fold cross-validation** to avoid data leakage
    - Applied precomputed slopes to test set via mapping

---

### 3. Long Episode Indicator

- **Feature Name:** `Is_Long_Episode`
- Binary value — 1 if `Episode_Length_minutes > 60`, else 0
- Purpose: Distinguish long-form vs short-form content
- *Note: Later dropped due to overlap with `Episode_Length_minutes`*

---

### 4. Ad Ratio

- **Feature Name:** `Ad_Ratio`
- Formula: `Number_of_Ads / Episode_Length_minutes`
- Purpose: Represents ad density, which may impact user retention

---

### ✅ Validation via Feature Importance (RandomForest)

- `Episode_Length_minutes`: Most influential feature
- `Ad_Ratio`: Ranked second
- `Podcast_Trend_Slope`, `Episode_Number`: Lower impact but useful
- `Is_Long_Episode`: Low importance → removed

---

## 📈 Key Findings

- The **Random Forest** model showed the best generalization ability.
- Feature engineering captured podcast-specific patterns such as:
    - `Ad_Ratio` (ad density)
    - `Podcast_Trend_Slope` (episode-level trend)
- Evaluation metric: **Root Mean Squared Error (RMSE)**

---

## 🔧 Technologies Used

- Python (pandas, numpy, matplotlib, seaborn, scikit-learn, xgboost, lightgbm)
- Jupyter Notebook
- Git (for version control and collaboration)

---
## 📁 Project Structure

```
├── predict_podcast_using_xgb-develop.ipynb
├── predict_podcast_using_rf_nf.ipynb
├── yasuko_LightGBM.ipynb
└── README.md
```

---

## ✅ Conclusion

- 1️⃣ **Episode length** is the most influential factor in predicting listening time.
- Engineered features like `Ad_Ratio` and `Podcast_Trend_Slope` added valuable context.
- All three models—**Random Forest, LightGBM, and XGBoost**—performed reliably.
- **Careful feature engineering and outlier handling** significantly contributed to prediction quality.
- 👉 **The Random Forest model** demonstrated the best generalization performance, achieving strong accuracy while avoiding overfitting.

---

## 📌 Author

**Aspyn Song** – Data Analyst / Data Scientist in training  
📧 jeongfree25@gmail.com
**Yasuko** – Data Analyst / Data Scientist in training  
📧 ysk06.sss@gmail.com
