# Programming_Assignment3_LUCAS

**ECE 2112 — Advanced Computer Programming and Algorithms**

**Experiment 3: Python Data Analysis (Pandas)**

**Programming Assignment 3 LUCAS**

# 📊 ECE 2112 — Experiment 3: Python Data Analysis (Pandas)

## 📋 Table of Contents

- [Overview](#overview)
- [Function Summary](#function-summary)
- [Problem Specifications & Solutions](#problem-specifications--solutions)
  - [A. Positional and Label-Based Slicing](#a-positional-and-label-based-slicing)
    - [A.a Shape and Column Names](#aa-shape-and-column-names)
    - [A.b Rows 6 to 10 Using iloc](#ab-rows-6-to-10-using-iloc)
    - [A.c Selecting Columns Using Labels](#ac-selecting-columns-using-labels)
  - [B. Model Lookup](#b-model-lookup)
    - [B.a Toyota Corolla](#ba-toyota-corolla)
    - [B.b Pontiac Firebird](#bb-pontiac-firebird)
  - [C. Multi-Model Subsetting](#c-multi-model-subsetting)
- [Project File Structure](#project-file-structure)
- [Prerequisites & Requirements](#prerequisites--requirements)
- [How to Run](#how-to-run)
  - [Using Jupyter Notebook](#using-jupyter-notebook)
- [Edge Cases Handled](#edge-cases-handled)
- [Complete Code](#complete-code)
- [Conclusion](#conclusion)

---

# Overview

This project contains the Python solutions for **ECE 2112: Advanced Computer Programming and Algorithms — Experiment 3: Python Data Analysis (Pandas)**.

The activity focuses on using Pandas to load a CSV dataset, access rows and columns, perform positional and label-based indexing, filter records using Boolean conditions, and create specific subsets of a DataFrame without modifying the original dataset.

The main dataset used in the activity is `cars.csv`, which is loaded into a Pandas DataFrame named `cars`.

---

# Function Summary

| Code / Function | Purpose |
|---|---|
| `import pandas as pd` | Imports the Pandas library and gives it the alias `pd`. |
| `pd.read_csv()` | Loads the CSV file into a Pandas DataFrame. |
| `cars.shape` | Displays the number of rows and columns in the DataFrame. |
| `cars.columns` | Accesses the column names of the DataFrame. |
| `.tolist()` | Converts the column names into a Python list. |
| `.iloc[]` | Selects rows or columns using integer-based positions. |
| `.loc[]` | Selects rows and columns using labels or Boolean conditions. |
| `display()` | Displays DataFrames clearly in Jupyter Notebook. |
| `==` | Compares a column value with a specified value. |
| `.isin()` | Checks whether values are contained in a specified list. |
| `assert` | Checks whether a condition is true. |
| `print()` | Displays text or values as output. |

---

# Problem Specifications & Solutions

## A. Positional and Label-Based Slicing

This section demonstrates how to access rows using positional indexing and columns using their labels.

### A.a Shape and Column Names

The shape and complete list of column names of the `cars` DataFrame are displayed using Pandas.

```python
print("Shape of cars:", cars.shape)

print("Column names:")
print(cars.columns.tolist())
```

The `shape` attribute returns the number of rows and columns in the DataFrame, while `columns` provides the names of all columns.

---

### A.b Rows 6 to 10 Using `iloc`

The first data row is considered **row 1**.

Since Python uses zero-based indexing:

- Row 1 → index 0
- Row 2 → index 1
- Row 3 → index 2
- Row 4 → index 3
- Row 5 → index 4
- Row 6 → index 5
- Row 10 → index 9

Therefore, `iloc[5:10]` selects rows 6 through 10.

```python
cars_6_to_10 = cars.iloc[5:10]

display(cars_6_to_10)
```

The `.iloc[]` method is used because the problem specifically requires positional selection.

---

### A.c Selecting Columns Using Labels

The required columns are:

- `Model`
- `mpg`
- `cyl`
- `hp`
- `gear`

The columns are selected using their column labels.

```python
cars_6_to_10_selected = cars_6_to_10[
    ['Model', 'mpg', 'cyl', 'hp', 'gear']
]

display(cars_6_to_10_selected)
```

This creates a new DataFrame containing only the requested columns in the required order.

---

## B. Model Lookup

This section uses Boolean indexing on the `Model` column to locate specific vehicle records.

### B.a Toyota Corolla

The complete row for `Toyota Corolla` is stored in a DataFrame named `toyota`.

```python
toyota = cars[cars['Model'] == 'Toyota Corolla']

display(toyota)
```

The model is located using its value instead of using a hard-coded row number.

---

### B.b Pontiac Firebird

For `Pontiac Firebird`, only the required columns `Model`, `mpg`, `hp`, and `wt` are displayed.

```python
pontiac = cars.loc[
    cars['Model'] == 'Pontiac Firebird',
    ['Model', 'mpg', 'hp', 'wt']
]

display(pontiac)
```

The `.loc[]` method combines the Boolean condition for finding the model with label-based selection of the required columns.

---

## C. Multi-Model Subsetting

The required models are:

1. Datsun 710
2. Lotus Europa
3. Ferrari Dino

The required columns are:

- `Model`
- `mpg`
- `cyl`
- `hp`
- `gear`

```python
models = [
    'Datsun 710',
    'Lotus Europa',
    'Ferrari Dino'
]

selected_cars = cars.loc[
    cars['Model'].isin(models),
    ['Model', 'mpg', 'cyl', 'hp', 'gear']
]

display(selected_cars)

print("Shape of selected_cars:", selected_cars.shape)
```

The `.isin()` method is used to find all records whose model is included in the specified list.

### Required Check

The final DataFrame must contain exactly **3 rows and 5 columns**.

```python
assert selected_cars.shape == (3, 5)

print("Check passed: selected_cars contains exactly 3 rows and 5 columns.")
```

If the DataFrame does not have the required shape, the `assert` statement will produce an error.

---

# Project File Structure

The project can be organized using the following structure:

```text
Programming_Assignment3_LUCAS/
│
├── cars.csv
├── ECE2112_PA3_LUCAS.ipynb
└── README.md
```

### File Descriptions

| File | Description |
|---|---|
| `cars.csv` | CSV dataset used for the Pandas activity. |
| `ECE2112_PA3_LUCAS.ipynb` | Jupyter Notebook containing the Python solutions and outputs. |
| `README.md` | Documentation containing the project information, solutions, and code explanations. |

---

# Prerequisites & Requirements

The following software and libraries are required to run the program:

- Python 3.x
- Pandas
- Jupyter Notebook

### Install Pandas

```bash
pip install pandas
```

### Install Jupyter Notebook

```bash
pip install notebook
```

The `cars.csv` file should be placed in the same folder as the Jupyter Notebook.

---

# How to Run

## Using Jupyter Notebook

### Step 1 — Prepare the Files

Place the following files in the same folder:

```text
cars.csv
ECE2112_PA3.ipynb
README.md
```

### Step 2 — Open the Terminal or Command Prompt

Navigate to the folder containing the files.

### Step 3 — Start Jupyter Notebook

Run the following command:

```bash
jupyter notebook
```

### Step 4 — Open the Notebook

Open:

```text
ECE2112_PA3.ipynb
```

### Step 5 — Run the Program

Run all cells in the Jupyter Notebook from beginning to end.

Make sure that all required outputs are displayed.

### Step 6 — Check the Final Result

The final output should include:

```text
Check passed: selected_cars contains exactly 3 rows and 5 columns.
```

---

# Edge Cases Handled

## 1. Zero-Based Indexing

Python uses zero-based indexing. Therefore, rows 6 through 10 of the dataset are selected using:

```python
cars.iloc[5:10]
```

This correctly corresponds to rows 6, 7, 8, 9, and 10 when the first data row is considered row 1.

---

## 2. Model-Based Selection

The program does not use hard-coded row numbers to locate the requested models.

For Toyota Corolla:

```python
cars['Model'] == 'Toyota Corolla'
```

For Pontiac Firebird:

```python
cars['Model'] == 'Pontiac Firebird'
```

This allows the program to find the records based on their model names.

---

## 3. Multiple Model Selection

The `.isin()` method is used to select multiple models at the same time.

```python
models = [
    'Datsun 710',
    'Lotus Europa',
    'Ferrari Dino'
]

cars['Model'].isin(models)
```

This creates a Boolean condition that identifies records matching any of the three specified models.

---

## 4. Original DataFrame Is Not Modified

The original `cars` DataFrame is not changed during the operations.

New DataFrames are created for the requested subsets:

```python
cars_6_to_10
```

```python
cars_6_to_10_selected
```

```python
toyota
```

```python
pontiac
```

```python
selected_cars
```

This keeps the original dataset unchanged.

---

## 5. Required Column Order

The requested columns are explicitly specified in the required order:

```python
['Model', 'mpg', 'cyl', 'hp', 'gear']
```

This ensures that the resulting DataFrame follows the required column arrangement.

---

## 6. Required DataFrame Shape

The final DataFrame is checked using:

```python
assert selected_cars.shape == (3, 5)
```

The expected result is:

```text
3 rows × 5 columns
```

If the condition is true, the program displays:

```text
Check passed: selected_cars contains exactly 3 rows and 5 columns.
```

---

# Complete Code

The complete Python code used in the experiment is shown below.

```python
import pandas as pd

# Load the CSV dataset
cars = pd.read_csv("cars.csv")


# A. POSITIONAL AND LABEL-BASED SLICING

# A.a Shape and column names

# Display the shape of the DataFrame
print("Shape of cars:", cars.shape)

# Display the complete list of column names
print("Column names:")
print(cars.columns.tolist())


# A.b Rows 6 to 10 using iloc

# Select rows 6 through 10 using positional indexing
cars_6_to_10 = cars.iloc[5:10]

print("Rows 6 to 10:")
display(cars_6_to_10)


# A.c Required columns

# Select specific columns using column labels
cars_6_to_10_selected = cars_6_to_10[
    ['Model', 'mpg', 'cyl', 'hp', 'gear']
]

display(cars_6_to_10_selected)


# B. MODEL LOOKUP

# B.a Toyota Corolla

# Find Toyota Corolla using Boolean indexing
toyota = cars[cars['Model'] == 'Toyota Corolla']

display(toyota)


# B.b Pontiac Firebird

# Find Pontiac Firebird and select the required columns
pontiac = cars.loc[
    cars['Model'] == 'Pontiac Firebird',
    ['Model', 'mpg', 'hp', 'wt']
]

display(pontiac)


# C. MULTI-MODEL SUBSETTING

# Models to select
models = [
    'Datsun 710',
    'Lotus Europa',
    'Ferrari Dino'
]

# Select the three models using Boolean indexing
selected_cars = cars.loc[
    cars['Model'].isin(models),
    ['Model', 'mpg', 'cyl', 'hp', 'gear']
]

# Display the selected data
display(selected_cars)

# Display the shape
print("Shape of selected_cars:", selected_cars.shape)

# REQUIRED CHECK
assert selected_cars.shape == (3, 5)

print("Check passed: selected_cars contains exactly 3 rows and 5 columns.")
```

---

# Functions Used

## `import pandas as pd`

Imports the Pandas library and assigns it the alias `pd`.

```python
import pandas as pd
```

---

## `pd.read_csv()`

Loads the `cars.csv` file into a Pandas DataFrame.

```python
cars = pd.read_csv("cars.csv")
```

---

## `.shape`

Returns the number of rows and columns in the DataFrame.

```python
cars.shape
```

---

## `.columns`

Accesses the column names of the DataFrame.

```python
cars.columns
```

---

## `.tolist()`

Converts the column names into a Python list.

```python
cars.columns.tolist()
```

---

## `.iloc[]`

Used for positional indexing.

```python
cars.iloc[5:10]
```

This selects rows based on their integer positions.

---

## `.loc[]`

Used for label-based selection and Boolean filtering.

```python
cars.loc[
    cars['Model'] == 'Pontiac Firebird',
    ['Model', 'mpg', 'hp', 'wt']
]
```

---

## `.isin()`

Used to determine whether values belong to a specified list.

```python
cars['Model'].isin(models)
```

---

## `display()`

Used to display DataFrames clearly in a Jupyter Notebook.

```python
display(selected_cars)
```

---

## `print()`

Used to display text and values.

```python
print("Shape of cars:", cars.shape)
```

---

## `assert`

Used to verify that the final DataFrame has the required dimensions.

```python
assert selected_cars.shape == (3, 5)
```

---

# Conclusion

This experiment demonstrates the use of Pandas for basic data analysis and DataFrame manipulation. The program loads the `cars.csv` dataset and performs positional slicing, label-based column selection, Boolean filtering, and multi-model subsetting. The requested records and columns are extracted without modifying the original dataset. The final shape check verifies that the required subset contains exactly three rows and five columns.

---

# 📚 Learning Outcomes

After completing this experiment, the following Pandas concepts are demonstrated:

- Loading CSV data using `pd.read_csv()`
- Creating and working with a Pandas DataFrame
- Checking DataFrame dimensions using `.shape`
- Accessing column names using `.columns`
- Converting column names to a list using `.tolist()`
- Performing positional indexing using `.iloc[]`
- Performing label-based indexing using `.loc[]`
- Filtering DataFrame records using Boolean conditions
- Selecting multiple models using `.isin()`
- Selecting specific columns from a DataFrame
- Creating new subsets without modifying the original dataset
- Verifying the dimensions of a resulting DataFrame using `assert`

---
