# Employee-attrition-analysis
Exploratory analysis of employee attrition data using Python, pandas, Matplotlib, and Seaborn. Examines attrition patterns across education, gender, city, and payment tier.
Notebook walkthrough

### 1. Import libraries

- `pandas` loads and organizes the CSV data in a DataFrame.
- `numpy` is imported for numerical work, although the current notebook does not use it directly.
- `matplotlib.pyplot` and `seaborn` create the charts.

### 2. Load and preview the data

`pd.read_csv('Employee_Analysis.csv')` loads the CSV file into a DataFrame named `Employee`. `Employee.head()` displays the first five rows so I can check that the file loaded and its columns look as expected.

### 3. Check the dataset structure

`Employee.info()` shows the number of rows, column names, data types, and non-missing values. The dataset has 4,653 rows and 9 columns, and every column has 4,653 non-null values.

### 4. Summarize numeric columns

`Employee.describe()` calculates summary statistics such as count, mean, standard deviation, minimum, quartiles, and maximum for the numeric columns.

### 5. Summarize text categories

`Employee.describe(exclude='number')` summarizes the text columns. It shows the number of distinct values, the most frequent value, and how often that value appears.

### 6. Inspect selected values

The `.unique()` calls list the values present in `City`, `Education`, `PaymentTier`, and `ExperienceInCurrentDomain`. This helps me understand the categories and ranges represented in the data.

### 7. Count the outcome values

`Employee['LeaveOrNot'].value_counts()` counts how many records have each outcome: `0` means stayed and `1` means left. There are 3,053 records marked as stayed and 1,600 marked as left.

### 8. Visualize the outcome distribution

The pie chart displays the proportion of records marked as stayed versus left. In this dataset, about 65.6% are marked as stayed and 34.4% as left.

### 9. Compare outcome counts across categories

The Seaborn count plots compare counts of stayed and left records across `Education`, `Gender`, `City`, and `PaymentTier`. These charts show the number of records in each group; they do not by themselves show the percentage of employees who left within that group.

### 10. Calculate the percentage who left within each category

Because the category groups have different sizes, I also calculate the leave rate within each group. Since `LeaveOrNot` is 1 for a record marked as left and 0 for a record marked as stayed, the mean of this column within a group is its leave percentage.

## My conclusion

In my view, this analysis gives a useful first overview of the employee dataset. It shows that the data is complete for the columns inspected and that 34.4% of records are marked as employees who left. The within-category percentages make comparisons clearer: for example, the recorded leave rate is higher for PaymentTier 2 and for employees in Pune in this dataset. These are descriptive differences, not proof that either factor caused employees to leave. The dataset does not include a recorded reason for leaving, so this analysis cannot establish why employees left. It also has no employee identifier, so identical rows cannot be assumed to be duplicate records for the same person.

## Running the notebook

Place `Employee_Analysis.csv` in the notebook's working folder, install the libraries, and open the notebook in Jupyter:

pip install pandas numpy matplotlib seaborn jupyter
jupyter notebook Employee_Analysis.ipynb
