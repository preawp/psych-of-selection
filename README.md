# **Are Some Personality Traits Linked to Being More Selective in Dating?**  
### **Exploring Personality, Selectivity, and Match Success in Speed Dating**

## 👥 Team Member  
**Pimpisut (Preaw) Puttipongkawin**

---

## 🎥 Presentations & Slides

## 📌 Final Deliverables

**Final Presentation Video:**  
https://www.youtube.com/watch?v=EB5K1pUrAAw  

**Final Slides:**  
https://docs.google.com/presentation/d/14EORtpNHcX-QAviXGwVSRY0N_2-WjBzQtFBSP3fBOi0/edit  

---

## 🕒 Midterm Deliverables

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
- Calculated each participant’s **yes-rate**  
- Grouped participants into **High / Medium / Low selectivity**

---

## 🔍 Statistical & Behavioral Analysis

### 🧠 Feature Importance (Random Forest)
- Top traits: `self_attractiveness`, `self_ambition`, `self_sincerity`  
- Weak traits: `self_fun`, `self_intelligence`  
- Helped us decide which features mattered most in predicting matches

### 📉 Trait-Level Insights (Low vs. High Self-Ratings)
- High sincerity & intelligence → slightly higher yes-rates  
- High ambition & attractiveness → slightly lower yes-rates  
- Fun: no strong pattern  
- Overall effects were small — no single trait was dominant

### 📐 T-Test Results
We used independent t-tests to compare low vs. high trait groups:

| Trait         | P-Value | Result                  |
|---------------|---------|-------------------------|
| Sincerity     | 0.012   | ✅ Significant           |
| Intelligence  | 0.027   | ✅ Significant           |
| Attractiveness| 0.046   | ✅ Significant           |
| Ambition      | 0.390   | ❌ Not significant       |
| Fun           | 0.280   | ❌ Not significant       |

→ Sincerity, intelligence, and attractiveness had meaningful behavioral effects

### 🎭 Trait Interactions
We explored whether combinations of traits affected behavior:

- **Ambition × Fun:**  
  → Low Ambition + Low Fun had the highest yes-rate  
- **Attractiveness × Intelligence:**  
  → Low Attractiveness + High Intelligence showed surprising openness  

These were not statistically strong, but added depth to our analysis.

---

## 🤖 Modeling & Prediction

We tested multiple models to predict whether a participant would receive a match.

### 📌 Logistic Regression
- Accuracy: ~56%  
- Very low recall for actual matches (class 1)  
- Linear model struggled with complex patterns  
→ **Baseline only**

---

### 🌳 Decision Tree (max_depth=4)
- Accuracy: 84%  
- Match recall: 0.01 → almost all predictions = “No Match”  
- Easy to interpret, but useless for catching matches  
→ **Not suitable**

---

### 🌲 Random Forest (Tuned)
- Accuracy: ~63%  
- Match recall: 0.47  
- Tuned `n_estimators`, `max_depth`, `min_samples_split`, and used `class_weight='balanced'`  
- Good balance between detecting matches and avoiding false positives  
→ **Strong general-purpose model**

---

### ⚡ XGBoost (Tuned)
- Accuracy: ~59%  
- Match recall: improved from 8% → **55%** after tuning  
- Tuned tree depth, learning rate, boosting weight  
- F1-score for matches: 0.30  
→ **Better at finding matches, but still noisy**

---

### 🤝 Ensemble Models

#### ✅ Equal-Weight Ensemble (RF + XGBoost, 50/50)
- Accuracy: ~61%  
- Match recall: 51%  
- F1-score: 0.30  
- Caught **135 real matches**  
→ **Best trade-off overall**

#### ⚠️ Weighted Ensemble (70% XGB)
- Accuracy: ~34%  
- Match recall: 85%  
- Predicted “yes” too often — many false positives  
→ Too risky, not balanced

---

## 📊 Model Summary

| Model                  | Accuracy | Recall (Match) | F1 (Match) | Notes                              |
|------------------------|----------|----------------|------------|-------------------------------------|
| Logistic Regression    | 56%      | 0.24           | 0.22       | Weak baseline                       |
| Decision Tree          | 84%      | 0.01           | 0.01       | Overfit, no match detection         |
| Tuned Random Forest    | 63%      | 0.47           | 0.29       | Strong balance                      |
| Tuned XGBoost          | 59%      | 0.55           | 0.30       | Good recall, lower precision        |
| Ensemble (50/50) ✅     | **61%**  | **0.51**       | **0.30**   | ✅ Final model — balanced and solid |
| Ensemble (70% XGB)     | 33%      | 0.85           | 0.29       | High recall, bad accuracy           |

---

## 💡 Key Findings

- Self-rated **sincerity**, **intelligence**, and **attractiveness** were most related to openness  
- Participants high in **ambition** tended to be more selective  
- Personality traits alone are **not strong predictors** of dating behavior  
- Our final ensemble model caught more than **half of all real matches**, with acceptable accuracy  
- Even smart models struggle to predict human behavior in dating — but we found real patterns

---

## 🛠️ How to Reproduce

```bash
# Clone the repository
git clone [your-repo-url]
cd your-repo-name

# Create virtual environment
python3 -m venv venv
source venv/bin/activate

# Install dependencies
make install

# Run notebooks (EDA, modeling, evaluation)
