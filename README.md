# obesity-dysglycemia-risk-prediction-prevention
Nationally representative NHANES 2017–2018 analysis of obesity-linked dysglycemia in U.S. women aged 20–44. Includes survey-weighted models, regression standardization (absolute risks, risk differences, PAF), pregnancy-history heterogeneity, sensitivity analyses, and reproducible tables/figures.

# Obesity–Dysglycemia Risk, Prediction, and Prevention (NHANES 2017–2018)

Nationally representative analysis of obesity-associated dysglycemia (prediabetes/diabetes) among **non-pregnant U.S. women aged 20–44 years** using NHANES 2017–2018. This repository provides the **source NHANES XPT files used for analysis** and the **fully rendered, publication-ready outputs** (tables, figures, and metadata inventories).

---

## Study summary

- **Design:** Cross-sectional analysis of NHANES 2017–2018 (complex survey design)
- **Population:** Non-pregnant women, age 20–44 years
- **Exposure:** Obesity (BMI ≥ 30 kg/m²)
- **Outcome:** Dysglycemia (guideline-consistent glycemic criteria and/or diabetes classification as defined in the manuscript)
- **Core outputs:** Survey-weighted prevalence; adjusted association models; standardized absolute risks; risk differences; risk ratios; population attributable fraction (PAF); heterogeneity by pregnancy history; sensitivity analyses and missingness profile

---

## Repository structure (matches this project)

.
├── data/
│ └── raw_xpt/
│ ├── ALQ_J.xpt
│ ├── BMX_J.xpt
│ ├── BPX_J.xpt
│ ├── DEMO_J.xpt
│ ├── DIQ_J.xpt
│ ├── DR1TOT_J.xpt
│ ├── DR2TOT_J.xpt
│ ├── FASTQX_J.xpt
│ ├── GHB_J.xpt
│ ├── GLU_J.xpt
│ ├── INS_J.xpt
│ ├── PAQ_J.xpt
│ ├── RHQ_J.xpt
│ ├── RXQ_RX_J.xpt
│ └── SMQ_J.xpt
└── results/
├── figures/
│ ├── Fig01_.png
│ ├── Fig02_.png
│ ├── ...
│ └── Fig10_HbA1c_vs_BMI.png
├── tables/
│ ├── Table01_.html
│ ├── Table02_.html
│ ├── ...
│ └── Table10_*.html
└── metadata/
├── xpt_inventory.csv
├── xpt_inventory.txt
├── xpt_varlist_ALQ_J.csv
├── xpt_varlist_BMX_J.csv
├── ...
└── xpt_varlist_SMQ_J.csv

yaml
Copy code

---

## Quick start (view the final outputs)

### Figures
All figures are in:
- `results/figures/`

Recommended “main-text” figures (typical AJPM-friendly set):
- **Fig05** — Model effect estimates (forest-style summary)
- **Fig06** — Standardized risks by obesity status (absolute-risk translation)
- **Fig07** — Policy-facing estimands (RD/RR/PAF summary)
- **Fig08** — Heterogeneity by pregnancy history (stratified estimates)

Additional figures (exploratory/diagnostic):
- **Fig01** BMI distribution by dysglycemia status
- **Fig02 / Fig10** HbA1c patterns vs obesity/BMI
- **Fig04** Correlation heatmap
- **Fig09** Missingness profile

### Tables
All rendered tables are in:
- `results/tables/` (HTML files; open in a browser)

Typical interpretation map:
- **Table01** — Baseline characteristics by obesity status
- **Table02** — Dysglycemia prevalence by obesity status (survey-weighted)
- **Table04** — Primary regression models (ORs)
- **Table05** — Standardized risks, RD, RR, and PAF (prevention-relevant metrics)
- **Table06** — Stratified models by pregnancy history
- **Table07** — Missing data profile
- **Tables 08–10** — Sensitivity analyses (HbA1c-only; continuous BMI; unmeasured confounding sensitivity)

---

## Data provenance and documentation

### NHANES data files used
The analysis uses NHANES 2017–2018 public-use SAS transport files (`.xpt`) stored in:
- `data/raw_xpt/`

### Variable inventories and codebook helpers
To support transparent variable mapping and reproducibility, this repository includes:
- `results/metadata/xpt_inventory.csv` and `xpt_inventory.txt` (file inventory)
- `results/metadata/xpt_varlist_*.csv` (variable lists for each XPT file used)

These metadata files provide a rapid “what’s in each file” index for auditing and manuscript supplement construction.

---

## Reproducibility (recommended local workflow)

This repository contains the **exact input XPT files** and the **final rendered outputs** (tables/figures).  
If you are reproducing the analysis from scratch, the standard approach in R is:

1) Read `.xpt` files from `data/raw_xpt/` (e.g., with `haven::read_xpt()`).
2) Merge NHANES components by respondent ID (SEQN).
3) Define analytic cohort (women 20–44, non-pregnant, complete eligibility).
4) Construct exposure/outcome variables (BMI, dysglycemia definition).
5) Fit survey-weighted models and compute standardized risks / RD / RR / PAF.
6) Render tables to HTML and figures to PNG into `results/tables/` and `results/figures/`.

> If you maintain analysis scripts elsewhere (or plan to add them), the best practice is to include a `code/` directory with a single entry-point script (e.g., `run_all.R`) that regenerates `results/` end-to-end.

---

## Ethics and data use
NHANES is a publicly available, de-identified dataset. Original data collection was conducted under National Center for Health Statistics (NCHS) protocols with participant consent. This repository contains NHANES public-use files and derived outputs; users should follow CDC/NCHS terms for NHANES data use and citation.

---

## Authors and contributions (CRediT)

- **Sunday A. Adetunji, MD** — Conceptualization; Methodology; Formal analysis; Software; Data curation; Visualization; Writing – Original Draft; Writing – Review & Editing; Project administration; Supervision.  
- **Feyisayo Olufemi, MPH** — Validation (independent review of scripts/outputs); Writing – Review & Editing (policy framing, interpretation, manuscript revisions).  
- **Olusola P. Ekundayo, BSN, RN** — Conceptualization (study design input); Writing – Review & Editing (critical manuscript review).

**Corresponding author:** Sunday A. Adetunji — adetunjs@oregonstate.edu

---

## Suggested citation
If you use or adapt materials from this repository, please cite the associated manuscript (and/or include a repository citation via `CITATION.cff` if present in your project).

---

## License
Add a `LICENSE` file to clearly define reuse terms for code and derived outputs (e.g., MIT or Apache-2.0). NHANES data are public-use; users should still cite NHANES/NCHS appropriately.

---
