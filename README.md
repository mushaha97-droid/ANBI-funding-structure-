# RAAP! Fundraising Strategy — NGO Income Source Benchmark

A data analytics project benchmarking the income mix of **14 NGOs** working in regenerative agriculture, nature restoration, and sustainable land use — to inform fundraising strategy for **RAAP!** (Regenerative Agriculture Action Project).

> **Research question:** *How can RAAP! develop effective and diversified fundraising strategies through storytelling, donor insights, and overcoming key challenges?*

**Stack:** Python · SQL (SQLite) · Power BI

---

## TL;DR

- **Business income (corporate sponsors, foundations) is the dominant channel** — it accounts for **70.3% of all pooled income** and reaches **78.8% of large-NGO budgets** (>€5M).
- **Funding mix shifts dramatically with size.** Small NGOs anchor on **community engagement (45%)**; large NGOs anchor on **business (79%)**. The path to scale runs through corporate and foundation funding.
- **6 of 14 NGOs (43%) are highly concentrated** — they get more than half their income from a single source. Diversification is harder than it sounds.
- **Community engagement and business each anchor 5 of 14 NGOs.** Donations alone anchors only 1 NGO. Pure individual-giving strategies do not work as the primary channel.

Full inferences in [`findings/FINDINGS.md`](findings/FINDINGS.md). Slide deck in [`findings/RAAP_Inferences.pptx`](findings/RAAP_Inferences.pptx).

---

## Project Structure

```
RAAP-Fundraising-Analysis/
├── README.md                          <- you are here
├── data/
│   ├── ngo_income_data.xlsx           <- source dataset (14 NGOs, 64 records)
│   └── ngo_income.db                  <- SQLite DB built by Python
├── sql/
│   └── analysis_queries.sql           <- 13 analytical SQL queries
├── python/
│   ├── build_database.py              <- Excel → SQLite
│   └── run_analysis.py                <- runs all SQL queries, exports CSVs
├── findings/
│   ├── FINDINGS.md                    <- full write-up of inferences
│   ├── RAAP_Inferences.pptx           <- 13-slide presentation deck
│   └── results/                       <- one CSV per query (Q01...Q13)
└── requirements.txt
```

---

## Workflow — How the Analysis Works

The analysis is a clean **SQL + Python pipeline**. No visualization libraries — charts are produced separately in **Power BI** using the same source data.

### 1. Python builds the database

`python/build_database.py` reads the source Excel file and creates a SQLite database with one table (`ngo_income`) containing 64 rows. It also pre-computes three helper columns (`size_band`, `ngo_total_income_eur`, `category_share`) so that the SQL queries stay readable.

### 2. SQL answers the analytical questions

`sql/analysis_queries.sql` contains 13 queries, each tackling a single analytical question:

| # | Question |
|---|---|
| Q1 | Dataset shape and currency mix |
| Q2 | Total income per NGO, ranked |
| Q3 | NGO count and pooled income by size band |
| Q4 | Income by source category (pooled across all NGOs) |
| Q5 | Funding mix per NGO — share by category |
| Q6 | Average funding mix by size band |
| Q7 | Concentration (HHI) per NGO |
| Q8 | How many NGOs are highly concentrated overall |
| Q9 | Dominant source per NGO |
| Q10 | How often is each category the dominant source |
| Q11 | Channel coverage — how widely used is each category |
| Q12 | Top 10 individual income lines across the benchmark |
| Q13 | Diversification leaders (lowest HHI) |

Each query uses idiomatic SQL — `GROUP BY`, conditional aggregation with `CASE WHEN`, window functions (`ROW_NUMBER()`), and a Common Table Expression (CTE) for the HHI calculation.

### 3. Python runs the queries and exports the results

`python/run_analysis.py` parses the `.sql` file into individual queries, executes each against the database, prints clean tables, and saves each result as a CSV in `findings/results/`. This is the link between SQL and Power BI: every CSV can be loaded into Power BI as a data source for visualizations.

### 4. Power BI builds the dashboard

The same Excel file (or any of the result CSVs) loads into Power BI for interactive visualization. The Python pipeline computes the values; Power BI presents them.

