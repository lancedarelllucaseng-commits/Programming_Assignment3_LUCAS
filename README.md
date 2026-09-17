# Programming_Assignment3_LUCAS

ECE 2112 — Experiment 3: Python Data Analysis (Pandas)
📋 Table of Contents
Overview
Function Summary
Problem Specifications & Solutions
A. Positional and Label-Based Slicing
A.a Shape and Column Names
A.b Rows 6 to 10 Using iloc
A.c Selecting Columns Using Labels
B. Model Lookup
B.a Toyota Corolla
B.b Pontiac Firebird
C. Multi-Model Subsetting
Project File Structure
Prerequisites & Requirements
How to Run
Using Jupyter Notebook
Edge Cases Handled
Overview

This project contains the Python solutions for ECE 2112: Advanced Computer Programming and Algorithms — Experiment 3: Python Data Analysis (Pandas).

The activity focuses on using Pandas to load a CSV dataset, access rows and columns, perform positional and label-based indexing, filter records using Boolean conditions, and create specific subsets of a DataFrame without modifying the original dataset.

The main dataset used in the activity is cars.csv, which is loaded into a Pandas DataFrame named cars.

Function Summary
Code / Function	Purpose
import pandas as pd	Imports the Pandas library using the alias pd.
pd.read_csv()	Reads the cars.csv file and creates a DataFrame.
cars.shape	Returns the number of rows and columns in the DataFrame.
cars.columns	Accesses the column names of the DataFrame.
.tolist()	Converts the column-name index into a Python list.
.iloc[]	Selects rows or columns using integer-based positions.
.loc[]	Selects rows and columns using labels or Boolean conditions.
display()	Displays a DataFrame clearly in a Jupyter Notebook.
==	Compares values to a specified condition.
.isin()	Checks whether values belong to a specified list of values.
assert	Checks whether a condition is true and raises an error if it is false.
Problem Specifications & Solutions
A. Positional and Label-Based Slicing

This section demonstrates how to access rows using positional indexing and columns using their labels.

A.a Shape and Column Names

Purpose: Display the dimensions of cars and the complete list of column names.

print("Shape of cars:", cars.shape)

print("Column names:")
print(cars.columns.tolist())
A.b Rows 6 to 10 Using iloc

The first data row is considered row 1. Since Python uses zero-based indexing, rows 6 through 10 correspond to positions 5 through 9.

cars_6_to_10 = cars.iloc[5:10]

display(cars_6_to_10)

Important: The .iloc[] method is used because the problem specifically requires positional selection.

A.c Selecting Columns Using Labels

The required columns are:

Model
mpg
cyl
hp
gear
cars_6_to_10_selected = cars_6_to_10[
    ['Model', 'mpg', 'cyl', 'hp', 'gear']
]

display(cars_6_to_10_selected)

The columns are selected using their column labels, not their numerical positions.

B. Model Lookup

This section uses Boolean indexing on the Model column to find specific vehicles.

B.a Toyota Corolla

The complete row for Toyota Corolla is stored in a DataFrame named toyota.

toyota = cars[cars['Model'] == 'Toyota Corolla']

display(toyota)

The model is located by its value rather than by using a hard-coded row number.

B.b Pontiac Firebird

For Pontiac Firebird, only the following columns are displayed:

Model
mpg
hp
wt
pontiac = cars.loc[
    cars['Model'] == 'Pontiac Firebird',
    ['Model', 'mpg', 'hp', 'wt']
]

display(pontiac)

The .loc[] method combines the Boolean row condition with label-based column selection.

C. Multi-Model Subsetting

This section creates a new DataFrame named selected_cars containing exactly three models:

Datsun 710
Lotus Europa
Ferrari Dino

Only the following columns are retained:

Model
mpg
cyl
hp
gear
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
Required Check

The final DataFrame must contain 3 rows and 5 columns.

assert selected_cars.shape == (3, 5)

print("Check passed: selected_cars contains exactly 3 rows and 5 columns.")

If the shape is not (3, 5), the assert statement will raise an error.

Project File Structure

A simple GitHub project structure can be organized as follows:

ECE2112-Experiment3/
│
├── cars.csv
├── ECE2112_PA3.ipynb
└── README.md
File Descriptions
File	Description
cars.csv	Dataset used for the Pandas activity.
ECE2112_PA3.ipynb	Jupyter Notebook containing the solutions and outputs.
README.md	Documentation explaining the activity and the Python code used.
Prerequisites & Requirements

Before running the notebook, install the following:

Python 3.x
Pandas
Jupyter Notebook

Install Pandas using:

pip install pandas

To install Jupyter Notebook:

pip install notebook

The cars.csv file must be available in the same directory as the notebook, unless a different file path is specified.

How to Run
Using Jupyter Notebook
Place cars.csv and ECE2112_PA3.ipynb in the same folder.
Open a terminal or command prompt in that folder.
Start Jupyter Notebook:
jupyter notebook
Open ECE2112_PA3.ipynb.
Run the cells from beginning to end.
Check that all requested outputs are displayed.
Confirm that the final shape check produces:
Check passed: selected_cars contains exactly 3 rows and 5 columns.
Edge Cases Handled
1. Zero-Based Indexing

Python starts positional indexing at 0. Therefore, dataset rows 6 through 10 are selected using:

cars.iloc[5:10]
2. Model-Based Selection

The code does not assume fixed row numbers for the requested vehicle models. Instead, it searches the Model column:

cars['Model'] == 'Toyota Corolla'

and:

cars['Model'] == 'Pontiac Firebird'
3. Multiple Model Selection

The .isin() method allows several model names to be selected at once:

cars['Model'].isin(models)
4. Original Dataset Is Not Modified

Each requested result is stored in a new DataFrame or Series. The original cars DataFrame is not changed.

5. Required Output Shape

The final result is checked with:

assert selected_cars.shape == (3, 5)

This confirms that the required subset contains exactly three records and five columns.
