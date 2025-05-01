# **Are Some Personality Traits Linked to Being More Selective in Dating?**  
### **Exploring Personality, Selectivity, and Match Success in Speed Dating**

## 👥 Team Member  
**Pimpisut (Preaw) Puttipongkawin**

---

## 🎥 Final Deliverables

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

### ❓ Research Questions
- Are **ambitious people** pickier in dating?  
- Do **fun-loving people** say “yes” more often?  
- Do **highly attractive people** reject more dates?

This project explores how **self-perceived personality traits** relate to dating behavior. Using real-world speed dating data, we investigate whether these traits influence selectivity and match outcomes.

To begin, we visualized how participants rated themselves. Below is the distribution of **self-rated attractiveness** — one of the key traits used in modeling:

<img width="756" alt="Screenshot 2025-05-01 at 4 37 42 PM" src="https://github.com/user-attachments/assets/9d11503f-fd32-49bb-91a1-59ea2c835ab3" />

> Most participants rated themselves between 10 and 30 (out of 100), with very few rating themselves above 60.  
> This skewed distribution helped guide our grouping strategy (e.g., splitting traits into "Low" vs. "High").

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

<img width="760" alt="Screenshot 2025-05-01 at 4 40 37 PM" src="https://github.com/user-attachments/assets/98efc685-ea57-42cf-9765-01c7b5aba788" />

> High-fun participants were slightly more open. In contrast, high-ambition participants were more selective, with lower yes-rates.
> 
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

**📊 Visualization: Average Yes-Rate by Trait Level**

<img width="758" alt="Screenshot 2025-05-01 at 4 46 01 PM" src="https://github.com/user-attachments/assets/603e17fa-6377-46dc-a1b3-39d1f96c15ea" />

### 🎭 Trait Interactions
We explored whether combinations of traits affected behavior:

- **Ambition × Fun:**  
  → Low Ambition + Low Fun had the highest yes-rate


<img width="759" alt="Screenshot 2025-05-01 at 4 43 10 PM" src="https://github.com/user-attachments/assets/ebcf35f3-593d-486d-af05-ccc27737c1fc" />

  
- **Attractiveness × Intelligence:**  
  → Low Attractiveness + High Intelligence showed surprising openness
  
<img width="755" alt="Screenshot 2025-05-01 at 4 44 25 PM" src="https://github.com/user-attachments/assets/13eb1f34-bbed-4712-8199-614c7001a8f4" />


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

<img width="754" alt="Screenshot 2025-05-01 at 4 51 40 PM" src="https://github.com/user-attachments/assets/36624f70-20b6-46b1-bc95-ffaddb9a686d" />

---

### 🌲 Random Forest (Tuned)
- Accuracy: ~63%  
- Match recall: 0.47  
- Tuned `n_estimators`, `max_depth`, `min_samples_split`, and used `class_weight='balanced'`  
- Good balance between detecting matches and avoiding false positives  
→ **Strong general-purpose model**

<img width="760" alt="Screenshot 2025-05-01 at 4 48 47 PM" src="https://github.com/user-attachments/assets/8eee94ca-418a-4468-bf06-91b6f6916fe1" />

**📊 Feature Importances from Random Forest**  
Shows the most predictive self-rated traits used by the model.

<img width="759" alt="Screenshot 2025-05-01 at 4 47 33 PM" src="https://github.com/user-attachments/assets/e7ea8266-d37b-4aea-8e8e-45c0e4c9fc30" />

---

### ⚡ XGBoost (Tuned)
- Accuracy: ~59%  
- Match recall: improved from 8% → **55%** after tuning  
- Tuned tree depth, learning rate, boosting weight  
- F1-score for matches: 0.30  
→ **Better at finding matches, but still noisy**

<img width="754" alt="Screenshot 2025-05-01 at 4 49 22 PM" src="https://github.com/user-attachments/assets/ecb24571-39da-4656-8cab-a691d331c7cc" />

---

### 🤝 Ensemble Models

#### ✅ Equal-Weight Ensemble (RF + XGBoost, 50/50)
- Accuracy: ~61%  
- Match recall: 51%  
- F1-score: 0.30  
- Caught **135 real matches**  
→ **Best trade-off overall**

<img width="757" alt="Screenshot 2025-05-01 at 4 49 42 PM" src="https://github.com/user-attachments/assets/9d97ac6e-313e-43b2-be97-454117294d52" />

#### ⚠️ Weighted Ensemble (70% XGB)
- Accuracy: ~34%  
- Match recall: 85%  
- Predicted “yes” too often — many false positives  
→ Too risky, not balanced

<img width="756" alt="Screenshot 2025-05-01 at 4 50 42 PM" src="https://github.com/user-attachments/assets/9c4a82ba-d2b1-4fc4-a4bb-8b223dae3b57" />

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