### 5. Findings document and slide deck synthesise the inferences

`findings/FINDINGS.md` maps each numerical finding to a strategic implication and ties it back to RAAP!'s slides. `findings/RAAP_Inferences.pptx` is a 13-slide deck with native (editable) PowerPoint charts.

---

## How to Run

```bash
# 1. Install dependencies
pip install -r requirements.txt

# 2. Build the SQLite database from the Excel file
python python/build_database.py

# 3. Run all analysis queries — exports CSVs to findings/results/
python python/run_analysis.py
```

The terminal prints each query's purpose and result. CSVs are saved automatically.

---

## Key Findings

### Funding mix shifts dramatically with NGO size (from Q6)

| Size band | Donation | Business | Community | Government | Capital |
|---|---|---|---|---|---|
| Small (<€1M) | 0.6% | 20.8% | **45.3%** | 17.2% | 16.1% |
| Mid (€1M–€5M) | 23.7% | 17.0% | **30.5%** | 19.5% | 9.3% |
| Large (>€5M) | 9.6% | **78.8%** | 1.9% | 9.6% | 0.1% |

Two phase transitions emerge:
- **Small → Mid:** donations grow from <1% to 24% — individual giving activates.
- **Mid → Large:** business jumps from 17% to **79%** — corporate/foundation funding is what gets NGOs to scale.

### Concentration is the norm (from Q7, Q8)

**6 of 14 NGOs (42.9%)** have HHI > 0.50. Highest-concentration peers (all single-anchored):
Foundation reNature (0.99), Stichting Lente Land (0.91), Commonland (0.79), Soil Association (0.77), Trees for All (0.68), Justdiggit (0.65).

### Diversification leaders worth studying (from Q13)

Most-balanced NGOs — these are the role models for RAAP!:

| NGO | HHI | Active categories |
|---|---|---|
| Urgenda | 0.28 | 4 |
| Coöperatie Land van Ons | 0.31 | 4 |
| Regenerative Organic Alliance | 0.31 | 4 |
| Stichting BD Grondbeheer | 0.33 | **5 (the only NGO using all)** |
| Stichting Herenboeren Nederland | 0.36 | 4 |

### Recommended target funding mix for RAAP! by stage

| Stage | Donation | Business | Community | Government | Capital |
|---|---|---|---|---|---|
| Stage 1 — Pilot (<€1M) | 5% | 20% | **45%** | 20% | 10% |
| Stage 2 — Growth (€1M–€5M) | 15% | 35% | **25%** | 20% | 5% |
| Stage 3 — Scaled (>€5M) | 10% | **55%** | 15% | 15% | 5% |

---

## Mapping to RAAP!'s Stated Opportunities

| RAAP! opportunity | Mapped category | Verdict from data |
|---|---|---|
| **ANBI status** | Donation | Useful enabler — but donation averages only 13.8% when used and is the dominant source for only 1 of 14 NGOs. |
| **Voluntary Carbon Market** | Business | Aligns with the dominant scale channel (78.8% at large NGOs). **Zero peers have this yet — first-mover opportunity.** |
| **EU Green Deal subsidies** | Government | Realistic — appears in 11 of 14 NGOs at avg 21.8% share. |
| **Growing organic / regenerative market** | Business | Aligns with the dominant scale channel. RAAP!'s Marketing & Distribution service is the right vehicle. |

---

## Limitations

- **Sample size** — 14 NGOs is enough for directional patterns but not statistical significance.
- **Categorisation judgement** — some income lines were borderline (e.g. "non-profit organisations" classified as business; could arguably be donation).
- **Year mismatch** — most data is 2023; reNature is 2022 and ROA is 2024.
- **Currency conversion** — fixed 2023 average rates (USD→EUR 0.92, GBP→EUR 1.15).
- **Selection bias** — NGOs selected on availability of public reports, biasing toward larger, more established organisations.

---

## Author

Data Analytics Internship Project · 2025

Public annual reports and Standaard Publicatieplicht filings sourced from Dutch ANBI registers and NGO websites.
