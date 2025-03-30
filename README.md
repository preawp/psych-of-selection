# **Are Some Personality Traits Linked to Being More Selective in Dating?**  
### **Exploring Personality, Selectivity, and Match Success in Speed Dating**

## **👥 Team Member**  
**Pimpisut (Preaw) Puttipongkawin**

---

## **📌 Project Overview**  
Are **ambitious people pickier in dating?** Do **fun-loving people say "yes" more often?** Do **highly attractive people reject more dates?**

This project explores how **personality traits influence dating selectivity**, using real speed dating data to investigate whether certain self-perceptions correlate with actual behavior and match outcomes.

---

## **🎯 Goals**  
- Analyze how personality traits relate to dating selectivity  
- Compare expected vs. actual matches to measure pickiness  
- Predict match likelihood based on personality traits  

---

## **📂 Data Collection & Processing**  
### **📊 Data Source**  
- Speed Dating Experiment Dataset (2002–2004)  
- [Kaggle Dataset Link](https://www.kaggle.com/datasets/whenamancodes/speed-dating)  

### **🔍 Features Extracted**  
- `self_attractiveness`, `self_fun`, `self_ambition`, `self_sincerity`, `self_intelligence`  
- Selectivity indicators: `expected_matches`, `decision_self`, `match`  

### **🛠 Data Cleaning**  
- Dropped rows with missing self-ratings  
- Kept partner ratings optional  
- Renamed features for clarity  
- Cleaned dataset saved to `data/cleaned_speed_dating_data.csv`

---

## **📊 Modeling & Prediction**  
We explored whether personality traits can predict match success.

### ✅ **Models Tested**  
- **Logistic Regression**  
  - Accuracy: ~56%  
  - Struggled with identifying actual matches (low recall/F1 for class 1)

- **Random Forest (Tuned)**  
  - Accuracy: ~63%  
  - Much better recall for class 1 (match = yes)  
  - Top predictors: `self_attractiveness`, `self_sincerity`, `self_ambition`  

- **XGBoost Classifier**  
  - Highest overall accuracy: **~83%**  
  - Weak recall for matches (class 1), predicting mostly non-matches  

### 📈 **Key Outputs**  
**🟩 Random Forest – Feature Importance Plot**  
> *Shows which personality traits had the strongest influence on predictions*  
<img width="957" alt="Screenshot 2025-03-30 at 1 26 38 AM" src="https://github.com/user-attachments/assets/96c8105d-13a3-47e6-9f92-ba0de5e86aeb" />

**🟪 Random Forest – Confusion Matrix**  
> *Correctly predicted 145 actual matches. Balanced performance.*  
<img width="719" alt="Screenshot 2025-03-30 at 1 27 02 AM" src="https://github.com/user-attachments/assets/16c92ea9-fba9-4ecd-a65a-f35a42c3a656" />

**🟦 XGBoost – Confusion Matrix**  
> *Very high overall accuracy (~83%), but struggled to identify matches (low recall for class 1)*  
<img width="816" alt="Screenshot 2025-03-30 at 1 30 20 AM" src="https://github.com/user-attachments/assets/0ddc4b8a-675a-4b0b-a326-81cc3da348e0" />

## 📋 **Model Performance Summary**

| Model                | Accuracy | Precision (Match) | Recall (Match) | F1-Score (Match) | Notes |
|---------------------|----------|-------------------|----------------|------------------|-------|
| **Logistic Regression** | ~56%     | 0.20              | 0.24           | 0.22             | Linear model, poor at capturing complex patterns. |
| **Random Forest**        | ~63%     | 0.21              | **0.47**       | 0.29             | Best balance between accuracy and match recall. |
| **Tuned Random Forest**  | **~63.2%** | 0.21              | **0.47**       | 0.29             | Improved slightly after increasing `n_estimators`. |
| **XGBoost**              | **~83%**  | 0.39              | **0.07**       | 0.12             | High overall accuracy but fails to detect actual matches. |

---

## **📌 Statistical Insight (Selectivity)**  
We grouped participants by trait level (Low / Medium / High) to analyze selectivity.

- **Ambition**: Higher ambition correlated with lower yes-rate  
- **Fun**: High-fun group said yes more often
  
<img width="958" alt="Screenshot 2025-03-30 at 1 27 34 AM" src="https://github.com/user-attachments/assets/5dce0f88-f9cc-45fb-91f2-c993c6df35d7" />

---

## **📊 Visualizations**  
- Histogram of trait distributions  
- Bar plots of yes-rates by trait groups  
- Confusion matrices (Random Forest, XGBoost)  
- Feature importance chart  

---

## **🛠️ Test Plan**  
- ✅ 80/20 train-test split  
- ✅ Used classification metrics: accuracy, precision, recall, F1  
- ✅ Trained: Logistic Regression, Random Forest, XGBoost  
- 🔜 Continue statistical testing (e.g., t-tests, correlation)  
- 🔜 Optional: More model tuning or feature engineering  

---

