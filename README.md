# Governance, Risk, and Return Analysis

An exploratory equity analysis examining whether higher corporate governance scores lead to higher returns or lower risk/volatility.

## Key Takeaway
- **Returns / Profitability:** Higher governance does **not** reliably guarantee higher returns. In the cross-sectional dataset, raw 5-year average ROE has near-zero correlation with governance (`r = -0.0036`, `p = 0.9051`), and winsorized ROE shows only a weak positive correlation (`r = 0.1026`, `p = 0.00075`) without a consistent climb from `Q1` to `Q5`. Similarly, in the 5-year portfolio study (Jul 2021 – Jul 2026), High vs. Low Governance deciles show no statistically significant difference in annualized return (`12.43%` vs. `15.78%`, `p = 0.331`) or Sharpe ratio (`0.29` vs. `0.25`, `p = 0.577`).
- **Risk / Volatility:** Higher governance is more consistently associated with **lower risk and volatility**—both via lower 5-year beta (`r = -0.1789`, `p = 3.42e-09`) in the cross-sectional data and via significantly lower volatility, max drawdown, and downside deviation (`p < 0.0001` across daily and monthly frequencies, surviving size and sector controls) in the comparative portfolio analysis.

## Repository Files

| File | What It Contains | How a Visitor Should Use It |
| :--- | :--- | :--- |
| `cleaned_data.csv` | Tabular dataset (`1,541` rows, `7` columns) containing company identifiers/names, `Market Cap (Billions)`, `Beta 5 Year`, `Governance Pillar Score (FY0)`, `ESG Score (FY0)`, and `ROE 5 YR Avg`. | Use as the input dataset for reproducing the exploratory cleaning, outlier handling, correlation, and quintile steps in the notebook. |
| `analysis_v2.ipynb` | Jupyter notebook performing data cleaning, missingness checks (`1,076` complete cases after dropping `465` rows), `[1%, 99%]` winsorization on `ROE 5 YR Avg` (`[-328.5425, 238.3025]`), correlation analysis, and quintile comparisons. | Open directly in GitHub or run locally with Jupyter/VS Code to inspect the step-by-step data preparation and statistical checks. |
| `governance_risk_analysis.html` | Self-contained HTML report comparing top vs. bottom 10% governance groups (`112` vs. `112` tickers; Jul 2021 – Jul 2026 adjusted-close prices) across daily/monthly risk metrics, Sharpe ratios, correlations, controlled regressions, and a forward out-of-sample test design. | Download and open in any web browser for a clean, visual summary of the comparative risk vs. return/Sharpe findings and caveats. |

## Recommended Reading Order
1. **Start with `governance_risk_analysis.html`** (opened in a browser) for the high-level comparison of risk vs. return/Sharpe and methodological caveats.
2. **Check `cleaned_data.csv` and `analysis_v2.ipynb`** to see the underlying cross-sectional dataset (`n = 1,541` total / `n = 1,076` complete cases) and how extreme `ROE 5 YR Avg` outliers affect correlations and quintiles.

## Caveats & Scope
- **Association, not proof of causation:** Observational/cross-sectional comparisons cannot prove causality or guarantee future performance.
- **Metric differences across files:** `cleaned_data.csv` focuses on accounting profitability (`ROE 5 YR Avg`) and `Beta 5 Year`, whereas `governance_risk_analysis.html` evaluates realized price risk, returns, and Sharpe ratios over Jul 2021 – Jul 2026.
- **Potential confounders:** Firm size (`Market Cap`), sector differences, and time-window effects can influence results.
