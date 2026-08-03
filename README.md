# Uncovering growth levers in Stochastic retail environments - A statistical deep dive

[![Tableau Public](https://img.shields.io/badge/Tableau_Public-Live_Dashboard-E97627?style=for-the-badge&logo=tableau&logoColor=white)](https://public.tableau.com/app/profile/mounika.kalamraju/viz/RetailSpendDiagnosticMarginOptimizationDashboard/Dashboard1)
[![Python 3.10](https://img.shields.io/badge/Python-3.10+-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)

An executive-level diagnostic analytics framework evaluating customer purchasing behaviors, promotional margin cannibalization, and inventory volume demand.

---

## 🌟 Interactive Dashboard Preview

[![Dashboard Overview](docs/assets/dashboard_overview.png)]https://public.tableau.com/app/profile/mounika.kalamraju/viz/RetailSpendDiagnosticMarginOptimizationDashboard/Dashboard1
> **💡 Interactive Feature:** Click the image above to interact with the live dashboard and parameter simulator on Tableau Public.

---

## 1. Summary

The objective of this project was to identify the key drivers of **Purchase Amount (USD)** and evaluate the effectiveness of current store strategies (Subscription, Discounts, and Seasonality). Through rigorous statistical testing, it is observed that the dataset follows a **Uniform Distribution**, meaning traditional customer segments (Age, Gender, Frequency) do not significantly impact the total spend per transaction.

---

## 2. Methodology & Technical Skills
* **Feature Engineering:** Hybrid Encoding.To ensure mathematical accuracy, instead of simple Label Encoding, specific strategies based on feature types are followed:
  * **Binary Mapping:** Converted Yes/No (Promo Codes, Discounts) and Gender to 0/1 to maintain interpretability.
  * **Ordinal Mapping:** Converted **Size** (S, M, L, XL) and **Frequency** to numerical scales to preserve their logical rank.
  * **One-Hot Encoding:** Used for nominal features like **Category** and **Payment Method** to prevent the models from assuming a "false hierarchy" between unrelated items.
* **Statistical Testing:** ANOVA, Independent T-Testing, Chi-Square Test of Independence.
* **Predictive Modeling:** Linear Regression & Random Forest (used for diagnostic importance).
* **Data Visualization:** Seaborn, Matplotlib.




---

## 3. Key Statistical Findings

**Table: Statistical Proof of Random Spending Distribution**

| Analysis Type | Key Metric | Statistical Value | Business Conclusion |
| --- | --- | --- | --- |
| **Predictive Modeling** | Coefficient of Determination ($R^2$) | $R^2 \approx 0$ | No Predictive Power. Demographics are not predictors of spend. |
| **Customer Loyalty** | Frequency ANOVA P-Value | 0.889 | High-frequency shoppers spend no more per visit. |
| **Promo Effectiveness** | Independent T-Test P-Value | 0.26 | Discounts are cannibalizing margins, not upsizing. |
| **Promo Magnitude** | T-Statistic | -1.1 | Negligible difference between group means. |

### Statistical Interpretation

* **$R^2 \approx 0$:** There is no "linear" or "tree-based" relationship between customer traits and spending. The models could not perform better than simply guessing the average purchase price ($\approx \$60$).
* **P-value (0.2):** This is much higher than the standard threshold of **0.05**. It means there is a 20% chance that the difference you see between the two groups is just "luck" or random noise. We conclude there is **no significant difference** in spending between those who used a promo code and those who didn't.
* **T-statistic (-1.1):** The negative sign tells us that the "Promo" group actually spent *slightly less* than the "No Promo" group, but because the number is so small (close to 0), that difference is mathematically negligible.

An **ANOVA p-value of 0.8**, and a **T-test p-value of 0.2** with a **T-statistic of -1.1** all tell the exact same story:
**The spending behavior in this dataset is completely random and independent of customer traits.**

## 4. Operational Insights (Non-Uniform Patterns)

While spending *amounts* are random, **Product Preferences** are not. 

* **Gender-Category Link:** Certain categories (e.g., Accessories vs. Clothing) show non-uniform distributions by gender.
* **Size Distribution:** Size "Medium" and "Large" dominate across categories, regardless of gender or location.

---

## 5. Strategic Recommendations for Store Improvement
Since the above analysis has systematically proven that neither Gender, Size, Frequency, nor Promo Codes drive higher spending, the following "Structural Changes" are recommended:

| Current Finding | Proposed "Structural" Change |
| --- | --- |
| **Promo Code p=0.2** | **Shift to Threshold-Based Incentives:** Since flat discounts (p=0.2) don't increase spend, replace them with **Spend-to-Save** thresholds. |
| **Frequency p=0.8** | **Frequency Conversion:** Since "Weekly" shoppers spend the same as "Annual" shoppers, introduce a points system where points only accumulate on purchases *above* the $60 average. |
| **Size Distribution** | **Inventory Precision:** Optimize stock ratios based on the Observed Size Distribution (e.g., 40% Medium, 30% Large). This reduces capital tied up in slow-moving sizes (S/XL).

---

## 6. Final Conclusion

The store currently operates on a **High-Volume, Low-Segmentation** model. While the brand has "Universal Appeal," there is a significant opportunity to increase **Customer Lifetime Value (CLV)** by introducing structural incentives that reward higher basket sizes and increased visit frequency.

---


