# Assignment 04 Interpretation Memo

**Student Name:** Rylan Leathers
**Date:** 02/13
**Assignment:** REIT Annual Returns and Predictors (Simple Linear Regression)

---

## 1. Regression Overview

You estimated **three** simple OLS regressions of REIT *annual* returns on different predictors:

| Model | Y Variable | X Variable | Interpretation Focus |
|-------|------------|------------|----------------------|
| 1 | ret (annual) | div12m_me | Dividend yield |
| 2 | ret (annual) | prime_rate | Interest rate sensitivity |
| 3 | ret (annual) | ffo_at_reit | FFO to assets (fundamental performance) |

For each model, summarize the key results in the sections below.

---

## 2. Coefficient Comparison (All Three Regressions)

**Model 1: ret ~ div12m_me**
- Intercept (β₀): 0.1082 (SE: 0.0060, p-value: 0.0000)
- Slope (β₁): -0.0687 (SE: 0.0320, p-value: 0.0346)
- R²: 0.002 | N: 2527

**Model 2: ret ~ prime_rate**
- Intercept (β₀): 0.1998 (SE: 0.0160, p-value: 0.0000)
- Slope (β₁): -0.0194 (SE: 0.0030, p-value: 0.0000)
- R²: 0.016 | N: 2527

**Model 3: ret ~ ffo_at_reit**
- Intercept (β₀): 0.0973 (SE: 0.0092, p-value: 0.0000)
- Slope (β₁): 0.5770 (SE: 0.5670, p-value: 0.3090)
- R²: 0.000 | N: 2518

*Note: Model 3 may have fewer observations if ffo_at_reit has missing values; statsmodels drops those rows.*

---

## 3. Slope Interpretation (Economic Units)

**Dividend Yield (div12m_me):**
- A 1 percentage point increase in dividend yield (12-month dividends / market equity) is associated with a -0.0687 change in annual return.
- Higher dividend yield is associated with lower annual returns, which could reflect that high yields signal lower growth prospects or higher risk.

**Prime Loan Rate (prime_rate):**
- A 1 percentage point increase in the year-end prime rate is associated with a -0.0194 change in annual return.
- The evidence suggests REIT returns are negatively related to interest rates, consistent with higher borrowing costs and lower property valuations.

**FFO to Assets (ffo_at_reit):**
- A 1 unit increase in FFO/Assets (fundamental performance) is associated with a 0.5770 change in annual return.
- The slope is positive but not statistically significant, so there is weak evidence that higher FFO/Assets predicts higher returns.

---

## 4. Statistical Significance

For each slope, at the 5% significance level:
- **div12m_me:** Significant — Dividend yield has a small negative association with annual returns.
- **prime_rate:** Significant — Higher prime rates are associated with lower REIT annual returns.
- **ffo_at_reit:** Not significant — FFO/Assets does not show a reliable relationship with returns in this sample.

**Which predictor has the strongest statistical evidence of a relationship with annual returns?** prime_rate

---

## 5. Model Fit (R-squared)

Compare R² across the three models:
- Prime rate explains the most variation, but R² values are low overall (0.016 at most), suggesting most return variation is driven by other factors.

---

## 6. Omitted Variables

By using only one predictor at a time, we might be omitting:
- Market risk (beta): Higher systematic risk could raise expected returns.
- Size (market equity or lnmcap): Smaller REITs may have higher average returns.
- Momentum (ret1 or ret_6_1): Recent performance can predict short-term returns.

**Potential bias:** If omitted variables are correlated with the predictor, the slope could be biased; for example, if high dividend yield is correlated with higher risk, the negative slope could be overstated.

---

## 7. Summary and Next Steps

**Key Takeaway:**
Prime rate has the strongest statistical relationship with REIT annual returns, with higher rates linked to lower returns. Dividend yield is also negatively related to returns, but the effect is small. FFO/Assets shows no reliable relationship, suggesting fundamentals alone do not explain year-to-year return variation in this simple setup.

**What we would do next:**
- Extend to multiple regression (include two or more predictors)
- Test for heteroskedasticity and other OLS assumption violations
- Examine whether relationships vary by time period or REIT sector

---

## Reproducibility Checklist
- [ ] Script runs end-to-end without errors
- [ ] Regression output saved to `Results/regression_div12m_me.txt`, `regression_prime_rate.txt`, `regression_ffo_at_reit.txt`
- [ ] Scatter plots saved to `Results/scatter_div12m_me.png`, `scatter_prime_rate.png`, `scatter_ffo_at_reit.png`
- [ ] Report accurately reflects regression results
- [ ] All interpretations are in economic units (not just statistical jargon)
