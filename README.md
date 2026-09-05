# ECE2112: Programming Assignment 3
**Ryan Joseph C. Dungca, 2ECE-D**

This repository contains code for Programming Assignment (X) of the course ECE2112, covering three problems related to _Module 3 - Pandas_. The creation of this code demonstrates the ability to:
- load a CSV dataset into a Pandas DataFrame;
- select rows and columns using positional and label-based indexing;
- filter records using conditions on a DataFrame column; and
- extract a well-defined subset of data without changing the source data.

To view the code itself, access the [related Python notebook file](). The `cars.csv` file, required to properly execute all included code, is not included.

The prerequisite first line for the problem solution, `cars = pd.read_csv('cars.csv')`, simply imports the local `.csv` file `cars.csv` into the variable `cars` as a Pandas DataFrame. It must be noted that the file is named relatively: this means that the file exists in the same directory as the `.ipynb` file to be run. If the file is not in the same directory as the notebook, its exact location on the system must be specified instead of simply its name.

To display the requested DataFrames over all three problems, the function `display()` is used over the `print()` function, as the former provides a richer format for the data, compared to the constructed plaintext table returned by the latter.

# A. Positional and Label-based Slicing
>_Objective_: After loading `cars`, complete the following operations.
> - Display the shape and complete list of column names of `cars`.
> - Using positional slicing, create `cars_6_to_10` containing rows 6 through 10 of the dataset, where the first data row is row 1.
> - From `cars_6_to_10`,  display only the columns `Model`, `mpg`, `cyl`, `hp`, and `gear`, in that order.

To display the shape of the new DataFrame, the attribute of the DataFrame `cars.shape` is printed by `print(cars.shape)`. Additionally, to return the column names of the DataFrame, a new list is constructed with `cols = cars.columns.tolist()`, where the chained methods `.columns` and `.tolist()` return only the column labels of the DataFrame, and then construct a list using these labels, respectively.

Next, to construct the requested DataFrame `cars_6_to_10` with the required attributes, the line `cars_6_to_10 = cars.loc[5:10]` is used. Here, positional slicing is used, which behaves similarly to slicing in other libraries, which takes the given range but omits the value of the upper limit itself. The format for the used method, `.iloc[]`, is `DataFrame.iloc[row_indexes, column_indexes]`, using the integer labels of the row and column range to be included. Notably, the method will default to including the entire range, should ranges for the row or column be omitted.

For the used line of code, `cars.iloc[5:10]` omits the column range, implying that the entire range of columns for the selected rows will be included. Therefore, it will only include rows 5 to 10, but excluding row 10, it simply includes rows 5 to 9, which are rows 6 to 10 of the DataFrame if the indexes of the rows are shifted by 1, as assumed by the instructions.

Finally for this problem, it is requested to display only certain columns of the previously constructed `cars_6_to_10` DataFrame. As the general instruction requests a separate DataFrame for each subset, a new DataFrame is constructed using the `.loc[]` method, which works similarly to `.iloc[]`, but instead uses the specific labels for each row and column instead of their integer labels. Notably, the label for each row is not dictated by the `Model`, but by the automatically-assigned integers. Similarly, omitting row or column ranges include the entire range for each.

The line `cars_6_to_10_select = cars_6_to_10.loc[:, ['Model', 'mpg', 'cyl', 'hp', 'gear']]` consturcts the new DataFrame `cars_6_to_10`. As previously noted, the row range is omitted, implying that the entirety of `cars_6_to_10`'s rows must be included. However, following the requirement, the specific columns required by the instructions are named by their labels as the argument for the column range.

The constructed solution, omitting importing both the Pandas library and `cars.csv`, is:
```py
cols = cars.columns.tolist()
cars_6_to_10 = cars.iloc[5:10]
cars_6_to_10_select = cars_6_to_10.loc[:, ['Model', 'mpg', 'cyl', 'hp', 'gear']]

print(cars.shape)
display(cols)
display(cars_6_to_10)
display(cars_6_to_10_select)
```

# B. Model Lookup
>_Objective_: Use Boolean indexing on the `Model` column to answer both requests.
> - Display the complete row for `Toyota Corolla`.
> - For `Pontiac Firebird`, display only `Model`, `mpg`, `hp`, and `wt`.
> Store the two results in `toyota` and `pontiac`, respectively. Do not use a hard-coded row number to locate either model.

As requested by the specific problem instructions, two DataFrames are constructed to fulfill the requested conditions via Boolean indexing. Firstly, the line `toyota = cars[cars['Model']=='Toyota Corolla']` constructs the DataFrame `toyota` containing only the row that fulfills the condition that the `Model` attribute is exactly `Toyota Corolla`. As the column range is omitted, all columns are included, completing the row of information for the Toyota Corolla.

Next, the line `pontiac = cars[car['Model']=='Pontiac Firebird', ['Model', 'mpg', 'hp', 'wt']]` constructs the DataFrame `pontiac`, containing the row fulfilling the condition where the `Model` is exactly `Pontiac Firebird`. Additionally, specific columns to be displayed are given as the column range, as specified by the instructions. 

The constructed solution, omitting importing both the Pandas library and `cars.csv`, is:
```py
toyota = cars[cars['Model']=='Toyota Corolla']
pontiac = cars.loc[cars['Model']=='Pontiac Firebird', ['Model', 'mpg', 'hp', 'wt']]

display(toyota)
display(pontiac)
```

# C. Multi-Model Subsetting
>_Objective_: Create a DataFrame named `selected_cars` containing only the records for three models: `Datsun 710`, `Lotus Europa`, and `Ferrari Dino`.
> For these records, retain only `Model`, `mpg`, `cyl`, `hp`, and `gear`. Select the rows by their model values rather than by row numbers. Display `selected_cars` and its shape.

For this problem, the DataFrame `selected_cars` is constructed by the line:
```
selected_cars = cars.loc[(cars['Model']=='Datsun 710')|(cars['Model']=='Lotus Europa')|(cars['Model']=='Ferrari Dino'), ['Model','mpg','cyl','hp','gear']]
```
Despite the length, it retains the form of the previous problems utilizing the `.loc[]` method, to fulfill the requirement that rows are selected by `Model` values. Here, the row range is simply a chain of logical OR operations (`|`), where the included rows are those whose `Model` are either `Datsun 710`, or `Lotus Europa`, or `Ferrari Dino`. A column range is also included, which specifies only the columns `Model`, `mpg`, `cly`, `hp`, and `gear` of those requested rows are included.

Finally, to check the shape of the constructed DataFrame `selected_cars`, which should yield `3, 5` to validate its inclusion of three rows and five columns from the original `cars` DataFrame, the function `print(selected_cars.shape)` is used.

The constructed solution is:
```py
selected_cars = cars.loc[(cars['Model']=='Datsun 710')|(cars['Model']=='Lotus Europa')|(cars['Model']=='Ferrari Dino'), ['Model','mpg','cyl','hp','gear']]

print(selected_cars.shape)
display(selected_cars)
```

## History
- 2026, September 3: File created.
- 2026, September 4: Notebook uploaded.
- 2026, September 5: Solution explanations introduced; revised notebook uploaded.
