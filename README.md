# Telco Customer Churn – Data Cleaning & EDA

Week 1 task for the **Virtual Data Science with Python Apprentice Internship (Yuva Intern)**.

The goal is to take a public dataset, clean it with Pandas and explore it to find out which customer
characteristics are linked to churn.

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
│   └── week1_data_cleaning_eda.ipynb       # all code, outputs and notes
├── reports/
│   ├── figures/                            # charts used in the report
│   └── Week1_Report_Anish_Goyal.docx
├── requirements.txt
└── README.md
```

## Cleaning steps
| Issue | Action |
|---|---|
| `TotalCharges` stored as text | converted to float |
| 11 blank `TotalCharges` (all tenure = 0) | filled with 0 – new customers not billed yet |
| Duplicates | 0 exact duplicates; 22 identical profiles kept because their IDs differ |
| `SeniorCitizen` coded 0/1 | mapped to Yes/No |
| "No internet service" / "No phone service" | merged into "No" |
| Outliers (1.5 × IQR) | none found |
| New feature | `TenureGroup` (0-12, 13-24, 25-48, 49-72 months) |

## Key findings
- Overall churn: **26.5%**
- Month-to-month contracts: **42.7%** churn vs **2.8%** on two-year contracts
- First 12 months: **47.4%** churn vs **9.5%** after 4 years
- Fiber optic: **41.9%**, electronic check: **45.3%**
- Gender has almost no effect (26.9% vs 26.2%)

## How to run
```bash
git clone https://github.com/anishgoyal0603/telco-churn-eda.git
cd telco-churn-eda
python -m venv venv
venv\Scripts\activate          # Windows  (Linux/Mac: source venv/bin/activate)
pip install -r requirements.txt
jupyter notebook notebooks/week1_data_cleaning_eda.ipynb
```
Run all cells from the `notebooks/` folder. The cleaned CSV and figures are regenerated automatically.
