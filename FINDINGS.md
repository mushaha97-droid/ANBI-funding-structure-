# Findings — RAAP! Fundraising Benchmark

This document summarises the inferences from the SQL analysis and maps them to the RAAP! presentation slides.
Every number cited here comes from the SQL queries in `sql/analysis_queries.sql`. Result CSVs are in `findings/results/`.

---

## Executive Summary

A SQL-driven benchmark of **14 NGOs** working in regenerative agriculture, nature restoration, and sustainable land use shows:

1. **Business income (corporate sponsors, foundations) is the dominant channel** — it accounts for **70.3% of all pooled income** and reaches **78.8% of large-NGO budgets** (>€5M).
2. **Funding mix shifts dramatically with size.** Small NGOs anchor on **community engagement (45%)**; large NGOs anchor on **business (79%)**. The path to scale runs through corporate and foundation funding.
3. **6 of 14 NGOs (43%) are highly concentrated** — they get more than half their income from a single source. Diversification is harder than it sounds.
4. **Community engagement and business each anchor 5 of 14 NGOs.** Donation alone anchors only 1 NGO. Pure individual-giving strategies do not work as the primary channel.
5. **Channel coverage is broad but uneven.** Donations, community engagement, and government grants each appear in 11 of 14 NGOs (79% coverage), while business income reaches 10 of 14 (71%) but contributes the largest share when used.

---

## Mapping Findings to RAAP! Slides

### Slide 1 — Research Question

> *"How can RAAP! develop effective and diversified fundraising strategies through storytelling, donor insights, and overcoming key challenges?"*

The SQL evidence reframes "diversified" from an even 5-way split into a more realistic target: **1 anchor source (~50%) plus 2–3 supporting streams (~15–20% each).**
This is what the diversification leaders in the data actually do (see Q13).

---

### Slide 2 — About RAAP!

RAAP!'s focus on regenerative agriculture in Europe places it most naturally alongside Dutch peers such as **Stichting BD Grondbeheer**, **Stichting Voedselbosbouw Nederland**, **Coöperatie Land van Ons**, and **Stichting Herenboeren Nederland**. All four sit in the Small or Mid size band and are reasonable size comparators for RAAP!'s current stage.

---

### Slide 5 — Income Sources (the dataset)

Confirmed by Q1: **64 source records across 14 NGOs**, total pooled income €77.6M, three currencies (EUR, USD, GBP) standardised to euros. Years 2022–2024.

The five categories (donation, business, community engagement, government, capital) have meaningfully different roles. From Q11 (channel coverage):

| Category | NGOs using | Average share when used |
|---|---|---|
| Community engagement | 11 of 14 (79%) | 36.4% |
| Donation | 11 of 14 (79%) | 13.8% |
| Government | 11 of 14 (79%) | 21.8% |
| Business | 10 of 14 (71%) | **47.8%** |
| Capital | 7 of 14 (50%) | 25.7% |

**Read:** business is the highest-impact channel *when activated*, even though slightly fewer NGOs use it. Donations are the most universal channel but contribute the least share.

---

### Slide 7 — Opportunities for RAAP!

Each opportunity stated in the deck is now backed (or qualified) by data:

| RAAP! opportunity | Mapped category | Verdict from data |
|---|---|---|
| **ANBI status** (tax-deductible giving) | Donation | Useful but limited — donation averages only **13.8%** of income when used, and is the dominant source for only **1 of 14 NGOs (Urgenda)**. Pursue ANBI as enabler, not anchor. |
| **Voluntary Carbon Market** (US corporate buyers) | Business | Aligns with the dominant scale channel (78.8% at large NGOs). **No NGO in the benchmark currently has VCM income** — first-mover opportunity. |
| **EU Green Deal** subsidies | Government | Realistic — government appears in 11 of 14 NGOs at an average **21.8%** share. Natuurmonumenten gets **51.6%** from government (incl. Postcode Loterij). |
| **Growing organic / regenerative market** | Business | Aligns with the dominant scale channel. RAAP!'s Marketing & Distribution service is the right vehicle. |

---

### Slide 8 — "Is VC funding feasible for an NGO?"

**Answer: not directly.** Q4 confirms there is no VC line in any of the 14 NGOs. NGOs cannot legally take venture capital because they cannot issue equity. The closest functional substitute in the benchmark is **business** income from foundations and corporate donors — i.e. the "VCs of the non-profit world."

A more realistic path is a **hybrid structure**: a non-profit RAAP! Foundation alongside a for-profit RAAP! BV. The for-profit arm could attract VC; the foundation channels grants and donations. Justdiggit and Commonland use related project-finance structures.

---

### Slide 8 — "Best fundraising channels in the Netherlands"

Ranked by what produces the largest single income lines (Q12):

