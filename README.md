# RAAP! Fundraising Strategy — NGO Income Source Benchmark

A data analytics project benchmarking the income mix of **14 NGOs** working in regenerative agriculture, nature restoration, and sustainable land use — used to inform fundraising strategy for **RAAP!** (Regenerative Agriculture Action Project).

> **Research question:** How can RAAP! develop effective and diversified fundraising strategies through storytelling, donor insights, and overcoming key challenges?

---

## TL;DR

- **The path to scale runs through corporate and foundation funding.** NGOs above €5M in income get ~70% of their money from the *business* category (corporate sponsors, foundation grants).
- **Smaller NGOs (<€1M) anchor on community engagement** — member fees, lease income, program services. RAAP!'s likely starting band.
- **Most peer NGOs are highly concentrated** — over half rely on a single source for >50% of income. "Diversification" in this space means 1 anchor + 2-3 secondary streams, not an even split.
- **VC funding is not directly viable** — zero of 14 benchmark NGOs report VC income. A hybrid foundation + for-profit entity is the realistic adjacent path.

---

## Headline Visualization

![Funding mix per NGO](visualizations/02_funding_mix_per_ngo.png)

Each NGO's income broken down by source category, sorted by total size. The pattern jumps out: **business income** (deep teal) dominates the largest organizations; **community engagement** (green) anchors the smallest.

---

## What's in this Repo

```
RAAP-Fundraising-Analysis/
├── README.md                       <- you are here
├── analysis.ipynb                  <- main analysis notebook
├── data/
│   └── ngo_income_data.xlsx        <- cleaned dataset (4 sheets)
├── visualizations/                 <- 7 PNG charts produced by the notebook
├── build_dataset.py                <- script that builds the Excel from raw data
├── build_notebook.py               <- script that builds the notebook
└── requirements.txt
```

### The Dataset (`data/ngo_income_data.xlsx`)

Four sheets:
1. **README** — purpose, exchange rates, sources
2. **Raw Data** — 64 rows, one per (NGO, income source item). Long format.
3. **Summary by NGO** — pivoted view with totals per category
4. **Categories** — definitions of the 5 source categories

Categories used: `donation` · `business` · `community_engagement` · `government` · `capital`

All amounts converted to EUR (USD→EUR: 0.92, GBP→EUR: 1.15, 2023 averages). Local-currency originals preserved.

### The Notebook (`analysis.ipynb`)

Walks through the analysis end-to-end — loading the data, building each chart, and connecting findings back to the strategic opportunities RAAP! identified (ANBI status, Voluntary Carbon Market, EU Green Deal, growing organic market). Ten sections:

1. Setup and data loading
2. Funding landscape — total income per NGO
3. Funding mix per NGO — the headline chart
4. Mix shift by NGO size band
5. Diversification analysis (Herfindahl-Hirschman Index)
6. Most common dominant source
7. Source coverage heatmap
8. **Strategic implications for RAAP!** — recommended target mix by stage
9. Limitations
10. Next steps

---

## Methodology

1. **Data collection** — public annual reports and Standaard Publicatieplicht filings from 14 NGOs (2022-2024). Sources include Justdiggit, Trees for All, Commonland, Soil Association Group, Urgenda, Stichting BD Grondbeheer, Stichting Herenboeren Nederland, Stichting Voedselbosbouw Nederland, Coöperatie Land van Ons, Foundation reNature, Stichting Lente Land, Standaard Publicatieplicht Fondsen, Natuurmonumenten, Regenerative Organic Alliance.
2. **Cleaning** — every income line was extracted and tagged with one of five source categories. Currency converted to EUR.
3. **Analysis** — pandas + matplotlib + seaborn. NGOs banded by size (Small <€1M, Mid €1M-€5M, Large >€5M). Concentration measured via HHI.
4. **Strategy translation** — findings mapped to RAAP!'s stated opportunities and translated into a staged target funding mix.

---

## How to Run

```bash
# clone
git clone https://github.com/<your-username>/RAAP-Fundraising-Analysis.git
cd RAAP-Fundraising-Analysis

# install dependencies
pip install -r requirements.txt

# regenerate the cleaned dataset
python build_dataset.py

# open the notebook
jupyter notebook analysis.ipynb
```

---

## Limitations

- **Sample size** — 14 NGOs is enough for directional patterns, not statistical significance.
- **Categorization judgment** — some income lines are borderline (e.g. "non-profit organizations" classified as business — could be donation).
- **Year mismatch** — most data is 2023, but reNature is 2022 and ROA is 2024.
- **Selection bias** — NGOs were selected on availability of public reports, biasing toward larger, more established organizations.

---

## Author

Data Analytics Internship Project · 2025

If you spot something off in the categorization or want to extend the benchmark, open an issue or pull request.
