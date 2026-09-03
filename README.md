# ECE2112: Programming Assignment 3
**Ryan Joseph C. Dungca, 2ECE-D**

This repository contains code for Programming Assignment (X) of the course ECE2112, covering three problems related to _Module 3 - Pandas_. The creation of this code demonstrates the ability to:
- load a CSV dataset into a Pandas DataFrame;
- select rows and columns using positional and label-based indexing;
- filter records using conditions on a DataFrame column; and
- extract a well-defined subset of data without changing the source data.

To view the code itself, access the [related Python notebook file](), which is currently not available.

# A. Positional and Label-based Slicing
>_Objective_: After loading `cars`, complete the following operations.
> - Display the shape and complete list of column names of `cars`.
> - Using positional slicing, create `cars_6_to_10` containing rows 6 through 10 of the dataset, where the first data row is row 1.
> - From `cars_6_to_10`,  display only the columns `Model`, `mpg`, `cyl`, `hp`, and `gear`, in that order.

The constructed solution is:
```
(PRB_SOL_1)
```

# B. Model Lookup
>_Objective_: Use Boolean indexing on the `Model` column to answer both requests.
> - Display the complete row for `Toyota Corolla`.
> - For `Pontiac Firebird`, display only `Model`, `mpg`, `hp`, and `wt`.
> Store the two results in `toyota` and `pontiac`, respectively. Do not use a hard-coded row number to locate either model.

The constructed solution is:
```
(PRB_SOL_2)
```

# C. (PRB_3)
>_Objective_: Create a DataFrame named `selected_cars` containing only the records for three models: `Datsun 710`, `Lotus Europa`, and `Ferrari Dino`.
> For these records, retain only `Model`, `mpg`, `cyl`, `hp`, and `gear`. Select the rows by their model values rather than by row numbers. Display `selected_cars` and its shape.

The constructed solution is:
```
(PRB_SOL_3)
```

## History
- 2026, September 3: File created.
