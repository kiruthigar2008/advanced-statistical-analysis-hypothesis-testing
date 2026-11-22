# Advanced Statistical Analysis & Hypothesis Testing

Rigorous inferential statistics on a real business dataset (restaurant bills and tips), using parametric and non-parametric hypothesis tests, ANOVA and Tukey HSD post-hoc analysis.

**Notebook:** [`Advanced_Statistical_Analysis_Hypothesis_Testing.ipynb`](Advanced_Statistical_Analysis_Hypothesis_Testing.ipynb)

## Objective

Test whether differences in restaurant bills and tipping behaviour are statistically significant, and check that the conclusions hold when test assumptions are violated. All tests use a significance level of **α = 0.05**.

## Dataset

The classic `tips` dataset (244 restaurant bills), loaded through `seaborn`.

| Column | Description |
|---|---|
| `total_bill` | Bill amount (USD) |
| `tip` | Tip amount (USD) |
| `sex` | Sex of the bill payer |
| `smoker` | Smoker in the party (Yes/No) |
| `day` | Thur, Fri, Sat, Sun |
| `time` | Lunch or Dinner |
| `size` | Party size |
| `tip_pct` | Derived column: tip as a percentage of the bill |

## Methods

| Step | Techniques |
|---|---|
| Normality testing | Shapiro-Wilk, Kolmogorov-Smirnov, Lilliefors correction, Q-Q plots, log transform |
| Two-sample tests | Welch's t-test, Mann-Whitney U, Levene's test, Cohen's d, rank-biserial correlation, 95% CI, bootstrap CI |
| One-Way ANOVA | F-test, Kruskal-Wallis, Tukey HSD, eta-squared, residual diagnostics |
| Two-Way ANOVA | Day × Sex with interaction (Type II sums of squares), Tukey HSD on cells, interaction plot |
| Robustness | ANOVA repeated on log-transformed bill, Holm multiple-comparison correction |

Every test documents its null and alternative hypotheses in markdown before the code.

## Key Findings

| Question | Result |
|---|---|
| Bill: Dinner vs Lunch | **Significant.** Dinner is about $3.63 higher (p ≈ 0.002). The only result that survives the Holm correction. |
| Bill: Male vs Female | Significant before correction (p ≈ 0.019), small effect (d = 0.30). Not significant after Holm. |
| Tip %: Smoker vs Non-smoker | **No difference** (p ≈ 0.68, negligible effect). |
| Bill across days (One-Way ANOVA) | Significant (p = 0.043), small effect (η² = 0.033). Sunday > Thursday on the log scale (Tukey p = 0.047). |
| Day × Sex (Two-Way ANOVA) | No significant main effects or interaction (interaction p = 0.79). |

Bills are right-skewed, so non-parametric tests were used alongside parametric ones. Both agreed on every two-sample decision.

## How to Run

```bash
git clone https://github.com/kiruthigar2008/advanced-statistical-analysis-hypothesis-testing.git
cd advanced-statistical-analysis-hypothesis-testing

python -m venv venv
venv\Scripts\activate          # Windows
# source venv/bin/activate     # Mac/Linux

pip install -r requirements.txt
jupyter notebook
```

Open the notebook and choose **Kernel → Restart & Run All**. An internet connection is needed on the first run because the dataset is downloaded through seaborn.

## Tech Stack

Python 3, pandas, NumPy, SciPy, statsmodels, seaborn, matplotlib, Jupyter Notebook

## Limitations

- Data come from one waiter at one restaurant, so results may not generalise.
- The design is unbalanced and some day × sex cells are small.
- The data are observational, so findings show association, not causation.

## Author

**Kiruthiga**: B.Tech Artificial Intelligence and Data Science, SKCET, Coimbatore
GitHub: [kiruthigar2008](https://github.com/kiruthigar2008)
