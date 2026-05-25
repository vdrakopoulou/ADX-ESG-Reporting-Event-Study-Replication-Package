div align="center">

# Mandate-Backed ESG Reporting and Limited Price Discovery

## Evidence from Sustainability Report Releases on the Abu Dhabi Securities Exchange

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.20371869.svg)](https://doi.org/10.5281/zenodo.20371869)
[![Article](https://img.shields.io/badge/article-Research%20Paper-2f6f9f.svg)](#journal-submission-metadata)
[![Replication](https://img.shields.io/badge/replication-package%20available-1f883d.svg)](#quick-start)
[![Python](https://img.shields.io/badge/python-3.10%2B-3776ab.svg)](#computational-environment)
[![ORCID](https://img.shields.io/badge/ORCID-0000--0002--1670--8033-a6ce39.svg)](https://orcid.org/0000-0002-1670-8033)

**A reproducible event-study package for examining whether ESG report publication on ADX creates price discovery, trading attention, investor-type rebalancing, or credibility-based market response.**

</div>

---

## Project at a Glance

| Field | Details |
|---|---|
| Paper title | *Mandate-Backed ESG Reporting and Limited Price Discovery: Evidence from Sustainability Report Releases on the Abu Dhabi Securities Exchange* |
| Target journal | *International Journal of Islamic and Middle Eastern Finance and Management* |
| Article classification | Research Paper |
| Author | Veliota Drakopoulou |
| Affiliations | a Higher Colleges of Technology, United Arab Emirates; b Embry-Riddle Aeronautical University, United States |
| ORCID | 0000-0002-1670-8033 |
| Correspondence | vdrakopoulou@gmail.com |
| GitHub repository | [insert GitHub URL] |
| Zenodo DOI | https://doi.org/10.5281/zenodo.20371869 |
| Data and code availability | Replication materials are available through the GitHub repository and Zenodo DOI listed above. |

> [!IMPORTANT]
> This repository supports a manuscript submission. The journal name above identifies the target outlet and should not be read as an acceptance or publication claim.

---

## Core Contribution

This project separates **ESG disclosure publication** from **ESG disclosure usefulness**.

The empirical question is intentionally narrow: when an ADX-listed firm releases an ESG, sustainability, integrated, or ESG-related annual report, does the market respond around the publication date? The answer is nuanced. ESG report releases do not generate statistically significant abnormal returns or abnormal trading activity, but investor-type order imbalance shows wider-window rebalancing. The evidence also suggests that trading responses are more visible when reports contain credible, specific, and verifiable ESG content.

In practical terms, the repository supports the following contribution:

> Mandate-backed ESG reporting may increase disclosure availability, but publication alone does not necessarily create price discovery. Market usefulness depends more on disclosure credibility than on disclosure existence.

---

## Research Design

The analysis treats ESG report releases as firm-specific disclosure events and applies a standard event-study structure. Each announcement date is aligned to the first eligible trading day on or after the report release date. The resulting event day is used to construct event windows and estimate returns, trading activity, and investor-type order imbalance.

### Main event windows

```text
[-1,+1]    immediate disclosure response
[-3,+3]    short delayed processing
[-5,+5]    wider short-run adjustment
[-10,+10]  gradual attention and investor rebalancing
```

### Main outcomes

| Outcome | Interpretation |
|---|---|
| Market-adjusted CAR | Price discovery around ESG report publication |
| Market-model CAR | Return-model robustness |
| Mean-adjusted CAR | Return-model robustness |
| Abnormal log value traded | Trading attention and market salience |
| Company order imbalance | Corporate/legal-entity account net buying or selling |
| Individual order imbalance | Natural-person account net buying or selling |
| Content credibility | Disclosure-quality proxy based on quantification, assurance/standards, targets/baselines, and boilerplate penalty |

---

## Empirical Snapshot

### Sample construction

| Sample item | N |
|---|---:|
| Clean ESG report events after date validation and duplicate screening | 103 |
| Events without matched trading day | 36 |
| Final aligned ESG report-release events | 67 |
| Firm-event-day observations | 1,388 |
| Unique tickers in aligned sample | 66 |
| Report-year coverage | 2021-2025 |
| Matched content-credibility events | 51 |

### Main result in one line

> No abnormal-return or abnormal-volume response; wider-window investor-type rebalancing; suggestive credibility-based trading response.

### Main abnormal-return evidence

| Outcome | Window | N | Mean | p-value |
|---|---:|---:|---:|---:|
| Market-adjusted CAR | [-1,+1] | 67 | 0.0029 | .634 |
| Market-adjusted CAR | [-3,+3] | 67 | 0.0027 | .753 |
| Market-adjusted CAR | [-5,+5] | 67 | -0.0033 | .802 |
| Market-adjusted CAR | [-10,+10] | 67 | -0.0004 | .976 |

### Main investor-type evidence

| Outcome | Window | N | Mean | p-value |
|---|---:|---:|---:|---:|
| Company OI | [-10,+10] | 67 | -0.1608 | .017 |
| Individual OI | [-10,+10] | 67 | 0.1608 | .017 |

### Content-credibility heterogeneity

| Outcome | Window | N | High credibility | Low credibility | Difference | p-value |
|---|---:|---:|---:|---:|---:|---:|
| Abnormal log value traded | [-10,+10] | 51 | 1.0906 | -1.4033 | 2.4939 | .057 |
| Company OI | [-10,+10] | 51 | -0.2502 | 0.0008 | -0.2510 | .099 |
| Individual OI | [-10,+10] | 51 | 0.2502 | -0.0008 | 0.2510 | .099 |

> [!NOTE]
> The content-credibility results are supplementary heterogeneity evidence. They should be described as suggestive because they cover 51 of the 67 event-study events and the strongest effects appear in wider windows.

---

## Repository Structure

```text
ADX_ESG_Disclosure_Event_Study_Replication_V2_1/
|
|-- README.md
|-- CHANGELOG.md
|-- RUN_REPLICATION.py
|-- RUN_CONTENT_HETEROGENEITY.py
|-- requirements.txt
|-- OUTPUT_INDEX.csv
|
|-- code/
|   |-- paper1_publishable_event_tests_v2.py
|   |-- paper1_content_credibility_heterogeneity.py
|
|-- data/
|   |-- event_calendar/
|   |   |-- event_calendar_verified_corrected.csv
|   |   |-- event_calendar_verified_corrected.xlsx
|   |   |-- Paper1_All_Companies_Combined_Event_Audit.xlsx
|   |   |-- confounding_events.csv
|   |
|   |-- raw/
|   |   |-- 05_panel_dataset.csv
|   |   |-- announcements_export.csv
|   |   |-- reports_list_with_dates_filled.xlsx
|   |
|   |-- text_source/
|       |-- code_python.zip
|
|-- outputs/
|   |-- main_event_study/
|   |   |-- data/
|   |   |-- diagnostics/
|   |   |-- figures/
|   |   |-- logs/
|   |   |-- tables/
|   |
|   |-- content_credibility/
|       |-- data/
|       |-- figures/
|       |-- tables/
|
|-- selected_figures/
|-- manuscript/
|-- documentation/
|-- logs/
```

---

## Quick Start

Clone the repository after the GitHub URL is finalized:

```bash
git clone [insert GitHub URL]
cd ADX_ESG_Disclosure_Event_Study_Replication_V2_1
```

Create and activate a virtual environment:

```bash
python -m venv .venv
source .venv/bin/activate
```

Install dependencies:

```bash
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
```

Run the main event-study replication:

```bash
python RUN_REPLICATION.py
```

Run the content-credibility heterogeneity extension:

```bash
python RUN_CONTENT_HETEROGENEITY.py
```

Reproduced outputs are written to:

```text
outputs_reproduced/main_event_study/
outputs_reproduced/content_credibility/
```

Precomputed corrected outputs are included in:

```text
outputs/main_event_study/
outputs/content_credibility/
```

---

## Computational Environment

The package is written in Python and uses standard scientific-computing libraries.

```text
pandas>=2.0
numpy>=1.24
scipy>=1.10
statsmodels>=0.14
matplotlib>=3.7
openpyxl>=3.1
```

The scripts were organized so that the main event-study pipeline and the content-credibility extension can be run independently.

---

## What Each Script Does

| Script | Purpose | Main outputs |
|---|---|---|
| `RUN_REPLICATION.py` | Wrapper for the main event-study workflow | Event panel, CAR tests, abnormal-volume tests, investor-flow tests, placebo tests, event-time regressions |
| `RUN_CONTENT_HETEROGENEITY.py` | Wrapper for content-credibility heterogeneity tests | High-low credibility tests, credibility regressions, content-credibility figures |
| `code/paper1_publishable_event_tests_v2.py` | Core event-study engine | Main tables, event panels, diagnostics, figures |
| `code/paper1_content_credibility_heterogeneity.py` | Content-credibility analysis | Merged credibility dataset and heterogeneity tests |

---

## Key Output Files

### Main event-study outputs

| File | Use |
|---|---|
| `outputs/main_event_study/tables/sample_construction.csv` | Sample construction and final event counts |
| `outputs/main_event_study/tables/event_window_tests_all_robustness.csv` | CAR, abnormal-volume, and investor-flow event-window tests |
| `outputs/main_event_study/tables/placebo_empirical_pvalues.csv` | Random-date placebo p-values |
| `outputs/main_event_study/tables/event_time_regressions.csv` | Event-time regression evidence |
| `outputs/main_event_study/data/event_panel_clean.csv` | Firm-event-day panel |
| `outputs/main_event_study/data/event_window_summary.csv` | Event-level summary file |
| `outputs/main_event_study/diagnostics/event_date_audit.csv` | Event-date audit and alignment diagnostics |

### Content-credibility outputs

| File | Use |
|---|---|
| `outputs/content_credibility/data/report_content_credibility_scores.csv` | Report-level content-credibility scores |
| `outputs/content_credibility/data/event_content_credibility_merged.csv` | Event outcomes merged with content scores |
| `outputs/content_credibility/tables/table_content_credibility_high_low.csv` | High-low credibility tests |
| `outputs/content_credibility/tables/table_content_credibility_regressions.csv` | Regression-based heterogeneity checks |
| `outputs/content_credibility/figures/figure_content_credibility_ioi_pm10.png` | Content-credibility figure for Individual OI over [-10,+10] |

---

## Selected Figures

The repository includes manuscript-ready figures in `selected_figures/`.

```text
selected_figures/Figure1_mean_market_adjusted_abnormal_returns.png
selected_figures/Figure2_company_order_imbalance.png
selected_figures/Figure3_individual_order_imbalance.png
selected_figures/Figure4_content_credibility_individual_oi_pm10.png
```

You can preview the main figures directly in GitHub once the repository is published:

![Mean market-adjusted abnormal returns](selected_figures/Figure1_mean_market_adjusted_abnormal_returns.png)

![Company order imbalance](selected_figures/Figure2_company_order_imbalance.png)

![Individual order imbalance](selected_figures/Figure3_individual_order_imbalance.png)

---

## Interpretation Guardrails

> [!CAUTION]
> This is **not** a positive-CAR paper.

The strongest defensible interpretation is:

1. ESG report releases on ADX do not generate statistically significant abnormal returns.
2. Abnormal trading activity is also insignificant.
3. Investor-type order imbalance shows wider-window rebalancing.
4. Content credibility appears to strengthen the investor-flow pattern, but the evidence is supplementary and should be described cautiously.
5. Wider-window findings should be interpreted as gradual investor adjustment rather than clean announcement-day causality.

Recommended manuscript language:

> Using 67 aligned ESG report-release events on ADX, the results show no evidence that mandate-backed ESG report publication generates significant short-window abnormal returns or abnormal trading volume. This indicates limited immediate price discovery. However, investor-type order imbalance shows wider-window rebalancing, with Individual accounts becoming net buyers and Company accounts becoming net sellers over the [-10,+10] window. Content-credibility heterogeneity tests further suggest that this rebalancing is stronger for reports containing more quantified, assured, standards-aligned, and target-specific ESG disclosure. The evidence suggests that report publication alone is not price-moving news; disclosure credibility is the more relevant investor signal.

---

## Data Access and Responsible Use

This package contains a corrected ESG report event calendar, ADX trading-panel inputs used by the replication workflow, event-study outputs, and content-credibility outputs.

The ESG report event calendar and report-source metadata are derived from public company reports, exchange disclosure records, and manually curated release information. The daily trading and investor-type panel should be used according to the author's data-provider, exchange-access, and institutional permissions.

The file `data/event_calendar/confounding_events.csv` is included as a template. It should be populated with earnings, dividends, board changes, capital actions, suspensions, M&A announcements, major contracts, and other firm-specific announcements around ESG report dates before final journal submission.

---

## Reproducibility Checklist

| Item | Status |
|---|---|
| Corrected event calendar included | Yes |
| Main event-study code included | Yes |
| Content-credibility extension included | Yes |
| Requirements file included | Yes |
| Precomputed corrected outputs included | Yes |
| Event-date diagnostics included | Yes |
| Output index included | Yes |
| SHA256 checksums included | Yes |
| GitHub URL finalized | No - replace `[insert GitHub URL]` before release |
| License finalized | No - add a license file before public release if required |

---

## Version Notes

### Version 2.1 corrected + content-credibility extension

This version includes:

- Corrected event calendar with 103 clean ESG report events.
- Final event-study sample with 67 aligned ESG report-release events.
- Event panel with 1,388 firm-event-day observations.
- Regenerated event-time regression table after fixing the `rel_day` dtype issue.
- Content-credibility heterogeneity extension covering 51 matched events.
- Updated outputs, diagnostics, selected figures, and SHA256 checksums.

---

## Journal Submission Metadata

| Field | Details |
|---|---|
| Target journal | *International Journal of Islamic and Middle Eastern Finance and Management* |
| Article classification | Research Paper |
| Title | *Mandate-Backed ESG Reporting and Limited Price Discovery: Evidence from Sustainability Report Releases on the Abu Dhabi Securities Exchange* |
| Author | Veliota Drakopoulou |
| Affiliations | a Higher Colleges of Technology, United Arab Emirates; b Embry-Riddle Aeronautical University, United States |
| ORCID | 0000-0002-1670-8033 |
| Correspondence | vdrakopoulou@gmail.com |
| GitHub repository | [insert GitHub URL] |
| Zenodo replication package DOI | https://doi.org/10.5281/zenodo.20371869 |
| Data and code availability statement | Replication materials are available through the GitHub repository and Zenodo DOI listed above. |

---

## How to Cite

Please cite both the manuscript and the replication package.

### Manuscript

```text
Drakopoulou, V. (2026). Mandate-backed ESG reporting and limited price discovery:
Evidence from sustainability report releases on the Abu Dhabi Securities Exchange.
Manuscript submitted for review.
```

### Replication package

```text
Drakopoulou, V. (2026). Replication package for "Mandate-Backed ESG Reporting
and Limited Price Discovery: Evidence from Sustainability Report Releases on the
Abu Dhabi Securities Exchange". Zenodo. https://doi.org/10.5281/zenodo.20371869
```

---

## References Used in the Manuscript

Barber, B. M., & Odean, T. (2008). All that glitters: The effect of attention and news on the buying behavior of individual and institutional investors. *The Review of Financial Studies, 21*(2), 785-818.

Christensen, H. B., Hail, L., & Leuz, C. (2021). Mandatory CSR and sustainability reporting: Economic analysis and literature review. *Review of Accounting Studies, 26*, 1176-1248.

Delmas, M. A., & Burbano, V. C. (2011). The drivers of greenwashing. *California Management Review, 54*(1), 64-87.

Kothari, S. P., & Warner, J. B. (2007). Econometrics of event studies. In B. E. Eckbo (Ed.), *Handbook of corporate finance: Empirical corporate finance* (Vol. 1, pp. 3-36). Elsevier.

Loughran, T., & McDonald, B. (2016). Textual analysis in accounting and finance: A survey. *Journal of Accounting Research, 54*(4), 1187-1230.

Lyon, T. P., & Montgomery, A. W. (2015). The means and end of greenwash. *Organization & Environment, 28*(2), 223-249.

MacKinlay, A. C. (1997). Event studies in economics and finance. *Journal of Economic Literature, 35*(1), 13-39.

Spence, M. (1973). Job market signaling. *The Quarterly Journal of Economics, 87*(3), 355-374.

---

## Contact

**Veliota Drakopoulou**  
Higher Colleges of Technology, United Arab Emirates  
Embry-Riddle Aeronautical University, United States  
ORCID: 0000-0002-1670-8033  
Email: vdrakopoulou@gmail.com

---

<div align="center">

**Open science note:** This repository is designed to make the event-study workflow transparent, auditable, and reproducible. The key research claim is intentionally cautious: ESG report publication alone does not produce immediate price discovery on ADX; disclosure credibility is the more plausible investor-relevant signal.

</div>
