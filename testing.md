---
layout: default
title: Testing | ETL for Data Science
---

# Testing

To ensure that our product meets quality standards, we will be placing a heavy emphasis on software testing throughout development. This page details the testing strategies for this project.

## Unit Testing

Unit testing will be used to ensure that components within the backend and front-end are functioning properly. They will be automatically run whenever changes are made to the source code to ensure the changes did not break existing functionality. 

### Angular.js front-end

Angular.js documentation recommends the use of the Jasmine behavior driven development framework as well as the Karma command line tool to run the tests written in Jasmine to run on different browsers. We will be following this recommendation. 

### Flask back-end

The Flask web application framework supports unit testing by simulating HTTP clients. Unit tests can then be written in any Python testing framework of our choice, and the Flask documentation shows examples using the testing module built into Python called unittest. However, we will be using a popular alternative to the default testing module, called py.test. The advantage of using py.test is that it does not require the developer to write any boilerplate (repetitive) code thus saving time.  

### Python data cleaning package

Unit tests for the Python data cleaning package will also be written using py.test. 

## Integration & Functional Testing

Integration testing will be used to ensure that the back-end and front-end components are functioning properly as an interconnected system. Functional testing will be used to ensure that the functional requirements of the product have been fulfilled. They will both be accomplished in this project by performing end to end testing on the Angular.js front-end. 

Selenium is an open-source testing framework that is frequently used for testing web applications but we will be using Protractor, the end to end testing framework recommended by the Angular.js documentation. Protractor is specifically designed for testing Angular.js applications and actually uses the server component of the Selenium framework. Protractor simulates the user’s interactions with the user interface across all major browsers and tests the behavior of the application. Protractor tests uses the same syntax as Jasmine, our choice of unit testing framework for Angular.js, so it should make writing test code more convenient. 

## User Acceptance Testing (UAT)

To ensure that our clients are satisfied with our product will be conducting UAT on a regular basis with our clients at Seldon. We aim to begin regularly incorporating UAT into our weekly Scrum sprints when we have completed the user interface in the front-end, and interaction with the system becomes possible. The UAT will be thoroughly planned in advance of the meetings, with test scenarios written in a format similar to use cases. We will only consider new features we develop to be completed the our clients have accepted them in the user acceptance tests. There is a chance we may reduce the frequency of UAT to every two weeks, if we see that not enough progress can be made to show for in a weekly sprint. 

## Manual Testing Results

