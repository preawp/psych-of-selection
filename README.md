# **Are Some Personality Traits Linked to Being More Selective in Dating?**  
### **Exploring Personality, Selectivity, and Match Success in Speed Dating**

## **👥 Team Member**  
**Pimpisut (Preaw) Puttipongkawin**

---
Midterm Report Presentation:
https://youtu.be/GfivNqeDmQI?si=onymMymRdp4l3F05

 Midterm Report Slides:
https://docs.google.com/presentation/d/1KkSF-TpkY1aTzjGL_iEwwzHMdSN_947-DXDuoYH8bKA/edit?usp=sharing

## **📌 Project Overview**  
Are **ambitious people pickier in dating?** Do **fun-loving people say "yes" more often?** Do **highly attractive people reject more dates?**

This project explores how **personality traits influence dating selectivity**, using real speed dating data to investigate whether self-perceived traits influence actual dating behavior and match outcomes.

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
> 📌 *Note: Feature importances are based on the default Random Forest model. Rankings were consistent after tuning (n_estimators = 100).*
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

These initial trends align with our hypotheses and will be further explored with statistical tests in the next phase.
---

## **📊 Visualizations**  
- Histogram of trait distributions  
- Bar plots of yes-rates by trait groups  
- Confusion matrices (Random Forest, XGBoost)  
- Feature importance chart  

---

## ✅ Test Plan & Next Steps  
- Completed:  
  - 80/20 train-test split  
  - Used classification metrics: accuracy, precision, recall, F1  
  - Trained and evaluated: Logistic Regression, Random Forest, XGBoost  
- In Progress:  
  - Statistical testing (e.g., t-tests, correlation) to validate behavioral patterns  
  - Refining selectivity grouping methods  
- Optional:  
  - More model tuning or new classifiers (e.g., Decision Tree)  
  - Additional behavioral insights based on visualizations  

---

## 💡 Key Findings & Behavioral Takeaways

- Participants who rated themselves **higher in intelligence or sincerity** were more likely to say "yes" to potential matches.
- Surprisingly, those with **higher self-rated attractiveness or ambition** were slightly more selective — suggesting confidence may increase pickiness.
- In an interaction plot, the group with **low attractiveness but high intelligence** showed the **highest yes-rate**, hinting that perceived intellect might compensate for lower appearance confidence.
- T-tests confirmed that sincerity, intelligence, and attractiveness all showed **statistically significant differences** in yes-rates between low and high self-raters.
- However, overall differences were relatively small — suggesting that **self-perception alone doesn’t fully explain dating behavior**.
- Our best model (an ensemble of Tuned XGBoost + Random Forest) reached **0.53 recall for actual matches**, showing that **real-world attraction is hard to predict, even with personality self-assessments**.

## 🔧 How to Build and Run

To reproduce the results:

1. Clone the repository  
2. Create a virtual environment and install dependencies  
```bash
make install

