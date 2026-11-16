# Employee Attrition Analysis (Python)

## Business Question
Why do employees leave, and which groups are most at risk?

## Dataset
IBM HR Analytics Employee Attrition & Performance, from Kaggle (search the title on kaggle.com to download it). 1,470 employees, 35 columns (age, job role, income, overtime, travel, satisfaction scores, and whether the employee left).

Source: [IBM HR Analytics Employee Attrition & Performance (Kaggle)](https://www.kaggle.com/datasets/pavansubhasht/ibm-hr-analytics-attrition-dataset)

## Tools
Python, pandas, matplotlib, Jupyter Notebook

## Project Structure

```
hr-attrition-analysis/
├── README.md                                # project summary
├── attrition_analysis.ipynb                 # analysis notebook
├── WA_Fn-UseC_-HR-Employee-Attrition.csv    # raw data (from Kaggle)
└── hr_attrition_clean.csv                   # cleaned data
```

## Steps
1. **Loaded** the data and checked shape, data types and missing values (none found).
2. **Cleaned** the data by dropping constant columns (`EmployeeCount`, `StandardHours`, `Over18`) and the ID column (`EmployeeNumber`), leaving 31 columns.
3. **Explored** attrition rates by overtime, job role, job level and business travel using `groupby`.
4. **Checked group sizes** before trusting percentages from small groups.
5. **Compared income** of leavers vs stayers using the median, since income is skewed.
6. **Visualised** results with bar charts and a boxplot.
7. **Calculated correlations** between numeric columns and attrition.

## Key Findings
- Overall attrition is **16%** (237 of 1,470). The data is imbalanced.
- **Overtime** is the strongest signal: **30.5%** attrition vs **10.4%** without overtime.
- **Sales Representatives** have the highest attrition by role (**about 40%**). Laboratory Technicians (24%) and Human Resources (23%) are also high.
- **Entry-level (Level 1)** staff leave at **26%**, far above other levels.
- Leavers had a lower median monthly income: **3,202 vs 5,204**.
- **Highest-risk segment:** Level 1 employees working overtime, with about **53%** attrition.
- **Frequent travellers** leave at **25%** vs **8%** for non-travellers.
- All numeric correlations with attrition were weak (under 0.2 in absolute value), so group comparisons were more informative.

## Recommendations
1. **Overtime:** cap overtime, especially for Level 1 staff, and monitor overtime per team.
2. **Entry-level and sales roles:** review pay and promotion paths, and run first-year check-ins for new hires.
3. **Travel:** limit or rotate frequent travel, and offer allowances or time off for heavy travellers.

## Limitations
- Results show association, not causation. A pilot in one team would test whether these changes reduce attrition.
- Some groups are small (e.g. Sales Representative n=83, Human Resources n=52), so their percentages are less certain.
