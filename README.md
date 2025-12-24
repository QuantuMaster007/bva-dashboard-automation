# BvA Dashboard Automation

This repo shows how to automate **Budget vs Actual (BvA)** reporting and KPI dashboards using a clean data model + repeatable variance logic.

## What’s included
- ✅ **Synthetic dataset** (24 months) with:
  - `fact_budget` (monthly budgets)
  - `fact_forecast` (M2/M1/M0 forecast snapshots)
  - `fact_actuals` (transaction-level actuals)
  - Dimensions for Cost Centers, Accounts, Projects, Vendors, and Dates
- ✅ Pre-built **monthly BvA output**: `data/processed/fact_bva_monthly.csv`
- ✅ Reference logic for:
  - SQL (`sql/bva_monthly.sql`)
  - Tableau calculated fields (`tableau/tableau_calcs.md`)
  - Excel formulas (`excel/excel_formulas.md`)
- ✅ Simple ETL to regenerate the processed table (`scripts/build_bva.py`)

## Quick start
1. Use the prebuilt dataset:
   - Load `data/processed/fact_bva_monthly.csv` into Tableau / Power BI / Excel.
2. (Optional) Rebuild processed output from raw facts:
   ```bash
   python scripts/build_bva.py --in data/raw --out data/processed
   ```

## KPI ideas (common Finance/Ops views)
- Budget, Actual, Forecast (latest)
- Variance $ and Variance % (Actual vs Budget)
- YTD and QTD rollups
- Top cost centers / accounts driving unfavorable variance
- CapEx vs OpEx split (via `dim_account.is_capex` or `dim_account_rollup`)

## Data dictionary
See `schemas/DATA_DICTIONARY.md`.
