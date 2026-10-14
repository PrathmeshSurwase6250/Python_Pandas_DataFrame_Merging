from pathlib import Path

readme = """# Pandas Merging, Joining & Concatenation

This repository contains Jupyter Notebook practice for combining and analyzing datasets with **Pandas** and **NumPy**.

## Topics Covered

- Loading CSV datasets with `pd.read_csv()`
- Inspecting DataFrames with `.head()`
- Combining DataFrames vertically with `pd.concat()`
- Creating a hierarchical index with the `keys` parameter
- Concatenating DataFrames horizontally with `axis=1`
- Performing inner, left, right, and outer merges with `DataFrame.merge()`
- Merging tables using matching key columns such as `student_id` and `course_id`
- Calculating total and month-wise course revenue
- Creating a registration report with student names, course names, and prices
- Grouping data and sorting results to find top students and registrations
- Finding common and non-common student IDs with NumPy set operations
- Self-joining a student DataFrame to match students with their partners
- Analyzing cricket deliveries and calculating sixes by venue
- Plotting course revenue with a bar chart

## Tools and Libraries

- Python
- Jupyter Notebook
- Pandas
- NumPy
- Matplotlib

## Datasets

The notebook loads these CSV files from a `dataSet` directory:

- `courses.csv`
- `matches.csv`
- `reg-month1.csv`
- `reg-month2.csv`
- `students (1).csv`
- `deliveries (1).csv`

Make sure these files are available in the expected `dataSet` directory before running the notebook. Dataset availability and filenames may vary depending on your local setup.

## Getting Started

### 1. Clone the repository

```bash
git clone <your-repository-url>
cd <your-repository-folder>
```

### 2. Create and activate a virtual environment (optional)

**macOS / Linux**
```bash
python3 -m venv .venv
source .venv/bin/activate
```

### 3. Install the required libraries

```bash
python -m pip install pandas numpy matplotlib jupyter
```

### 4. Launch Jupyter Notebook

```bash
jupyter notebook
```

Open `merging.ipynb` and run the cells in order.

## Example Operations

### Concatenate monthly registrations

```python
regs = pd.concat([nov, dec], ignore_index=True)
```

### Merge registrations with course information

```python
registration_details = regs.merge(courses, how="inner", on="course_id")
```

### Calculate revenue by course

```python
revenue_by_course = (
    regs.merge(courses, on="course_id")
        .groupby("course_name")["price"]
        .sum()
        .sort_values(ascending=False)
)
```

### Find students registered in both months

```python
common_ids = np.intersect1d(nov["student_id"], dec["student_id"])
```

## Learning Objectives

By completing this notebook, you can practice how to combine related datasets, select the appropriate merge type, perform group-based analysis, calculate revenue, compare records across datasets, and derive insights from tabular data.

## Author

**Prathamesh Surwase**

## Note

This is a learning and practice notebook. The results depend on the contents of the CSV datasets supplied with the notebook.
"""
path = Path("/mnt/data/README.md")
path.write_text(readme, encoding="utf-8")
print(f"Created: {path}")
