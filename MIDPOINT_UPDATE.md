Midpoint Report: Psych of Selection

1. Preliminary Visualizations

We explored the dataset using various visualizations to understand patterns in dating selectivity:

Self vs. Partner-Rated Attractiveness: Self-ratings tend to be higher than partner ratings.
Attractiveness vs. Match Rate: More attractive individuals have slightly higher match rates.
Gender-based Differences: Men rate themselves higher on attractiveness compared to women.
Correlation Heatmap: Fun, attractiveness, and sincerity show positive correlations with match success.
2. Data Processing

Selected key features: self_attractiveness, partner_attractiveness, self_fun, self_sincerity, self_intelligence, self_ambition, match, decision_self, decision_partner.
Handled missing values by imputing medians where appropriate.
Standardized numeric traits for better comparison.
3. Data Modeling So Far

Hypothesis Testing:
Are attractive people more selective? T-test shows higher self-rated attractiveness correlates with increased selectivity.
Are ambitious people less likely to match? Negative correlation suggests ambitious individuals have fewer matches.
Do fun people match more? Boxplot analysis indicates a higher fun score increases match likelihood.
Preliminary Logistic Regression Model:
Goal: Predict match outcome using personality traits.
Features: self_attractiveness, self_fun, self_ambition, self_sincerity, self_intelligence.
Initial Accuracy: Achieved ~X% accuracy in predicting match success.
4. Preliminary Results

Attractiveness and fun are strong predictors of matches.
Ambition negatively correlates with match success, supporting the idea that ambitious individuals are pickier.
Men rate themselves higher on attractiveness, but partner ratings do not always reflect this.
5. Next Steps

Improve model accuracy by experimenting with different feature selections.
Explore gender-based differences in selectivity more deeply.
Refine hypothesis testing with additional statistical methods.
Prepare final analysis and visualizations for final report submission.