<table>
<thead><tr><th>Test Scenario</th><th>Test Data</th><th>Test Data Type</th><th>Expected Results</th><th>Actual Results</th><th>Pass/Fail</th></tr></thead><tbody>
 <tr><td colspan="6"><strong>Upload Screen</strong></td></tr>
 <tr><td>Upload a CSV file</td><td>Valid CSV file</td><td>Normal</td><td>Parse file successfully and update spreadsheet with data</td><td>As expected</td><td>Pass</td></tr>
 <tr><td>Upload a JSON file</td><td>Valid JSON file</td><td>Normal</td><td>Parse file successfully and update spreadsheet with data</td><td>As expected</td><td>Pass</td></tr>
 <tr><td>Upload a XLS(X) file</td><td>Valid XLS(X) file</td><td>Normal</td><td>Parse file successfully and update spreadsheet with data</td><td>As expected</td><td>Pass</td></tr>
 <tr><td>Upload a file with inconsistencies </td><td>Invalid CSV file</td><td>Abnormal</td><td>unable to parse file error appears</td><td>As expected</td><td>Pass</td></tr>
 <tr><td>Select a sample size when uploading a file</td><td>Sample size = 50, (Normal Data)</td><td>Normal</td><td>Upload a percentage of the data-set based on the sample size, (sampling should be done randomly)</td><td>As expected</td><td>Pass</td></tr>
 <tr><td>Select a sample size when uploading a file</td><td>Sample size = -10</td><td>Abnormal</td><td>Input rejected</td><td>As expected</td><td>Pass</td></tr>
 <tr><td>Specify a seed for sampling the data</td><td>Seed = 4</td><td>Normal</td><td>Use the seed for sampling the data</td><td>As expected</td><td>Pass</td></tr>
 <tr><td>Specify a seed for sampling the data</td><td>Seed = -50</td><td>Abnormal</td><td>Input Rejected</td><td>Input accepted, File Parsing Failed</td><td>Fail</td></tr>
 <tr><td>Specify a number of initial rows to skip when uploading a file</td><td>Skip=10</td><td>Normal</td><td>Skip the first 10 rows of the file before uploading</td><td>As expected</td><td>Pass</td></tr>
 <tr><td>Specify a number of initial rows to skip when uploading a file</td><td>Skip = -10</td><td>Abnormal</td><td>Input rejected</td><td>As expected</td><td>Pass</td></tr>
 <tr><td>Unmark the option for 'file includes column headers'</td><td>Uncheck the checkbox</td><td>Normal</td><td>Upload the dataset without column headers</td><td>As Expected</td><td>Pass</td></tr>
 <tr><td colspan="6"><strong>Clean Tab</strong></td></tr>
 <tr><td>Create a duplicate of a column</td><td>Select a column</td><td>Normal</td><td>Create a duplicate of the column specified and add it to the dataset</td><td>As expected</td><td>Pass</td></tr>
 <tr><td>Split a Column using a delimiter</td><td>Delimiter ='.'</td><td>Normal</td><td>Splits the data contained within the column into multiple columns if the delimiter is present</td><td>As expected</td><td>Pass</td></tr>
 <tr><td>Split a Column that contains invalid values</td><td>Delimiter = '.'</td><td>Extreme</td><td>Split the data in the column if the delimiter is present</td><td>Operation Fails</td><td>Fail</td></tr>
 <tr><td>Combine multiple columns into a new column</td><td>Separator = '@,' New column name = email</td><td>Normal</td><td>Combine the selected columns using '@' as a separator into a new column named 'email'</td><td>As expected</td><td>Pass</td></tr>
 <tr><td>combine multiple columns into a new column</td><td>seperator = '  ' (space)</td><td>Extreme</td><td>Combine the selected columns using '  ' as a separator</td><td>The seperator is not used </td><td>Fail</td></tr>
 <tr><td>Use combine feature on a single column</td><td>Select a single column to combine only</td><td>Abnormal</td><td>The user cannot run the operation</td><td>As expected</td><td>Pass</td></tr>
 <tr><td>Impute missing data with the columns mean</td><td>Select a column with missing values</td><td>Normal</td><td>Missing values are filled with the column mean</td><td>As expected</td><td>Pass</td></tr>
 <tr><td>Impute missing data with the columns mean</td><td>Select a column with no missing values</td><td>Extreme</td><td>Column stays the same</td><td>As expected</td><td>Pass</td></tr>
 <tr><td>Impute missing data with the columns mode</td><td>Select a column with missing values</td><td>Normal</td><td>Missing values are filled with the column mode</td><td>As expected</td><td>Pass</td></tr>
 <tr><td>Impute missing data with the columns mode</td><td>Select a column with missing values but with no mode</td><td>Extreme</td><td>Missing values are filled with any value contained within the column</td><td>As expected</td><td>Pass</td></tr>
 <tr><td>Impute missing data with the columns median</td><td>Select a column with missing values</td><td>Normal</td><td>Missing values are filled with the column median</td><td>As expected</td><td>Pass</td></tr>
 <tr><td>Impute missing data with the last valid value</td><td>Select a column with missing values</td><td>Normal</td><td>Missing values are filled with the last valid value</td><td>As expected</td><td>Pass</td></tr>
 <tr><td>Impute missing data with the next valid value</td><td>Select a column with missing values</td><td>Normal</td><td>Missing values are filled with the next valid value</td><td>As expected</td><td>Pass</td></tr>
 <tr><td>Impute missing data using linear interpolation</td><td>Select a column with missing values</td><td>Normal</td><td>Missing values are filled using linear interpolation</td><td>As expected</td><td>Pass</td></tr>
 <tr><td>Impute missing data using spline interpolation</td><td> Spline order = 10</td><td>Normal</td><td>Missing values are filled using spline interpolation</td><td>As expected</td><td>Pass</td></tr>
 <tr><td>Impute missing data using spline interpolation</td><td> Spline order = -5 </td><td>Abnormal</td><td>Input rejected</td><td>As expected</td><td>Pass</td></tr>
 <tr><td>Impute missing data using polynomial interpolation</td><td> Polynomial order = 3 </td><td>Normal</td><td>Missing values are filed using polynomial interpolation</td><td>As expected</td><td>Pass</td></tr>
 <tr><td>Impute missing data using PHCIP interpolation</td><td>Select a column with missing values </td><td>Normal</td><td>Missing values are filed using PHCIP interpolation</td><td>As expected</td><td>Pass</td></tr>
 <tr><td>Impute missing data in a specific column using a custom value</td><td> Custom value = "%£$^&^%* </td><td>Extreme</td><td>Missing values are filed using the custom value</td><td>As expected</td><td>Pass</td></tr>
 <tr><td>Delete rows containing missing values in a single column</td><td>Select a column with missing values</td><td>Normal</td><td>Rows containing missing values should be deleted</td><td>As expected</td><td>Pass</td></tr>
 <tr><td>Delete rows containing missing values in a single column</td><td>Select a column with no missing values</td><td>Extreme</td><td>Dataset should remain unchanged</td><td>As expected</td><td>Pass</td></tr>
 <tr><td>Discretize the data in a column using bins</td><td>Number of  Bins = 5 </td><td>Normal</td><td>Column data changed with discretized data</td><td>As expected</td><td>Pass</td></tr>
 <tr><td>Discretize the data in a column using bins</td><td>Select a column that contains invalid values </td><td>Extreme</td><td>Column data changed with discretized data</td><td>Operation Fails</td><td>Fail</td></tr>
 <tr><td>Specify custom ranges for discretizing a column</td><td>ranges = 1,20,30,40</td><td>Normal</td><td>descretize the data using the range provided </td><td>As expected</td><td>Pass</td></tr>
 <tr><td>Quantile the data in a column using bins</td><td>Number of Bins = 5 </td><td>Normal</td><td>Column data changed with Quantized data</td><td>As expected</td><td>Pass</td></tr>
 <tr><td>Quantile the data in a column using bins</td><td>Number of Bins = -20 </td><td>Abnormal</td><td>Input rejected</td><td>As expected</td><td>Pass</td></tr>
 <tr><td>Apply categorical feature encoding to a column</td><td>Select a column</td><td>Normal</td><td>Convert each record of the column to a combination of high and low bits</td><td>As expected</td><td>Pass</td></tr>
 <tr><td>Apply categorical feature encoding to a column</td><td>Select a column with missing/invalid values</td><td>Extreme</td><td>Convert each record of the column to a combination of high and low bits</td><td>As expected</td><td>Pass</td></tr>
 <tr><td>Apply min-max feature scaling to a numeric column</td><td>Range = 10 to 20</td><td>Normal</td><td>Scale the data in the column according to the range specified</td><td>As expected</td><td>Pass</td></tr>
 <tr><td>Apply min-max feature scaling to a numeric column</td><td>Range = -3543  to  294342</td><td>Extreme</td><td>Scale the data in the column according to the range specified</td><td>As expected</td><td>Pass</td></tr>
 <tr><td>Standardise the data in a column</td><td>Select a column</td><td>Normal</td><td>Standardise the data within the column</td><td>As expected</td><td>Pass</td></tr>
 <tr><td>Find and replace all  values within a column that match the input string </td><td>Match = 'hello', Replace = 'world'</td><td>Normal</td><td>Replace all occurences of the string 'hello' with the string 'world'</td><td>As expected</td><td>Pass</td></tr>
 <tr><td>Apply find and replace feature to a column of type date</td><td>Select a colum of type date </td><td>Normal</td><td>Replace all values of the specified string with the replacement string </td><td>Operation fails </td><td>Fail</td></tr>
 <tr><td>Use find and replace feature using a regular expression </td><td>Regex = [0-9]*, Replace = 10</td><td>Normal</td><td>Replace all values that match the regex with the string '10' </td><td>As expected</td><td>Pass</td></tr>
 <tr><td>Use find and replace feature using a regular expression </td><td>Regex = [0-9]*, Replace = 48"£$%^&*f</td><td>Extreme</td><td>Replace all values that match the regex with the string provided </td><td>As expected</td><td>Pass</td></tr>
 <tr><td>filter the dataset by duplicates in a selected column</td><td>Select a column with duplicates</td><td>Normal</td><td>filter the data to display only duplicates in the selected column</td><td>As expected</td><td>Pass</td></tr>
 <tr><td>filter the dataset by duplicates in a selected column</td><td>Select a column with no duplicates</td><td>Extreme</td><td>Filtered dataset should contain nothing</td><td>As expected</td><td>Pass</td></tr>
 <tr><td>filter the dataset by Invalid values in a selected column</td><td>Select a column with invalid values</td><td>Normal</td><td>filter the data to display only rows containing invalid values in the selected column</td><td>As expected</td><td>Pass</td></tr>
 <tr><td>filter the dataset by Invalid values in a selected column</td><td>Select a column with no invalid values</td><td>Extreme</td><td>Filtered dataset should contain nothing</td><td>As expected</td><td>Pass</td></tr>
 <tr><td>filter the dataset using outliers in a selected column</td><td>Standard deviation = 2, Trim Percentage = 10</td><td>Normal</td><td>filter the data to display only rows containing outliers in the selected column</td><td>As expected</td><td>Pass</td></tr>
 <tr><td>filter the dataset using outliers in a selected column</td><td>Standard deviation = -24, Trim Percentage = -11</td><td>Abnormal</td><td>Input rejected</td><td>As expected</td><td>Pass</td></tr>
 <tr><td>Change the name of a column</td><td>New name = 'col1'</td><td>Normal</td><td>Change the column name to 'col1'</td><td>As expected</td><td>Pass</td></tr>
 <tr><td>Change the name of a column</td><td>New name = '"£$%^&*('</td><td>Extreme</td><td>Change the column name </td><td>As expected</td><td>Pass</td></tr>
 <tr><td>Change the name of a column</td><td>Change the name to a name that is already present </td><td>Extreme</td><td>Reject the input </td><td>Operation fails</td><td>Fail</td></tr>
 <tr><td>Change the type of a column from float to int </td><td>Select a column with no invalid values</td><td>Normal</td><td>Data type changes to int </td><td>As expected</td><td>Pass</td></tr>
 <tr><td>Change the type of a column from float to int </td><td>Select a column with invalid values</td><td>Extreme</td><td>Data type changes to int </td><td>Operation fails</td><td>Fail</td></tr>
 <tr><td>Change the type of a column from int to float</td><td>Select a column</td><td>Normal</td><td>Data type changes to float</td><td>As expected</td><td>Pass</td></tr>
 <tr><td>Change the type of a column from int/float to string</td><td>Select a column</td><td>Normal</td><td>Data type changes to String</td><td>As expected</td><td>Pass</td></tr>
 <tr><td>Change the type of a column from int/float to string</td><td>Select a column with missing values</td><td>Extreme</td><td>Data type changes to String</td><td>As expected</td><td>Pass</td></tr>
 <tr><td>Change the type of a column from string to datetime </td><td>Select a column of type string with date values</td><td>Normal</td><td>Data type changes to datetime</td><td>As expected</td><td>Pass</td></tr>
 <tr><td>Change the type of a column from string to datetime </td><td>Select a column of type date</td><td>Normal</td><td>Data type changes to string </td><td>Operation fails</td><td>Fail</td></tr>
 <tr><td>Delet a selected column</td><td>Select a column</td><td>Normal</td><td>The selected column should be deleted </td><td>As expected</td><td>Pass</td></tr>
 <tr><td>Sort the dataset by a single column</td><td>Select a column</td><td>Normal</td><td>Sort the dataset with respect to the specified column</td><td>As expected</td><td>Pass</td></tr>
 <tr><td>Sort the dataset by a single column</td><td>Select a column where every value is the same </td><td>Extreme</td><td>Data set remains unchanged</td><td>As expected</td><td>Pass</td></tr>
 <tr><td>Sort the dataset by multiple columns</td><td>Select multiple columns for sorting </td><td>Normal</td><td>Sort the dataset with respect to the specified columns</td><td>As expected</td><td>Pass</td></tr>
 <tr><td>Search the rows in a column using a search term</td><td>Search term =  'hello'</td><td>Normal</td><td>Display only those rows within the column that contatin the word hello (complete match)</td><td>The filtered results arenot a complete match</td><td>Fail</td></tr>
 <tr><td>Search the rows in a column usng a reular expression</td><td>Select a column that is not a numeric type, regex = [0-9]</td><td>Normal</td><td>Display only those rows that contatin the matched regex</td><td>As expected</td><td>Pass</td></tr>
 <tr><td>Search the rows in a column using a search term</td><td>Select a search term that is not contained within the column</td><td>Extreme</td><td>Filtered dataset should contain no rows </td><td>As expected</td><td>Pass</td></tr>
 <tr><td>Search for a term in all the columns </td><td>Search term =  'hello'</td><td>Normal</td><td>Display only those rows which contain the search term in any column</td><td>As expected</td><td>Pass</td></tr>
 <tr><td>Search for a term in all the columns using a regular expression</td><td>Regex = [0-9]*</td><td>Normal</td><td>Display only those rows which contain the regex term in any column</td><td>As expected</td><td>Pass</td></tr>
 <tr><td>Filter the column than search through the column</td><td>Filter = Duplicates, Search = 'hello'</td><td>Noramal</td><td>Display only those rows which contain the search term in the filtered column</td><td>Operation fails </td><td>Fail</td></tr>
 <tr><td>Edit the vallue in a particular cell</td><td>New cell value = 'hello world'</td><td>Normal</td><td>Change the value of the cell to 'hello world'</td><td>As expected</td><td>Pass</td></tr>
 <tr><td>Edit the vallue in a particular cell</td><td>New cell value = '£$^&&@(-3'</td><td>Extreme</td><td>Change the value of the cell to ''£$^&&@(-3'</td><td>As expected</td><td>Pass</td></tr>
 <tr><td colspan="6"><strong>Analysis tab</strong></td></tr>
 <tr><td>Check if all generic analyses are displayed for every column</td><td>Full dataset</td><td>Normal</td><td>Display all generic analyses for every column</td><td>As expected</td><td>Pass</td></tr>
 <tr><td>Check if all numeric analyses are displayed for numeric columns</td><td>Numeric columns</td><td>Normal</td><td>Display numeric analyses for all the numeric columns</td><td>As expected</td><td>Pass</td></tr>
 <tr><td>Check if all String analyses are displayed for string and date columns</td><td>String and date columns</td><td>Normal</td><td>Display string analyses for all the string and date columns</td><td>As expected</td><td>Pass</td></tr>
 <tr><td>Check if a word frequency table is available for string types in the analysis tab</td><td>String and date columns</td><td>Normal</td><td>Display the word frequency table for all the string and date columns</td><td>As expected</td><td>Pass</td></tr>
 <tr><td colspan="6"><strong>Visualise Tab</strong></td></tr>
 <tr><td>Check If a line chart works  correctly</td><td>Select two columns</td><td>Normal</td><td>Line charat is diaplayed</td><td>As expected</td><td>Pass</td></tr>
 <tr><td>Check If  a scatter chart work correctly</td><td>Select two columns</td><td>Normal</td><td>Scatter charat is diaplayed</td><td>As expected</td><td>Pass</td></tr>
 <tr><td>Check If  a histogram works correctly</td><td>Select two columns</td><td>Normal</td><td>Histogram is diaplayed</td><td>As expected</td><td>Pass</td></tr>
 <tr><td>Change the bin size of the histogram</td><td>bin size = 10</td><td>Normal</td><td>Display histogram with a bin size of 10</td><td>As expected</td><td>Pass</td></tr>
 <tr><td>Change the bin size of the histogram</td><td>bin size = '$%^&*</td><td>Extreme</td><td>Input rejected</td><td>Input accepted</td><td>Fail</td></tr>
 <tr><td>Check If  a frequency chart work correctly</td><td>Select a single colum </td><td>Normal</td><td>Frequency charat is diaplayed</td><td>As expected</td><td>Pass</td></tr>
 <tr><td>Check If  a time series chart work correctly</td><td>Select a column</td><td>Normal</td><td>Time series chart is displayed</td><td>Dates are not ordered before the chart is generated </td><td>Fail</td></tr>
 <tr><td colspan="6"><strong>Export/Save</strong></td></tr>
 <tr><td>Save the dataframe as a CSV file</td><td>Dataset</td><td>Normal</td><td>Dataset is downloaded as a CSV file</td><td>As expected</td><td>Pass</td></tr>
 <tr><td>Save the dataframe as a JSON file</td><td>Dataset</td><td>Normal</td><td>Dataset is downloaded as a JSON file</td><td>As expected</td><td>Pass</td></tr>
</tbody></table>

<br><a class="btn-resp" href="#top">^ Back to Top</a>