# The AI Hiring Shift: Analyzing AI-Related Job Opportunities in 2026

## Project Overview

This project analyses AI-related job postings from a cleaned dataset of 1,696 job listings spanning three countries — the United States, United Kingdom, and India. The central question is: **what proportion of current job postings are AI-related, and how do those postings differ from non-AI postings across geography, job category, salary, and employment structure?**

The analysis was conducted using Python and covers the distribution of AI vs. non-AI postings, country-level breakdowns, job category patterns, within-currency salary comparisons, top hiring companies, and employment contract structure.

---

## Dataset Information

| Attribute | Detail |
|---|---|
| **File** | `ai_job_market_dataset.clean.xlsx` (sheet: `Sheet1`) |
| **Total postings** | 1,696 |
| **Countries** | United States, United Kingdom, India |
| **Date coverage** | Primarily 2026 (1,637 of 1,696 postings) |
| **AI-related postings** | 1,021 (60.20%) |
| **Non-AI postings** | 675 (39.80%) |
| **Excluded column** | `description` — no NLP analysis performed |

## Dataset Source

Kaggle: [AI Job Market Dataset](https://www.kaggle.com/datasets/mariaaqdas/ai-job-market-2026-automation-vs-traditional-role)

### Key Columns Used

| Column | Description |
|---|---|
| `title` | Job title |
| `company` | Hiring company |
| `location` | Job location |
| `category` | Job category (e.g. IT Jobs, Engineering Jobs) |
| `contract_time` | Full time / Part time / Not Specified |
| `salary_min`, `salary_max`, `salary_avg` | Salary range and average |
| `is_ai_related` | Binary flag: 1 = AI-related, 0 = non-AI |
| `created_date` | Posting date |
| `currency` | Salary currency (GBP / USD / INR) |
| `country_name` | Country of the posting |

---

## Methodology

1. **Data loading** — The pre-cleaned Excel file is loaded directly via `pandas.read_excel()`. No re-cleaning is performed.
2. **AI classification** — The `is_ai_related` column (binary flag, already established) is used to segment postings.
3. **Country analysis** — Posting counts and AI proportions are computed per country.
4. **Category analysis** — AI vs. non-AI counts are broken down by `category`.
5. **Salary analysis** — Within-currency median `salary_avg` comparisons are made separately for UK (GBP) and US (USD). India is excluded from salary comparison due to insufficient non-AI salary observations (17 AI observations, 0 non-AI).
6. **Top companies** — AI postings are aggregated by `company` and ranked.
7. **Employment structure** — `contract_time` distributions are compared between AI and non-AI postings.

> **Scope note:** Currencies are not converted. No cross-country salary comparisons are made. No NLP is performed on the `description` column.

---

## Technologies

| Library | Purpose |
|---|---|
| `pandas` | Data loading, filtering, and aggregation |
| `numpy` | Numerical operations |
| `matplotlib` | Chart generation |
| `seaborn` | Enhanced chart styling |
| `openpyxl` | Excel file reading back-end for pandas |

Python version: **3.10+**

---

## Key Findings

1. **60.20% of postings are AI-related** — 1,021 out of 1,696 total listings.
2. **India has the highest AI proportion at 83.50%**, followed by the US (59.87%) and UK (54.29%).
3. **IT Jobs and Engineering Jobs dominate AI-related postings** — 652 and 226 AI postings respectively.
4. **AI postings are associated with higher median salaries within each currency:**
   - UK: AI median £57,500 vs. non-AI median £27,091.05 (GBP)
   - US: AI median $124,965.99 vs. non-AI median $40,624.72 (USD)
   - India: excluded from salary comparison (17 AI observations, 0 non-AI observations)
5. **AI hiring is concentrated among a small number of companies** — Bespoke Labs leads with 112 AI postings, followed by Capital One (26) and A&O Shearman (20).

---

## Limitations

1. **Temporal scope** — 1,637 of 1,696 postings are from 2026, which limits historical or time-series generalizability.
2. **India salary data** — Only 17 AI salary observations and zero non-AI salary observations are available for India; no India salary comparison is made.
3. **Geographic scope** — The dataset covers only three countries (India, UK, US).
4. **No NLP** — The `description` column was excluded; job-requirement or skills-level analysis is not included.

---

## How to Run

### Prerequisites

- Python 3.10 or higher
- The dataset file `ai_job_market_dataset.clean.xlsx` in the same directory as the notebook

### Setup

```bash
# 1. (Optional) Create and activate a virtual environment
python -m venv .venv
# Windows
.venv\Scripts\activate
# macOS / Linux
source .venv/bin/activate

# 2. Install dependencies
pip install -r requirements.txt

# 3. Launch Jupyter
jupyter notebook Bhaskar_Prakash_More_AIJobMarketAnalysis.ipynb
```

---

## Project Files

| File | Description |
|---|---|
| `Bhaskar_Prakash_More_AIJobMarketAnalysis.ipynb` | Main analysis notebook |
| `ai_job_market_dataset.clean.xlsx` | Pre-cleaned dataset |
| `requirements.txt` | Python dependency list |
| `README.md` | This file |
| `Bhaskar_Prakash_More_ProjectReport.docx` | Written project report with findings |
