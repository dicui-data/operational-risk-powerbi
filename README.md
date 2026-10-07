# operational-risk-powerbi

An executive risk dashboard built around one question: **what needs attention this month?**
Five risk programs, six source systems, one reporting-month selector.

![Executive summary](images/01_executive_summary.png)

## What it does

- **Exceptions first.** The summary page shows only what breached a limit or is overdue, ranked by priority. Everything else is one click away.
- **One model, every program.** Loss events, issues, KRIs, RCSA results, and control tests share one star schema, so a single slicer moves them all together.
- **Checks built in.** Every refresh reconciles to source control totals and runs eight data quality rules. Problems are flagged, not quietly fixed.
- **Signals lined up.** A control rated effective in the self-assessment but failing independent testing is flagged automatically.

## Pages

| Page | Shows |
|---|---|
| Executive summary | Auto-updating summary line, KPI cards vs prior month, prioritized attention list |
| Risk and control profile | Residual risk heat map that filters the risk register; self-assessment vs test results |
| Events and issues | Loss trend, loss by Basel event type, issue aging |
| Department profile | Drill-through: KRIs against thresholds, risks, open issues, recent events |
| Data quality | Source reconciliation and data quality rule results |

![Risk and control profile](images/02_risk_control.png)

## How it's built

- **Power Query** — six sources read through two reusable functions; folder path held in a parameter; name mismatches across systems resolved through a mapping table
- **Data model** — star schema, six fact tables, single-direction relationships, role-playing dates
- **DAX** — month-end snapshot measures, as-of lookups for the latest assessment, thresholds stored as data rather than hard-coded

## Data

Synthetic data for a fictional bank, September 2025 to August 2026, with a few data quality problems planted on purpose. Event types follow Basel Level 1. Ratings and thresholds are illustrative.

## Run it

Open `powerbi/Operational_Risk.pbix` in Power BI Desktop, then go to **Transform data → Manage parameters** and point `SourceFolder` to your local `data/` folder.

## Repository

- `data/` — the six source files
- `powerbi/` — the report
- `images/` — page screenshots

**Tools:** Power BI (Power Query, DAX), Excel
