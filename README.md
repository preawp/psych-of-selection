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
- **Saved cleaned dataset** to `data/cleaned_speed_dating_data.csv`.

---

## **📊 Data Analysis & Modeling**  
We began by exploring how personality traits relate to match success using classification models.

### **✅ Work Completed**  
- **Logistic Regression Model**  
   - Used to predict whether someone would receive a match based on self-ratings.  
   - Applied `class_weight='balanced'` to address class imbalance (most participants did not match).  
   - Result: Moderate accuracy (~56%), but weak at identifying actual matches (low recall and precision for class 1).  

- **Random Forest Classifier**  
   - Improved performance over logistic regression, especially for recall.  
   - Achieved accuracy of **~62%**, correctly identifying more real matches.  
   - Returned feature importances to identify key traits for match success.  
   - **Top predictors were `self_attractiveness`, `self_sincerity`, and `self_ambition`**, while `self_fun` and `self_intelligence` had less impact.

#### 📈 **Key Results**  
- Random Forest correctly predicted **145 actual matches** and **883 non-matches**, as shown in the confusion matrix.  
- **Attractiveness** had the strongest influence, while **fun** and **intelligence** were the weakest predictors.  
- The confusion matrix and feature importance plot helped visualize how well the model performed.

<img width="726" alt="Feature Importance Bar Chart" src="https://github.com/user-attachments/assets/6e1ae7aa-7d6d-45bc-b748-5c928015b86d" />  
<img width="726" alt="Confusion Matrix" src="https://github.com/user-attachments/assets/81c45269-b4ac-4641-892a-51447fe155b3" />  

---

## **📌 Next Steps**  
- **Statistical analysis**:  
   - Are ambitious people more selective than others?  
   - Do fun-loving participants say yes more often than serious ones?  
- **Create comparison groups** (Low, Medium, High selectivity) and explore patterns.  
- **Optional**: Try other models (e.g., XGBoost) or tune hyperparameters for improvement.

---

## **📊 Data Visualization**  
We will visualize insights using:  
- **Scatter plots** → Selectivity vs. personality traits.  
- **Box plots** → Differences in pickiness across groups.  
- **Bar charts** → Match rates based on personality traits.  

---

## **🛠️ Test Plan**  

To ensure reliable insights:  
- ✅ **Train-test split** (80% train / 20% test) was used to evaluate model performance.  
- ✅ **Evaluation metrics** included accuracy, precision, recall, F1-score, and confusion matrix.  
- 🔜 **Statistical tests** (e.g., correlation analysis, t-tests) will be used in the next phase to compare selectivity across groups.  
- ✅ **Machine learning models** (Logistic Regression and Random Forest) were tested to predict match likelihood based on traits.  
- 🔜 May explore additional models (e.g., Decision Tree, XGBoost) if needed.

---

