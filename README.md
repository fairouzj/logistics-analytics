# Logistics Analytics and Shipment Delay Modeling

**Python · Apache Spark · Spark ML · Power BI**

An academic logistics analytics project by **Fairouz Juma**, exploring where shipments are delayed and how well shipment characteristics explain those delays. It combines data-quality checks, timestamp processing, operational analysis, regression baselines and an interactive Power BI dashboard.

![Power BI operational overview](assets/dashboard-overview.png)

## Project at a glance

- Original CSV supplied with this project: **100,000 records and 29 columns**.
- Original notebook retained **99,607 records** after removing missing delay/departure/arrival values.
- Analyzed hub and route performance, transport modes, congestion, product weight and daily patterns.
- Compared linear regression, random forest and gradient-boosted trees with Spark ML.
- Built Power BI visuals for shipment volumes, delays and planned versus actual transit times.

## My work

I wrote the PySpark cleaning and analysis notebook, built regression pipelines with categorical encoding and numerical features, compared model results, and created the Power BI dashboard. This repository presents the academic work with portable file paths, cleared notebook output and documentation for reuse.

## Workflow

1. Inspect the schema, missing values and duplicate shipment IDs.
2. Remove records missing key outcome/timestamp fields; fill missing fragility and weight values.
3. Parse timestamps and derive delay categories and actual transit duration.
4. Aggregate delays by hub, route, day, congestion and shipment characteristics.
5. Export cleaned records for visualization.
6. Split the modeling data 80/20, encode categories, assemble features and train three regression models.
7. Compare RMSE and R-squared and communicate findings in Power BI.

## Original model results

These values come from the original notebook's saved output, not a fresh execution of this packaged notebook.

| Model | RMSE (minutes) | R² |
|---|---:|---:|
| Linear Regression | 18.0872 | 0.2517 |
| Random Forest | 18.2812 | 0.2356 |
| Gradient-Boosted Trees | 18.1609 | 0.2456 |

Linear regression performed best among these baselines. The modest R² indicates that much of the delay variation remains unexplained; this is not a production-ready forecasting system.

## Repository contents

```text
notebooks/logistics_analysis.ipynb   Main analysis and modeling workflow
data/shipments_demo.csv             Generated demonstration data (600 rows)
data/README.md                      Dataset instructions and field reference
dashboards/logistics_dashboard.pbix Original Power BI dashboard
dashboards/README.md                Dashboard refresh instructions
assets/                            Dashboard screenshots
reports/results.md                 Recorded results and technical limitations
requirements.txt                   Python dependency ranges
```

## Run locally

Use Python 3.10 or 3.11 and a Java 17 JDK with `JAVA_HOME` configured. The dependency ranges describe the intended environment; a full Spark training rerun has not been performed during packaging.

```bash
python -m venv .venv
# Windows PowerShell:
.venv\Scripts\Activate.ps1
# macOS/Linux instead: source .venv/bin/activate
python -m pip install -r requirements.txt
python -m jupyter lab
```

Open `notebooks/logistics_analysis.ipynb` and run its cells in order. It defaults to the **generated demo CSV**. Demo model scores will differ from the original results.

To analyze the original dataset, place your authorized copy at `data/shipments.csv` and set its absolute path before launching Jupyter:

```powershell
$env:SHIPMENTS_CSV = (Resolve-Path data/shipments.csv).Path
python -m jupyter lab
```

On macOS/Linux: `export SHIPMENTS_CSV="/absolute/path/to/shipments.csv"`.

The raw CSV is not bundled. The PBIX is the original dashboard and can contain embedded project data; it is not a dashboard generated from the demo CSV. No redistribution license for the original dataset was supplied.

## Power BI dashboard

![Power BI trends and transit comparison](assets/dashboard-trends.png)

Open `dashboards/logistics_dashboard.pbix` with Power BI Desktop. To refresh it using your local data, follow [the dashboard notes](dashboards/README.md). The images above were extracted from the original project report.

## Limitations and improvements

- A random split does not test forecasting on future periods; use a chronological holdout for that claim.
- Duplicate IDs are counted but not automatically removed.
- Timestamp parsing can introduce nulls; validate the parsed fields before using new datasets.
- Mean weight imputation occurs before splitting, though weight is not used by the regression models in this notebook.
- Confirm all predictors are available at the intended prediction time.
- Coalescing output into one CSV partition helps desktop reporting but limits distributed scalability.
- Hyperparameter tuning, cross-validation and production deployment are future work.

## Author

Fairouz Juma · [LinkedIn](https://www.linkedin.com/in/fairouzjuma/)

Academic portfolio project. No open-source license has been selected for this repository; third-party data and materials retain their applicable rights.
