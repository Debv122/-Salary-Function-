# SF Employee Salary, Data Processing Assignment

A Jupyter Notebook project using the **San Francisco City Employee Salaries (2011–2018)**
dataset to demonstrate Python data processing, error handling, file management, and R integration.

---

## Project Structure

```
employee_project/
├── Employee_Data_Processing.ipynb   # Main notebook — all 6 tasks
├── Total.csv                        # SF salary dataset (2011–2018)
├── unzip_display.R                  # Standalone R script for Task 6
└── README.md                        # This file
```

After running the notebook, `Employee Profile.zip` will also be generated in the same folder.

---

## Dataset Columns (`Total.csv`)

| Column | Description |
|--------|-------------|
| `Id` | Unique record identifier |
| `EmployeeName` | Employee's full name |
| `JobTitle` | Role / job title |
| `BasePay` | Base annual salary (USD) |
| `OvertimePay` | Overtime pay (USD) |
| `OtherPay` | Other compensation (USD) |
| `Benefits` | Benefits value (USD) |
| `TotalPay` | BasePay + OvertimePay + OtherPay |
| `TotalPayBenefits` | TotalPay + Benefits |
| `Year` | Fiscal year (2011–2018) |
| `Notes` | Optional notes |
| `Agency` | City agency name |
| `Status` | Employment status |

---

## Requirements

### Python
- Python 3.10+
- Jupyter Notebook or JupyterLab
- `pandas`, `numpy`
- `rpy2` (for the embedded R cell in Task 6)

```bash
pip install pandas numpy rpy2 notebook
```

### R
- R 4.0+ installed on your system
- No additional R packages needed — only base R is used

---

## How to Run

### Option A — Jupyter Notebook (all tasks)

```bash
jupyter notebook Employee_Data_Processing.ipynb
```

Run all cells top to bottom (**Kernel > Restart & Run All**).

The notebook will:
1. Load `Total.csv` and coerce pay columns to numeric
2. Look up employees by name using `get_employee_details()`
3. Build an ID-keyed employee dict and a year-level summary dict
4. Demonstrate 5 types of error handling
5. Export 3 employee profiles to `Employee Profile.zip`
6. Use embedded R (via `rpy2`) to unzip and display the profiles

### Option B — Standalone R Script (Task 6 only)

After Task 5 has generated `Employee Profile.zip`:

```bash
Rscript unzip_display.R
```

---

## Task Summary

| # | Task | Key function / approach |
|---|------|------------------------|
| 1 | Import data | `pd.read_csv('Total.csv')` + numeric coercion |
| 2 | Employee function | `get_employee_details(name, df)` — case-insensitive, returns all years |
| 3 | Dictionary processing | `employee_by_id` dict + `year_stats` aggregation dict |
| 4 | Error handling | `safe_load_salary_data()` — 5 exception types covered |
| 5 | Export to ZIP | `export_employee_to_zip()` — CSV zipped into `Employee Profile.zip` |
| 6 | R unzip + display | `unzip()` + `read.csv()` + combined `data.frame` print |

---

## Notes

- `get_employee_details()` is case-insensitive and returns all records across all years.
- Pay columns are coerced to `float64`; rows with non-numeric values become `NaN` gracefully.
- The ZIP uses append mode so multiple employees can be added to the same archive.
- If `rpy2` or R is not available, run `unzip_display.R` directly with `Rscript`.
