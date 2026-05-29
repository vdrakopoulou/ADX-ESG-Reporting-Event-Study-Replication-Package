#!/usr/bin/env python3
"""Create a short GitHub README for the ADX ESG event-study replication package."""
from __future__ import annotations

import argparse
from pathlib import Path
from textwrap import dedent

README = r"""
# Mandate-Backed ESG Reporting and Limited Price Discovery

## Evidence from Sustainability Report Releases on the Abu Dhabi Securities Exchange

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.20371869.svg)](https://doi.org/10.5281/zenodo.20371869)
[![Python](https://img.shields.io/badge/Python-3.10%2B-blue.svg)](https://www.python.org/)
[![ORCID](https://img.shields.io/badge/ORCID-0000--0002--1670--8033-green.svg)](https://orcid.org/0000-0002-1670-8033)
[![Replication](https://img.shields.io/badge/Replication-Package%20Available-brightgreen.svg)](https://doi.org/10.5281/zenodo.20371869)

A reproducible event-study package examining whether ESG report publication on the Abu Dhabi Securities Exchange creates price discovery, trading attention, investor-type rebalancing, or credibility-based market response.

---

## Project at a Glance

| Field | Details |
|---|---|
| Paper title | *Mandate-Backed ESG Reporting and Limited Price Discovery: Evidence from Sustainability Report Releases on the Abu Dhabi Securities Exchange* |
| Target journal | *International Journal of Islamic and Middle Eastern Finance and Management* |
| Article classification | Research Paper |
| Author | Veliota Drakopoulou |
| Affiliations | Higher Colleges of Technology, United Arab Emirates; Embry-Riddle Aeronautical University, United States |
| ORCID | [0000-0002-1670-8033](https://orcid.org/0000-0002-1670-8033) |
| Correspondence | [vdrakopoulou@gmail.com](mailto:vdrakopoulou@gmail.com) |
| GitHub repository | https://github.com/vdrakopoulou/ADX-ESG-Reporting-Event-Study-Replication-Package |
| Zenodo DOI | https://doi.org/10.5281/zenodo.20371869 |
| Data and code availability | Replication materials are available through this GitHub repository and Zenodo DOI. |

> **Note:** The journal name identifies the target outlet and should not be read as an acceptance or publication claim.

---

## Core Contribution

This project separates **ESG disclosure publication** from **ESG disclosure usefulness**.

The empirical question is narrow: when an ADX-listed firm releases an ESG, sustainability, integrated, or ESG-related annual report, does the market respond around the publication date?

The main result is cautious:

> ESG report releases do not generate statistically significant abnormal returns or abnormal trading activity. However, investor-type order imbalance shows wider-window rebalancing, and the response appears stronger when reports contain credible, specific, and verifiable ESG content.

---

## Sample Summary

| Item | Value |
|---|---:|
| ESG report universe | Approximately 101 ADX-listed firms |
| Clean ESG report events | 103 |
| Final aligned ESG report-release events | 67 |
| Firm-event-day observations | 1,388 |
| Unique tickers in aligned sample | 66 |
| Matched content-credibility events | 51 |
| Period | 2021-2025 |

---

## Main Results

| Test | Finding |
|---|---|
| Market-adjusted CARs | Not statistically significant |
| Abnormal log value traded | Not statistically significant |
| Company order imbalance | Net selling over wider windows |
| Individual order imbalance | Net buying over wider windows |
| Content credibility | Stronger wider-window trading response for higher-credibility reports |

**Interpretation:**  
This is not a positive-CAR paper. The evidence supports limited immediate price discovery, with suggestive wider-window investor-type rebalancing.

---

## Repository Structure

```text
ADX_ESG_Disclosure_Event_Study_Replication_V2_1/
|
|-- README.md
|-- CHANGELOG.md
|-- requirements.txt
|-- RUN_REPLICATION.py
|-- RUN_CONTENT_HETEROGENEITY.py
|
|-- code/
|   |-- paper1_publishable_event_tests_v2.py
|   |-- paper1_content_credibility_heterogeneity.py
|
|-- data/
|   |-- event_calendar/
|   |-- raw/
|   |-- text_source/
|
|-- outputs/
|   |-- main_event_study/
|   |-- content_credibility/
|
|-- selected_figures/
|-- manuscript/
|-- documentation/
|-- logs/
```

---

## Quick Start

Clone the repository:

```bash
git clone https://github.com/vdrakopoulou/ADX-ESG-Reporting-Event-Study-Replication-Package.git
cd ADX-ESG-Reporting-Event-Study-Replication-Package
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
outputs_reproduced/
```

---

## Key Output Files

| File | Purpose |
|---|---|
| `outputs/main_event_study/tables/sample_construction.csv` | Sample construction |
| `outputs/main_event_study/tables/event_window_tests_all_robustness.csv` | Main CAR, volume, and order-imbalance results |
| `outputs/main_event_study/tables/placebo_empirical_pvalues.csv` | Random-date placebo tests |
| `outputs/main_event_study/tables/event_time_regressions.csv` | Event-time regression evidence |
| `outputs/content_credibility/tables/table_content_credibility_high_low.csv` | Content-credibility heterogeneity tests |
| `selected_figures/` | Manuscript-ready figures |

---

## Interpretation Guardrails

The strongest defensible interpretation is:

> ESG report publication alone does not generate immediate price discovery on ADX. Wider-window investor-type order imbalance suggests gradual investor rebalancing, and this response appears stronger when ESG reports contain more credible content.

Wider-window flow results should not be interpreted as clean announcement-day causality.

---

## Data Availability

Replication materials are available through this GitHub repository and Zenodo:

https://doi.org/10.5281/zenodo.20371869

Some daily trading and investor-type data may be subject to exchange, institutional, or data-provider access conditions.

---

## Citation

Drakopoulou, V. (2026). *Replication package for "Mandate-Backed ESG Reporting and Limited Price Discovery: Evidence from Sustainability Report Releases on the Abu Dhabi Securities Exchange"*. Zenodo. https://doi.org/10.5281/zenodo.20371869

---

## Contact

**Veliota Drakopoulou**  
Higher Colleges of Technology, United Arab Emirates  
Embry-Riddle Aeronautical University, United States  
ORCID: [0000-0002-1670-8033](https://orcid.org/0000-0002-1670-8033)  
Email: [vdrakopoulou@gmail.com](mailto:vdrakopoulou@gmail.com)
"""


def main() -> None:
    parser = argparse.ArgumentParser(description="Create a short GitHub README.md file.")
    parser.add_argument("--outdir", default=".", help="Directory where README.md will be written.")
    parser.add_argument("--filename", default="README.md", help="Output file name.")
    parser.add_argument("--overwrite", action="store_true", help="Overwrite existing README.md if present.")
    args = parser.parse_args()

    outdir = Path(args.outdir).expanduser().resolve()
    outdir.mkdir(parents=True, exist_ok=True)
    output_path = outdir / args.filename

    if output_path.exists() and not args.overwrite:
        raise FileExistsError(f"{output_path} already exists. Use --overwrite to replace it.")

    output_path.write_text(dedent(README).strip() + "\n", encoding="utf-8")
    print(f"Created {output_path}")


if __name__ == "__main__":
    main()
