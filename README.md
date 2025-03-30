# **Are Some Personality Traits Linked to Being More Selective in Dating?**  
### **Exploring Personality, Selectivity, and Match Success in Speed Dating**  

## **👥 Team Member**  
**Pimpisut (Preaw) Puttipongkawin**  

---

## **📌 Project Overview**  
Are **ambitious people pickier in dating?** Do **fun-loving people say "yes" more often?** Do **highly attractive people reject more dates?**  

This project explores **how personality traits influence dating selectivity**, analyzing whether people with certain traits tend to have **higher standards and fewer matches**. Using real speed dating data, we aim to uncover:  
- **Which personality traits are linked to higher selectivity?**  
- **Do more attractive people reject more dates?**  
- **Are ambitious people less likely to match due to high expectations?**  

---

## **🎯 Goals**  
- **Analyze how personality traits relate to dating selectivity.**  
- **Compare expected vs. actual matches to measure pickiness.**  
- **Identify whether attractiveness, ambition, intelligence, or fun predicts match likelihood.**  

---

## **📂 Data Collection & Processing**  
### **📊 Data Source**  
- **Speed Dating Experiment Dataset (2002–2004)**  
- [Dataset Link](https://www.kaggle.com/datasets/whenamancodes/speed-dating)  

### **🔍 Features Extracted**  
- **Personality Traits:** `self_attractiveness`, `self_fun`, `self_ambition`, `self_sincerity`, `self_intelligence`  
- **Selectivity Indicators:**  
   - **Expectation vs. Reality:** `expected_matches` vs. `match`  
   - **Decision Selectivity:** `decision_self` vs. `decision_partner`  
   - **Self-Perception vs. Reality:** `self_attractiveness` vs. `match`  

### **🛠 Data Cleaning & Preparation**  
- **Dropped rows with missing self-ratings** (attractiveness, fun, etc.) to ensure clean modeling.  
- **Dropped rows with unreliable partner ratings** only when required.  
- **Renamed features** for better readability (`attr1_1` → `self_attractiveness`, etc.).  
- **Saved cleaned dataset** to `data/cleaned_speed_dating_data.csv` for use in modeling.

---

## **📊 Data Analysis & Modeling**  
We began by testing how personality traits relate to match success using machine learning models.

### **✅ Work Completed**  
- **Logistic Regression Model:**  
   - Goal: Predict match success based on traits like `self_attractiveness`, `self_fun`, `self_ambition`, etc.  
   - Used `class_weight='balanced'` to address class imbalance (most participants did not match).  
   - Result: Moderate overall accuracy, but poor recall for predicting actual matches (label = 1).

- **Random Forest Classifier:**  
   - Outperformed logistic regression in handling class imbalance and improving recall.  
   - Returned **feature importances**, helping us understand which traits matter most.  
   - **Top predictors were `self_attractiveness`, `self_sincerity`, and `self_ambition`**.  
   - `self_fun` and `self_intelligence` were less predictive of match success.

<img width="816" alt="Screenshot 2025-03-29 at 9 17 07 PM" src="https://github.com/user-attachments/assets/6e1ae7aa-7d6d-45bc-b748-5c928015b86d" />

- **Evaluation:**  
   - Performance assessed using **accuracy**, **precision**, **recall**, **F1-score**, and **confusion matrix**.  
   - Feature importances were visualized with a bar plot.

### **📌 Next Steps**  
- **Statistical correlation analysis:**  
   - Are ambitious people more selective?  
   - Do fun-loving people match more often?  
- **Selectivity groups (Low, Medium, High):**  
   - Group participants based on how picky they were and compare behaviors.  

---

## **📊 Data Visualization**  
Data visualization will be used to highlight trends:  
- **Scatter plots** → Selectivity vs. personality traits.  
- **Box plots** → Differences in pickiness across groups.  
- **Bar charts** → Match rates based on personality traits.  

---

## **🛠️ Test Plan**  
To ensure reliable insights:  
- **Train-test split** (e.g., 80% train, 20% test) to evaluate model performance.  
- **Statistical tests** to confirm significant differences between groups.  
- **Optional: Machine learning models** to predict match likelihood based on traits.  

---

