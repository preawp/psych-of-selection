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
- **Speed Dating Experiment Dataset (2002-2004)**
- [Dataset Link](https://www.kaggle.com/datasets/whenamancodes/speed-dating)  

### **🔍 Features Extracted**  
- **Personality Traits:** `attractive`, `funny`, `ambition`, `sincere`, `intelligence`  
- **Selectivity Indicators:**  
   - **Expectation vs. Reality:** `expected_num_matches` vs. `match`  
   - **Decision Selectivity:** `decision` vs. `decision_o`  
   - **Self-Perception vs. Reality:** `attractive` vs. `match`  

### **🛠 Data Cleaning & Preparation**  
- **Handling missing values** and inconsistent responses.  
- **Standardizing numeric traits** for better comparability.  
- **Filtering out unreliable or incomplete responses.**  

---

## **📊 Data Analysis & Modeling**  
This project will explore:  
- **Statistical correlations** (Are ambitious people pickier? Do fun-loving people match more?)  
- **Comparison groups** (Low, Medium, High selectivity groups)  
- **Regression models** (Which traits best predict selectivity?)  //Done, random forest

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

