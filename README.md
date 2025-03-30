# **Are Some Personality Traits Linked to Being More Selective in Dating?**  
### **Exploring Personality, Selectivity, and Match Success in Speed Dating**

## **👥 Team Member**  
**Pimpisut (Preaw) Puttipongkawin**

---

## **📌 Project Overview**  
Are **ambitious people pickier in dating?** Do **fun-loving people say "yes" more often?** Do **highly attractive people reject more dates?**

This project explores how **personality traits influence dating selectivity**, analyzing whether people with certain traits tend to have **higher standards and fewer matches**. Using real speed dating data, we aim to uncover:  
- Which personality traits are linked to higher selectivity  
- Whether attractive people reject more dates  
- Whether ambitious people are harder to match  

---

## **🎯 Goals**  
- Analyze how personality traits relate to dating selectivity  
- Compare expected vs. actual matches to measure pickiness  
- Identify whether attractiveness, ambition, intelligence, or fun predicts match likelihood  

---

## **📂 Data Collection & Processing**  
### **📊 Data Source**  
- Speed Dating Experiment Dataset (2002–2004)  
- [Kaggle Dataset Link](https://www.kaggle.com/datasets/whenamancodes/speed-dating)  

### **🔍 Features Extracted**  
- **Personality Traits**: `self_attractiveness`, `self_fun`, `self_ambition`, `self_sincerity`, `self_intelligence`  
- **Selectivity Indicators**:  
  - *Expectation vs. Reality*: `expected_matches` vs. `match`  
  - *Decision Selectivity*: `decision_self` vs. `decision_partner`  
  - *Self-Perception vs. Reality*: `self_attractiveness` vs. `match`  

### **🛠 Data Cleaning & Preparation**  
- Dropped rows with missing self-ratings (e.g., attractiveness, fun)  
- Dropped rows with unreliable partner ratings only when needed  
- Renamed features for clarity (e.g., `attr1_1` → `self_attractiveness`)  
- Saved cleaned dataset as `cleaned_speed_dating_data.csv`

---

## **📊 Data Analysis & Modeling**  
We explored how personality traits predict match success using classification models.

### ✅ **Work Completed**  
- **Logistic Regression**  
  - Predicts match using personality traits  
  - Used `class_weight='balanced'` for imbalance correction  
  - Result: Accuracy ~56%, but weak recall and F1 for actual matches  

- **Random Forest Classifier**  
  - Improved performance: Accuracy ~62%, better recall  
  - Showed feature importances  
  - **Top predictors**: `self_attractiveness`, `self_sincerity`, `self_ambition`  
  - Weaker traits: `self_fun`, `self_intelligence`  

#### 📈 **Key Results**  
- Random Forest predicted **145 actual matches** and **883 non-matches**  
- Attractiveness had the strongest influence on prediction  
- Evaluation used: accuracy, precision, recall, F1-score, and confusion matrix  

<img width="726" alt="Feature Importance Bar Chart" src="https://github.com/user-attachments/assets/6e1ae7aa-7d6d-45bc-b748-5c928015b86d" />  
<img width="726" alt="Confusion Matrix" src="https://github.com/user-attachments/assets/81c45269-b4ac-4641-892a-51447fe155b3" />

---

## **📌 Statistical Insights**  
We tested whether traits like ambition and fun are linked to how often participants said “yes” to others.  
- Grouped participants into Low, Medium, High based on trait levels  
- Compared “yes” proportions across groups

<img width="842" alt="Screenshot 2025-03-30 at 12 36 31 AM" src="https://github.com/user-attachments/assets/8018372a-7b64-407a-801c-55da618ff7b8" />

### 🔍 **Findings**  
- **Ambitious people were slightly more selective** (lower yes-rate in high group)  
- **Fun-loving people said yes more often** (higher yes-rate in high group)  
- Trends support original hypotheses and will be further validated with statistical tests  

---

## **📊 Data Visualization**  
Visual tools used to support analysis:  
- Bar charts → Yes-rates by trait groups  
- Confusion matrix → Prediction accuracy breakdown  
- Feature importance chart → Model interpretability  

---

## **🛠️ Test Plan**  
- ✅ **Train-test split** (80/20) for model evaluation  
- ✅ **Metrics used**: accuracy, precision, recall, F1-score  
- ✅ Models tested: Logistic Regression, Random Forest  
- 🔜 **Statistical tests** (e.g., correlation, t-tests) for group comparison  
- 🔜 Optional: Try new models (e.g., XGBoost) or fine-tune for performance  

