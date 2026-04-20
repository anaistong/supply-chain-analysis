# Reducing Cost-to-Serve and Operational Inefficiencies in a Fashion & Beauty Supply Chain

A consulting-style Operational Analytics case study on supplier performance, route efficiency, product quality, and cost-to-serve optimisation.

---

## 1. Business Problem

A fashion & beauty brand sells skincare, haircare, and cosmetics across retail and DTC. Growth has outpaced operational maturity: 5 suppliers, 3 carriers, 4 transport modes, 3 routes — and no systematic view of which combinations deliver the best cost, quality, and service outcomes.

**Question:** *How can the client reduce cost-to-serve, improve supplier reliability, and minimise quality incidents — without sacrificing delivery lead times or availability?*

**Stakeholders:** COO, Head of Procurement, Head of Logistics, Head of Quality, CFO.

---

## 2. Data

**Source:** [Supply Chain Analysis – Kaggle](https://www.kaggle.com/datasets/harshsingh2209/supply-chain-analysis)

100 SKU-level records × 24 columns covering product & commercial, inventory, supplier & manufacturing, logistics, and quality data.

**Caveat:** the dataset is small (n = 100). Insights are directional; the framework and KPIs are designed to scale to a full operational dataset.

---

## 3. Methodology

Four stages, one per notebook:

1. **Data cleaning & EDA** — standardise, engineer operational metrics, first-pass insights.
2. **KPI framework & bottleneck diagnosis** — define KPIs, identify where cost / quality is concentrated.
3. **Predictive modelling & segmentation** — Random Forest / XGBoost defect-risk model + K-Means supplier segmentation.
4. **Recommendations & roadmap** — 5 actions with quantified impact, dashboard spec, phased plan.

---

## 4. KPI Framework

| KPI | Formula | What it tells you |
|---|---|---|
| Cost-to-Serve per unit | `manufacturing_cost + shipping_cost` | Profitability lever per SKU |
| Gross Margin % | `(revenue − cost_to_serve) / revenue` | Commercial health |
| Supplier Reliability | blend of pass rate, lead-time stability, defect rate | Procurement ranking |
| Late-Delivery Rate | `shipping_time > supplier_lead_time` | Service-level proxy |
| Quality Pass Rate | `share of Pass` | Brand / rework-cost proxy |
| Inventory Cover | `stock_levels / avg_daily_sales` | Working-capital efficiency |
| Cost per Route × Mode | `mean(shipping_cost)` | Logistics signal |

---

## 5. Headline Findings

- **Cost-to-serve is concentrated** in a few suppliers, product types, and SKUs — not uniform.
- **Two suppliers** cluster as Underperformers: high cost *and* low reliability.
- **Some route × transport mode combinations** are both expensive and slow — mode-switch candidates.
- **Defect risk is predictable** — the model flags High / Medium / Low risk SKUs with meaningful lift, enabling risk-based QA.

---

## 6. Recommendations

| # | Recommendation | Owner | Horizon |
|---|---|---|---|
| R1 | Shift volume from Underperformer suppliers to Top performers | Procurement | 0–3m |
| R2 | Switch expensive road shipments to rail / sea where SLA allows | Logistics | 3–6m |
| R3 | Risk-based QA driven by the defect-risk model | Quality | 3–6m |
| R4 | Dynamic safety stock for high-variance SKUs | Operations | 3–6m |
| R5 | Weekly Power BI dashboard on the KPI framework | Analytics | 0–3m |

**Aggregate target:** ~8–12% reduction in cost-to-serve and 20%+ reduction in flagged-SKU defect incidents within 6 months.

---

## 7. Project Structure

```
Supply Chain Analytics Project/
├── README.md
├── requirements.txt
├── data/
│   ├── raw/              ← place supply_chain_data.csv here
│   └── processed/
├── notebooks/
│   ├── 01_data_cleaning_eda.ipynb
│   ├── 02_kpi_bottleneck_analysis.ipynb
│   ├── 03_predictive_modeling_segmentation.ipynb
│   └── 04_recommendations_roadmap.ipynb
└── reports/
    ├── executive_summary.md
    └── dashboard_mockup.md
```

---

## 8. How to Run

```bash
pip install -r requirements.txt
# Download supply_chain_data.csv from the Kaggle link above → data/raw/
jupyter lab notebooks/
```

Run the notebooks in order (01 → 04).

---

## 9. Tech Stack

Python (pandas, NumPy, matplotlib, seaborn, scikit-learn, XGBoost) · Jupyter · Power BI (dashboard spec only).

---

## 10. Limitations

- Small sample (n = 100) — the ML model is a proof of concept, not a production model.
- Snapshot data only — no time series, so trend / seasonality analysis is out of scope.
- Impact figures are directional; validate against client P&L before committing to them.

---

*Author: Anais Tong*
