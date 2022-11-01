# School Audit Results and Analysis

## Overview of a Project

We have been asked to assist Maria, the chief data scientist for a city school district, to analyze student data from multiple schools and in a variety of formats. The result of our analysis will be used to inform discussions and strategic decisions at the school and district levels.

## Resources
 - Data Source: [**new_full_student_data.csv**](https://github.com/vkbt/School_District_Analysis/blob/main/Resources/new_full_student_data.csv)
 - Software: Anaconda **2022.05**, Python **3.7.13**, Conda **22.9.0**, Jupyter Notebook **6.4.12**, Pandas **1.3.5**
 
## Summary

We used three phase process (collect, prepare and analyze) to analyze this data.
 
### 1. Collect the data

Maria provided us with a raw csv file [new_full_student_data.csv](https://github.com/vkbt/School_District_Analysis/blob/main/Resources/new_full_student_data.csv).

Using **Conda** package management system we created a new virtual environment that runs the latest version of **Python 3.7** and contains all the **Anaconda** packages including **Jupyter Notebook** and named it PythonData. We imported the data into **Jupyter Notebook** using [**os**](https://docs.python.org/3/library/os.html) module and read the data using [**pandas.read_csv**](https://pandas.pydata.org/docs/reference/api/pandas.read_csv.html) function. **Jupyter Notebook** is a powerful interactive computional environment that supports **Python** and is largely used for data analysis and visualization. We used **Pandas**, a fast and powerful software library built on top of **Python**, to clean, manipulate and analyze student data provided by Maria.

<img src="https://github.com/vkbt/School_District_Analysis/blob/main/Resources/1_pandas_import_and_read_data_from_csv.png" width=100% height=100%>

### 2. Prepare the data

It is essential to clean the data before we analyze it. We used built-in Pandas functions below to handle missing data, duplicated data, messy text data, and incorrect data types:
- [**pandas.DataFrame.isna**](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.isna.html) function to identify missing values and [**pandas.DataFrame.dropna**](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.dropna.html) function to remove rows with missing values
- [**pandas.DataFrame.duplicated**](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.duplicated.html) function to identify duplicate values and [**pandas.DataFrame.drop_duplicates**](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.drop_duplicates.html) function to remove them
- we found non-numerical characters where we expected to see only numbers (i.e. 9**th** instead of 9) and converted them into numbers using [**pandas.DataFrame.replace**](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.replace.html) and [**pandas.DataFrame.astype**](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.astype.html) functions

<img src="https://github.com/vkbt/School_District_Analysis/blob/main/Resources/2_pandas_clean_data.png" width=100% height=100%>

### 3. Analyze the data

Finally, we were able to move on to the last step of our process - analyze the data. We started with high level analysis and produced summary statistics, mean math score and lowest reading score for the entire data set using [**pandas.DataFrame.describe**](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.describe.html), [**pandas.DataFrame.mean**](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.mean.html) and [**pandas.DataFrame.min**](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.min.html) functions.

<img src="https://github.com/vkbt/School_District_Analysis/blob/main/Resources/3_pandas_high_level_data_analysis.png" width=100% height=100%>

Next we moved on to targeted analysis. We analyzed 9th grade only data using [**pandas.DataFrame.loc**](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.loc.html) and [**pandas.DataFrame.describe**](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.describe.html) functions, reviewed Dixon High School's reading score for grade 10 using [**pandas.DataFrame.loc**](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.loc.html) and conditional statements and produced mean reading score for all students in grades 11 and 12 using [**pandas.DataFrame.loc**](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.loc.html), conditional statements and [**pandas.DataFrame.mean**](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.mean.html) functions.

<img src="https://github.com/vkbt/School_District_Analysis/blob/main/Resources/4_pandas_targeted_data_analysis.png" width=100% height=100%>

Lastly, we used [**pandas.DataFrame.groupby**](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.groupby.html), [**pandas.DataFrame.count**](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.count.html), and [**pandas.DataFrame.sort_values**](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.sort_values.html) functions to find the total number of students at each school and sort the output in the descending order.

<img src="https://github.com/vkbt/School_District_Analysis/blob/main/Resources/5_pandas_grouping_data.png" width=100% height=100%>

## Challenge Summary

Using our **Python**,  **Pandas** and **Jupyter Notebook** skills we were able to collect, clean up and prepare school district data for our analysis. We began the analysis by summarizing the data, continued by drilling down into the data and completed by aggregating the data. We believe the analysis of average score is beneficial for every school. We found out that Matthew Thomas from Dixon High School had the lowest reading score from the entire dataset, however Matthew’s math score was relatively close to the mean math score across all schools. The budget for charter and private schools was relatively close - 872,625 vs 911,195. Montgomery High School had highest number of students (2038) and Chang High School had lowest number of students (171). Additionally, we thought it would be beneficial to group mean reading and math scores by school type and grade.  The result showed us that the average reading score for charter and public schools was relatively close (72.0) and average math score for charter schools was higher than for public schools (67.0 and 63.0). 


Note:

During our analysis we came across a warning message that advised us: _"FutureWarning: Dropping of nuisance columns in DataFrame reductions (with 'numeric_only=None') is deprecated; in a future version this will raise TypeError.  Select only valid columns before calling the reduction."_
We were able to find 2 solutions for that:
1. make our statement more specific by adding **(numeric_only=True)** to the function
2. use filter warning functions **warnings.filterwarnings("ignore")**