1. **Charitable Activities / commercial services** — Soil Association alone earned **€21.6M** from this in 2023 (paid certifications, consulting). High-impact but requires a commercial operation.
2. **Foundation grants ("Other non-profit organisations")** — Commonland **€8.4M**, Justdiggit **€3.8M**, Natuurmonumenten **€2.4M**. Stichting DOEN, IKEA Foundation, Goeie Grutten Foundation are common funders.
3. **Corporate donors directly** — Justdiggit **€7.4M**, Trees for All **€6.9M**. Companies fund branded reforestation/regeneration projects.
4. **Postcode Loterij** — Natuurmonumenten **€3.6M**, Commonland **€1.1M**. Selective but transformative once secured. Multi-year track record required.
5. **Individual donations + legacies** — Soil Association **€2.3M**, Justdiggit **€1.9M**, Trees for All **€1.5M**. Long-tail channel that builds with brand awareness.

---

## Detailed Inferences

### Inference 1 — The mix shifts dramatically with size (Q6)

| Size band | Donation | Business | Community | Government | Capital |
|---|---|---|---|---|---|
| Small (<€1M) | 0.6% | 20.8% | **45.3%** | 17.2% | 16.1% |
| Mid (€1M–€5M) | 23.7% | 17.0% | **30.5%** | 19.5% | 9.3% |
| Large (>€5M) | 9.6% | **78.8%** | 1.9% | 9.6% | 0.1% |

Two phase transitions:
- **Small → Mid**: donations grow from <1% to 24% — individual giving activates as brand awareness builds.
- **Mid → Large**: business jumps from 17% to **79%** — corporate/foundation funding is what gets NGOs to scale.

### Inference 2 — Concentration is the norm, not the exception (Q7, Q8)

**6 of 14 NGOs (42.9%)** have HHI > 0.50, meaning more than half their income comes from one category. Highest concentrations:

- Foundation reNature: HHI = 0.99 (community engagement only)
- Stichting Lente Land: HHI = 0.91 (community engagement only)
- Commonland: HHI = 0.79 (business)
- Soil Association: HHI = 0.77 (business)
- Trees for All: HHI = 0.68 (business)
- Justdiggit: HHI = 0.65 (business)

The four large business-anchored NGOs (Commonland, Soil Association, Trees for All, Justdiggit) all chose concentration as a feature — they doubled down on what worked. **This is a viable strategy if the anchor channel is large enough.**

### Inference 3 — Diversification leaders to study (Q13)

Most-balanced NGOs in the benchmark, by lowest HHI:

| NGO | HHI | Active categories | Note |
|---|---|---|---|
| Urgenda | 0.28 | 4 | Donations 39%, government 26%, business 20%, community 15% |
| Cooperatie Land van Ons | 0.31 | 4 | Capital 46%, donations 20%, community 20%, government 14% |
| Regenerative Organic Alliance | 0.31 | 4 | Community 42%, business 30%, government 18%, donation 10% |
| Stichting BD Grondbeheer | 0.33 | **5** | The only NGO using all 5 categories. |
| Stichting Herenboeren Nederland | 0.36 | 4 | Community 50%, government 27%, business 20%, donation 4% |

**Strategic takeaway:** these are the role models for RAAP! to study in depth — they have proven that 4–5-way diversification is achievable, which the heavily-concentrated peers have not.

### Inference 4 — Recommended target mix for RAAP! by stage

Synthesised from Q6 and Q13:

| Stage | Donation | Business | Community | Government | Capital |
|---|---|---|---|---|---|
| Stage 1 — Pilot (<€1M) | 5% | 20% | **45%** | 20% | 10% |
| Stage 2 — Growth (€1M–€5M) | 15% | 35% | **25%** | 20% | 5% |
| Stage 3 — Scaled (>€5M) | 10% | **55%** | 15% | 15% | 5% |

The shift mirrors what successful peer NGOs have done: anchor on community engagement early, gradually pivot the anchor to business funding as the organisation scales.

---

## Limitations

- **Sample size** — 14 NGOs is enough for directional patterns but not statistical significance.
- **Categorisation judgement** — some income lines were borderline (e.g. "non-profit organisations" classified as business; could arguably be donation).
- **Year mismatch** — most data is 2023; reNature is 2022 and ROA is 2024.
- **Currency conversion** — fixed 2023 average rates used (USD→EUR 0.92, GBP→EUR 1.15).
- **Selection bias** — NGOs included were chosen on availability of public reports, biasing toward larger, more established organisations.

---

## Reproducibility

```bash
python python/build_database.py    # Excel → SQLite
python python/run_analysis.py      # Run all 13 queries → CSV results
```

All numerical claims in this document trace directly to a query in `sql/analysis_queries.sql` and a CSV in `findings/results/`.
