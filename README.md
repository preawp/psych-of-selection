# **Are Some Personality Traits Linked to Being More Selective in Dating?**  
### **Exploring Personality, Selectivity, and Match Success in Speed Dating**

## 👥 Team Member  
**Pimpisut (Preaw) Puttipongkawin**

---

## 📌 Final Deliverables (Primary)

**Final Presentation Video:**  
https://www.youtube.com/watch?v=EB5K1pUrAAw  

**Final Slides:**  
https://docs.google.com/presentation/d/14EORtpNHcX-QAviXGwVSRY0N_2-WjBzQtFBSP3fBOi0/edit  

---

## 🕒 Midterm Deliverables (Reference)

**Midterm Presentation Video:**  
https://youtu.be/GfivNqeDmQI?si=onymMymRdp4l3F05  

**Midterm Slides:**  
https://docs.google.com/presentation/d/1KkSF-TpkY1aTzjGL_iEwwzHMdSN_947-DXDuoYH8bKA/edit?usp=sharing  

---

## 📌 Project Overview

Are **ambitious people pickier in dating?**  
Do **fun-loving people say “yes” more often?**  
Do **highly attractive people reject more dates?**

This project explores how **self-perceived personality traits** relate to dating behavior. We use real speed dating data to test whether self-assessments influence how open or selective people are — and whether those traits help predict match success.

---

## 🎯 Goals

- Analyze how personality traits relate to dating selectivity  
- Compare expected vs. actual matches to measure pickiness  
- Predict whether someone will get a match based on self-rated traits  
- Explore behavioral trends behind openness and attraction

---

## 📂 Data Collection & Processing

**📁 Data Source:** Kaggle (Speed Dating Experiment, 2002–2004)  
**🔑 Features Used:**  
- Personality traits: `self_attractiveness`, `self_fun`, `self_ambition`, `self_sincerity`, `self_intelligence`  
- Decision data: `decision_self`, `decision_partner`, `match`, `expected_matches`

**🧼 Cleaning Steps:**  
- Dropped missing self-ratings  
- Renamed columns for clarity  
- Filtered unreliable responses  
- Saved cleaned version: `cleaned_speed_dating_data.csv`  
- Calculated yes-rate per participant  
- Grouped participants into selectivity levels (High / Medium / Low)

---

## 🔍 Statistical & Behavioral Analysis

### 🧠 Feature Importance (Random Forest)
- Top traits: `self_attractiveness`, `self_ambition`, `self_sincerity`  
- Weak traits: `self_fun`, `self_intelligence`

**Feature Importance Plot:**  
![Random Forest Feature Importance](path/to/your/feature_importance_rf.png) <!-- update this path if needed -->

---

### 📉 Trait-Level Insights (Low vs. High Self-Ratings)
- High sincerity & intelligence → slightly higher yes-rates  
- High ambition & attractiveness → slightly lower yes-rates  
- Fun: no clear pattern  
- No single trait fully explained openness

**Trait Group Bar Plot:**  
![Trait Bar Plot](path/to/your/trait_bar_plot.png)

---

### 📐 T-Test Results

| Trait         | P-Value | Result                  |
|---------------|---------|-------------------------|
| Sincerity     | 0.012   | ✅ Significant           |
| Intelligence  | 0.027   | ✅ Significant           |
| Attractiveness| 0.046   | ✅ Significant           |
| Ambition      | 0.390   | ❌ Not significant       |
| Fun           | 0.280   | ❌ Not significant       |

---

### 🎭 Trait Interactions

- **Ambition × Fun:**  
  Low Ambition + Low Fun → highest yes-rate  
- **Attractiveness × Intelligence:**  
  Low Attractiveness + High Intelligence → highest yes-rate group

**Interaction Plot (Ambition × Fun):**  
![Ambition x Fun Plot](path/to/your/ambition_fun_plot.png)

**Interaction Plot (Attractiveness × Intelligence):**  
![Attr x Intel Plot](path/to/your/attr_intel_plot.png)

---

## 🤖 Modeling & Prediction

We tested multiple models to predict match success.

### 🔹 Logistic Regression
- Accuracy: ~56%  
- Very low recall for actual matches  
- Too simple to model real dating patterns  
> **Baseline only**

---

### 🌳 Decision Tree (max_depth=4)
- Accuracy: 84%  
- Match recall: 0.01  
- Predicted “No Match” for nearly everyone

**Confusion Matrix – Decision Tree:**  
![Confusion Tree](path/to/confusion_tree.png)

---

### 🌲 Random Forest (Tuned)
- Accuracy: ~63%  
- Match recall: 0.47  
- Used class balancing + hyperparameter tuning  
> Strong balance model

**Confusion Matrix – Random Forest:**  
![Confusion RF](path/to/confusion_rf.png)

---

### ⚡ XGBoost (Tuned)
- Accuracy: ~59%  
- Match recall: 0.55  
- Tuned depth, learning rate, and `scale_pos_weight`

**Confusion Matrix – XGBoost:**  
![Confusion XGB](path/to/confusion_xgb.png)

---

### 🤝 Ensemble Models

#### ✅ Equal-Weight Ensemble (RF + XGBoost, 50/50)
- Accuracy: ~61%  
- Match recall: 0.51  
- F1 (match): 0.30  
> Final model — best recall-accuracy balance

**Confusion Matrix – Ensemble (50/50):**  
![Confusion Ensemble](path/to/confusion_ensemble.png)

#### ⚠️ Weighted Ensemble (70% XGBoost)
- Accuracy: ~34%  
- Recall (match): 0.85  
- Predicted “yes” too often — overfit to positive class

---

## 📊 Model Summary

| Model                  | Accuracy | Recall (Match) | F1 (Match) | Notes                            |
|------------------------|----------|----------------|------------|----------------------------------|
| Logistic Regression    | 56%      | 0.24           | 0.22       | Weak baseline                    |
| Decision Tree          | 84%      | 0.01           | 0.01       | Overfit, poor recall             |
| Tuned Random Forest    | 63%      | 0.47           | 0.29       | Great balance                    |
| Tuned XGBoost          | 59%      | 0.55           | 0.30       | Boosted match detection          |
| Ensemble (50/50) ✅     | 61%      | 0.51           | 0.30       | ✅ Final model – balanced         |
| Ensemble (70% XGB)     | 34%      | 0.85           | 0.29       | Too aggressive                   |

---

## 💡 Key Findings

- Traits like **sincerity**, **intelligence**, and **attractiveness** are linked to openness  
- **Ambitious** participants were more selective  
- No single trait can explain behavior — context matters  
- Final ensemble model predicts **half of all real matches**  
- Dating prediction is hard — but there *are* patterns!

---

## 🛠️ How to Reproduce

```bash
# Clone the repository
git clone [your-repo-url]
cd your-repo-folder

# Create virtual environment
python3 -m venv venv
source venv/bin/activate

# Install dependencies using Makefile
make install
