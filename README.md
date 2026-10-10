# Telco Customer Churn – Data Science Internship Project

Weekly tasks for the **Virtual Data Science with Python Apprentice Internship (Yuva Intern)**, all built on one public dataset.

| Week | Topic | Notebook | Report |
|---|---|---|---|
| 1 | Data acquisition, cleaning and EDA | `notebooks/week1_data_cleaning_eda.ipynb` | `reports/Week1_Report_Anish_Goyal.docx` |
| 2 | Advanced visualization and storytelling | `notebooks/week2_visual_storytelling.ipynb` | `reports/Week2_Report_Anish_Goyal.docx` |

## Dataset
IBM Telco Customer Churn – 7,043 customers, 21 columns.
Source: [IBM/telco-customer-churn-on-icp4d](https://github.com/IBM/telco-customer-churn-on-icp4d)

## Project structure
```
telco-churn-eda/
├── data/
│   ├── raw/Telco-Customer-Churn.csv        # original file, never edited
│   └── processed/telco_churn_clean.csv     # output of the cleaning steps
├── notebooks/
│   ├── week1_data_cleaning_eda.ipynb       # Week 1: cleaning + EDA
│   └── week2_visual_storytelling.ipynb     # Week 2: data story
├── reports/
│   ├── figures/                            # Week 1 charts (week2/ subfolder for Week 2)
│   ├── interactive/churn_sunburst.html     # Plotly chart, open in a browser
│   ├── Week1_Report_Anish_Goyal.docx
│   └── Week2_Report_Anish_Goyal.docx
├── requirements.txt
└── README.md
```

## Week 1 – Cleaning steps
| Issue | Action |
|---|---|
| `TotalCharges` stored as text | converted to float |
| 11 blank `TotalCharges` (all tenure = 0) | filled with 0 – new customers not billed yet |
| Duplicates | 0 exact duplicates; 22 identical profiles kept because their IDs differ |
| `SeniorCitizen` coded 0/1 | mapped to Yes/No |
| "No internet service" / "No phone service" | merged into "No" |
| Outliers (1.5 × IQR) | none found |
| New feature | `TenureGroup` (0-12, 13-24, 25-48, 49-72 months) |

## Week 1 – Key findings
- Overall churn: **26.5%**
- Month-to-month contracts: **42.7%** churn vs **2.8%** on two-year contracts
- First 12 months: **47.4%** churn vs **9.5%** after 4 years
- Fiber optic: **41.9%**, electronic check: **45.3%**
- Gender has almost no effect (26.9% vs 26.2%)

## Week 2 – The data story
Six visualizations, each answering one question for a non-technical reader:

| # | Question | Chart | Takeaway |
|---|---|---|---|
| 1 | When do customers leave? | Kaplan–Meier retention curves | ~30% of month-to-month customers leave in year one |
| 2 | Who leaves? | Contract × tenure heatmap | Month-to-month churn is 26–51% at every tenure |
| 3 | What does it cost? | Pareto chart | ~$139k/month lost (30.5% of revenue); 72% from month-to-month fiber |
| 4 | Why? | Dumbbell chart | Security/support add-ons go with less than half the churn; streaming doesn't |
| 5 | Who to target? | Risk-factor ladder | 0 red flags → 2.5% churn, 5 red flags → 72% |
| 6 | Big picture | Nested donut + interactive Plotly sunburst | 55% of customers are month-to-month, 43% of them churned |

## How to run
```bash
git clone https://github.com/anishgoyal0603/telco-churn-eda.git
cd telco-churn-eda
python -m venv venv
venv\Scripts\activate          # Windows  (Linux/Mac: source venv/bin/activate)
pip install -r requirements.txt
jupyter notebook
```
Open the notebooks inside `notebooks/` and run all cells in order (Week 1 first, because Week 2 reads the cleaned CSV it creates).
