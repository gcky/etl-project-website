---
layout: default
title: Testing | ETL for Data Science
---

# Testing and Evaluation

To ensure that our system meets quality standards, we will be placing a heavy emphasis on software testing throughout development. This page details the testing strategies for this project. Click the buttons below to jump to the corresponding section.

<a class="btn-resp" href="#unit-testing">1. Unit Testing</a>
<a class="btn-resp" href="#functional-testing">2. Functional Testing</a>
<a class="btn-resp" href="#compatibility">3. Compatibility Testing</a>
<a class="btn-resp" href="#requirements-evaluation">4. Requirements Evaluation</a>
<a class="btn-resp" href="#performance">5. Performance Testing</a>
<a class="btn-resp" href="#uat">6. Acceptance Testing</a>

<a class="anchor" id="unit-testing"></a>

## Unit Testing

To ensure the integrity, completeness and correctness of our software, we developed a individual test suites which consisted of unit tests for both our front and back-ends. After developing a feature we would carry out regression testing by automatically running the test suites to ensure no new bugs are introduced.

### Back-end - Python Modules

Since our backend consisted of Python modules, we used a full-featured testing tool called Pytest to create our unit tests. While developing the test suite for the backend, we made sure to individually test each python function with extreme, normal and abnormal data to ensure that our software was robust enough. In total we had 100 unit tests in our test suite.

### Front-end - Angular.js

To construct unit tests for the front-end, we used Jasmine which is a behaviour driven development framework as well as Karma which is a test runner that is framework agnostic. we used Karma to run the tests written in Jasmine to run on different browsers. While constructing the unit tests we tried to test most of the important features of our UI. Overall we have 75 tests in our suite.

The locations of these unit tests can be found in the [Project File Structure]({{site.baseurl}}/dev/files.html) page of our technical documentation.

<br><a class="btn-resp" href="#top">^ Back to Top</a>

<hr>

<a class="anchor" id="functional-testing"></a>

## Functional Testing

Functional testing is used as a quality assurance process for a software system.It refers to activities that verify a specific action or function of the code. Functional test tends to answer the questions like “can the user do this” or “does this particular feature work”.  In order to carry out our functional testing, we used our requirements specification to construct a series of test cases which were used for manual black-box testing.

### Manual Testing
The test cases we used were built around the specification, system requirements and design parameters. For each test case we selected both valid and invalid inputs in order to determine whether the system produces the correct desired output. Each of the test cases were carried out manually, the type of test carried out and the result of each test is recorded in the table below:

<table>
<thead><tr class="headerRow"><td>Test Scenario</td><td>Test Data</td><td>Test Data Type</td><td>Expected Results</td><td>Actual Results</td><td>Pass/Fail</td></tr></thead><tbody>
 <tr class="seperator"><td colspan="6"><strong>Upload Screen</strong></td></tr>
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
 <tr class="seperator"><td colspan="6"><strong>Clean Tab</strong></td></tr>
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
 <tr class="seperator"><td colspan="6"><strong>Analysis tab</strong></td></tr>
 <tr><td>Check if all generic analyses are displayed for every column</td><td>Full dataset</td><td>Normal</td><td>Display all generic analyses for every column</td><td>As expected</td><td>Pass</td></tr>
 <tr><td>Check if all numeric analyses are displayed for numeric columns</td><td>Numeric columns</td><td>Normal</td><td>Display numeric analyses for all the numeric columns</td><td>As expected</td><td>Pass</td></tr>
 <tr><td>Check if all String analyses are displayed for string and date columns</td><td>String and date columns</td><td>Normal</td><td>Display string analyses for all the string and date columns</td><td>As expected</td><td>Pass</td></tr>
 <tr><td>Check if a word frequency table is available for string types in the analysis tab</td><td>String and date columns</td><td>Normal</td><td>Display the word frequency table for all the string and date columns</td><td>As expected</td><td>Pass</td></tr>
 <tr class="seperator"><td colspan="6"><strong>Visualise Tab</strong></td></tr>
 <tr><td>Check If a line chart works  correctly</td><td>Select two columns</td><td>Normal</td><td>Line charat is diaplayed</td><td>As expected</td><td>Pass</td></tr>
 <tr><td>Check If  a scatter chart work correctly</td><td>Select two columns</td><td>Normal</td><td>Scatter charat is diaplayed</td><td>As expected</td><td>Pass</td></tr>
 <tr><td>Check If  a histogram works correctly</td><td>Select two columns</td><td>Normal</td><td>Histogram is diaplayed</td><td>As expected</td><td>Pass</td></tr>
 <tr><td>Change the bin size of the histogram</td><td>bin size = 10</td><td>Normal</td><td>Display histogram with a bin size of 10</td><td>As expected</td><td>Pass</td></tr>
 <tr><td>Change the bin size of the histogram</td><td>bin size = '$%^&*</td><td>Extreme</td><td>Input rejected</td><td>Input accepted</td><td>Fail</td></tr>
 <tr><td>Check If  a frequency chart work correctly</td><td>Select a single colum </td><td>Normal</td><td>Frequency charat is diaplayed</td><td>As expected</td><td>Pass</td></tr>
 <tr><td>Check If  a time series chart work correctly</td><td>Select a column</td><td>Normal</td><td>Time series chart is displayed</td><td>Dates are not ordered before the chart is generated </td><td>Fail</td></tr>
 <tr class="seperator"><td colspan="6"><strong>Export/Save</strong></td></tr>
 <tr><td>Save the dataframe as a CSV file</td><td>Dataset</td><td>Normal</td><td>Dataset is downloaded as a CSV file</td><td>As expected</td><td>Pass</td></tr>
 <tr><td>Save the dataframe as a JSON file</td><td>Dataset</td><td>Normal</td><td>Dataset is downloaded as a JSON file</td><td>As expected</td><td>Pass</td></tr>
</tbody></table>

**N.B.** Most of the failures has since been fixed.

<br><a class="btn-resp" href="#top">^ Back to Top</a>

<hr>

<a class="anchor" id="compatibility"></a>

## Compatibility Testing

With all the different operating systems and web browsers available, it is very important to these the compatibility of an application. Below are some of the tests we carried out:

### Browser compatibility

Ensuring that a web application works on the most widely used browsers is extremely important, this is because applications can behave differently dependent on browsers they are run on. It is also the case that different browsers have different configurations and settings that a web page should be compatible with. We therefore tested our web application on Internet explorer, Firefox, Chrome, Safari, and Edge with different versions.

### OS compatibility

In some cases a functionality of a web application may not be compatible with all operating systems. Technologies such as graphic designs and interface calls may not be available in all Operating Systems. We therefore tested our application on Windows, Mac and Linux systems.

<br><a class="btn-resp" href="#top">^ Back to Top</a>

<hr>

<a class="anchor" id="requirements-evaluation"></a>

## Requirements Evaluation

Throughout the development of the system, we evaluate the progress and success of the system by referring to our requirements specification for the system and made sure that all must have and should have requirements were implemented. The status of each requirement at the end of the project is listed below:

<table class="table table-bordered table-hover table-condensed">
<tbody><tr class="headerRow"><td>ID</td>
<td width="60%">Requirement</td>
<td>Type</td>
<td>Category</td>
<td>Priority</td>
<td>Status</td>
</tr>
<tr><td class="seperator" colspan="6">UI/UX</td>
</tr>
<tr><td>Um1</td>
<td>The DCS shall display the user imported dataset as a spreadsheet/table.</td>
<td>Functional</td>
<td>UI/UX</td>
<td>Must</td>
<td>Implemented</td>
</tr>
<tr><td>Uc1</td>
<td>The DCS shall display all unresolved cleanliness issues</td>
<td>Functional</td>
<td>UI/UX</td>
<td>Could</td>
<td>Not Implemented</td>
</tr>
<tr><td>Uc2</td>
<td>The DCS shall offer the user a choice between a pure GUI interface and a notebook style interface.</td>
<td>Functional</td>
<td>UI/UX</td>
<td>Could</td>
<td>Withdrawn</td>
</tr>
<tr><td>Uc3</td>
<td>The DCS shall support persistence of user sessions.</td>
<td>Functional</td>
<td>UI/UX</td>
<td>Could</td>
<td>Implemented</td>
</tr>
<tr><td>Uc4</td>
<td>The DCS shall support partial loading of rows in datasets.</td>
<td>Functional</td>
<td>UI/UX</td>
<td>Could</td>
<td>Implemented</td>
</tr>
<tr><td>Uw1</td>
<td>The DCS shall allow multiple users to collaborate showing changes in real time</td>
<td>Functional</td>
<td>UI/UX</td>
<td>Would</td>
<td>Partially Implemented</td>
</tr>
<tr><td>Uw2</td>
<td>The DCS shall compute a &quot;messiness&quot; score.</td>
<td>Functional</td>
<td>UI/UX</td>
<td>Would</td>
<td>Not Implemented</td>
</tr>
<tr><td class="seperator" colspan="6">Data Loading</td>
</tr>
<tr><td>Lm1</td>
<td>The DCS shall support loading of user-uploaded CSV files. </td>
<td>Functional</td>
<td>Data Loading</td>
<td>Must</td>
<td>Implemented</td>
</tr>
<tr><td>Lm2</td>
<td>The DCS shall allow users to specify variable names and types.</td>
<td>Functional</td>
<td>Data Loading</td>
<td>Must</td>
<td>Implemented</td>
</tr>
<tr><td>Ls1</td>
<td>The DCS shall support a Date variable type.</td>
<td>Functional</td>
<td>Data Loading</td>
<td>Should</td>
<td>Implemented</td>
</tr>
<tr><td>Ls2</td>
<td>The DCS shall parse dates with a user-provided format string.</td>
<td>Functional</td>
<td>Data Loading</td>
<td>Should</td>
<td>Implemented</td>
</tr>
<tr><td>Lc1</td>
<td>The DCS shall support loading of user-uploaded structured file formats (JSON, Excel).</td>
<td>Functional</td>
<td>Data Loading</td>
<td>Could</td>
<td>Implemented</td>
</tr>
<tr><td>Lc2</td>
<td>The DCS shall support partial loading of columns in datasets.</td>
<td>Functional</td>
<td>Data Loading</td>
<td>Could</td>
<td>Not Implemented</td>
</tr>
<tr><td>Lw1</td>
<td>The DCS shall support loading user-uploaded unstructured data text files. </td>
<td>Functional</td>
<td>Data Loading</td>
<td>Would</td>
<td>Not Implemented</td>
</tr>
<tr><td>Lw2</td>
<td>The DCS shall support parsing of unstructured file format.</td>
<td>Functional</td>
<td>Data Loading</td>
<td>Would</td>
<td>Not Implemented</td>
</tr>
<tr><td>Lw3</td>
<td>The DCS shall support loading of data files over network.</td>
<td>Functional</td>
<td>Data Loading</td>
<td>Would</td>
<td>Not Implemented</td>
</tr>
<tr><td>Lw4</td>
<td>The DCS shall load asynchronously. </td>
<td>Functional</td>
<td>Data Loading</td>
<td>Would</td>
<td>Not Implemented</td>
</tr>
<tr><td>Lw5</td>
<td>The DCS shall support loading of data streams.</td>
<td>Functional</td>
<td>Data Loading</td>
<td>Would</td>
<td>Not Implemented</td>
</tr>
<tr><td>Lw6</td>
<td>The DCS shall support an Email variable type.</td>
<td>Functional</td>
<td>Data Loading</td>
<td>Would</td>
<td>Not Implemented</td>
</tr>
<tr><td>Lw7</td>
<td>The DCS shall intelligently guess variable types. </td>
<td>Functional</td>
<td>Data Loading</td>
<td>Would</td>
<td>Partially Implemented</td>
</tr>
<tr><td class="seperator" colspan="6">Data Viewing</td>
</tr>
<tr><td>Xs1</td>
<td>The DCS shall support sorting of rows by user-specified column</td>
<td>Functional</td>
<td>Data Viewing</td>
<td>Should</td>
<td>Implemented</td>
</tr>
<tr><td>Xs2</td>
<td>The DCS shall support searching datasets with a keyword</td>
<td>Functional</td>
<td>Data Viewing</td>
<td>Should</td>
<td>Implemented</td>
</tr>
<tr><td>Xc1</td>
<td>The DCS shall support querying datasets with SQL</td>
<td>Functional</td>
<td>Data Viewing</td>
<td>Could</td>
<td>Not Implemented</td>
</tr>
<tr><td class="seperator" colspan="6">Data Cleaning</td>
</tr>
<tr><td>Cm1</td>
<td>The DCS shall support removing rows as a universal cleaning operation </td>
<td>Functional</td>
<td>Data Cleaning</td>
<td>Must</td>
<td>Implemented</td>
</tr>
<tr><td>Cm2</td>
<td>The DCS shall support inserting user-specified values as a universal cleaning operation </td>
<td>Functional</td>
<td>Data Cleaning</td>
<td>Must</td>
<td>Implemented</td>
</tr>
<tr><td>Cm3</td>
<td>The DCS shall show rows with invalid numbers in specified column</td>
<td>Functional</td>
<td>Data Cleaning</td>
<td>Must</td>
<td>Implemented</td>
</tr>
<tr><td>Cm4</td>
<td>The DCS shall show rows with missing values in specified column</td>
<td>Functional</td>
<td>Data Cleaning</td>
<td>Must</td>
<td>Implemented</td>
</tr>
<tr><td>Cm5</td>
<td>The DCS shall support cleaning of missing values by inserting an average</td>
<td>Functional</td>
<td>Data Cleaning</td>
<td>Must</td>
<td>Implemented</td>
</tr>
<tr><td>Cm6</td>
<td>The DCS shall support cleaning of missing values by filling with the most recent value</td>
<td>Functional</td>
<td>Data Cleaning</td>
<td>Must</td>
<td>Implemented</td>
</tr>
<tr><td>Cm7</td>
<td>The DCS shall support cleaning of missing values by interpolation</td>
<td>Functional</td>
<td>Data Cleaning</td>
<td>Must</td>
<td>Implemented</td>
</tr>
<tr><td>Cs1</td>
<td>The DCS shall show rows where Date parsing failed</td>
<td>Functional</td>
<td>Data Cleaning</td>
<td>Should</td>
<td>Withdrawn</td>
</tr>
<tr><td>Cs2</td>
<td>The DCS shall show duplicate rows</td>
<td>Functional</td>
<td>Data Cleaning</td>
<td>Should</td>
<td>Implemented</td>
</tr>
<tr><td>Cs3</td>
<td>The DCS shall provide the option to ignore outliers</td>
<td>Functional</td>
<td>Data Cleaning</td>
<td>Should</td>
<td>Withdrawn</td>
</tr>
<tr><td>Cs4</td>
<td>The DCS shall provide the option to filter rows using regular expression</td>
<td>Functional</td>
<td>Data Cleaning</td>
<td>Should</td>
<td>Implemented</td>
</tr>
<tr><td>Cs5</td>
<td>The DCS shall support data normalisation and standarisation</td>
<td>Functional</td>
<td>Data Cleaning</td>
<td>Should</td>
<td>Implemented</td>
</tr>
<tr><td>Cc1</td>
<td>The DCS shall provide the option to group multiple text representation of the same entity and replace them with a single value</td>
<td>Functional</td>
<td>Data Cleaning</td>
<td>Could</td>
<td>Not Implemented</td>
</tr>
<tr><td>Cc2</td>
<td>The DCS shall fix escaped HTML strings</td>
<td>Functional</td>
<td>Data Cleaning</td>
<td>Could</td>
<td>Not Implemented</td>
</tr>
<tr><td>Cc3</td>
<td>The DCS shall show values that are not found in English dictionary </td>
<td>Functional</td>
<td>Data Cleaning</td>
<td>Could</td>
<td>Not Implemented</td>
</tr>
<tr><td>Cw1</td>
<td>The DCS shall show rows where Email parsing failed</td>
<td>Functional</td>
<td>Data Cleaning</td>
<td>Would</td>
<td>Not Implemented</td>
</tr>
<tr><td class="seperator" colspan="6">Data Analysis</td>
</tr>
<tr><td>Am1</td>
<td>The DCS shall show the unique values and their count of every column of the dataset</td>
<td>Functional</td>
<td>Data Analysis</td>
<td>Must</td>
<td>Implemented</td>
</tr>
<tr><td>Am2</td>
<td>The DCS shall show the mean, median, mode of columns with numerical data</td>
<td>Functional</td>
<td>Data Analysis</td>
<td>Must</td>
<td>Implemented</td>
</tr>
<tr><td>Am3</td>
<td>The DCS shall show the max and min values of columns with numerical data</td>
<td>Functional</td>
<td>Data Analysis</td>
<td>Must</td>
<td>Implemented</td>
</tr>
<tr><td>Am4</td>
<td>The DCS shall show the range and standard deviation of columns with numerical data</td>
<td>Functional</td>
<td>Data Analysis</td>
<td>Must</td>
<td>Implemented</td>
</tr>
<tr><td>As1</td>
<td>The DCS shall show text analysis such as most frequent word for string type data</td>
<td>Functional</td>
<td>Data Analysis</td>
<td>Should</td>
<td>Implemented</td>
</tr>
<tr><td class="seperator" colspan="6">Data Visualisation</td>
</tr>
<tr><td>Vm1</td>
<td>The DCS shall be able to visualise data using histograms</td>
<td>Functional</td>
<td>Data Visualisation</td>
<td>Must</td>
<td>Implemented</td>
</tr>
<tr><td>Vm2</td>
<td>The DCS shall be able to visualise data using line charts</td>
<td>Functional</td>
<td>Data Visualisation</td>
<td>Must</td>
<td>Implemented</td>
</tr>
<tr><td>Vs1</td>
<td>The DCS shall be able to visualise data using scatter plots</td>
<td>Functional</td>
<td>Data Visualisation</td>
<td>Should</td>
<td>Implemented</td>
</tr>
<tr><td>Vs2</td>
<td>The DCS shall be able to visualise data using time-series plots</td>
<td>Functional</td>
<td>Data Visualisation</td>
<td>Should</td>
<td>Implemented</td>
</tr>
<tr><td>Vc1</td>
<td>The DCS shall provide the option to export graphs to image</td>
<td>Functional</td>
<td>Data Visualisation</td>
<td>Could</td>
<td>Implemented</td>
</tr>
<tr><td>Vc2</td>
<td>The DCS shall be able to visualise data using pie charts</td>
<td>Functional</td>
<td>Data Visualisation</td>
<td>Could</td>
<td>Not Implemented</td>
</tr>
<tr><td>Vw1</td>
<td>The DCS shall be able to visualise data using regression matricies</td>
<td>Functional</td>
<td>Data Visualisation</td>
<td>Would</td>
<td>Not Implemented</td>
</tr>
<tr><td>Vw2</td>
<td>The DCS shall be able to visualise data using bar charts</td>
<td>Functional</td>
<td>Data Visualisation</td>
<td>Would</td>
<td>Partially Implemented</td>
</tr>
<tr><td class="seperator" colspan="6">Others</td>
</tr>
<tr><td>Nm1</td>
<td>The DCS shall use a browser as its user interface</td>
<td>Non-Functional</td>
<td>Compliance to Standards</td>
<td>Must</td>
<td>Implemented</td>
</tr>
<tr><td>Nm2</td>
<td>The DCS shall support the latest versions of Safari, Internet Explorer, Chrome, Firefox</td>
<td>Non-Functional</td>
<td>Performance</td>
<td>Must</td>
<td>Implemented</td>
</tr>
<tr><td>Nm3</td>
<td>The DCS shall be easily installable by an untrained user with the help of documentation</td>
<td>Non-Functional</td>
<td>Deployment</td>
<td>Must</td>
<td>Implemented</td>
</tr>
<tr><td>Nc1</td>
<td>The DCS shall ensure that error messages give the users specific instructions for recovery</td>
<td>Non-Functional</td>
<td>Ease of Use</td>
<td>Could</td>
<td>Implemented</td>
</tr>
<tr><td>Nc2</td>
<td>The DCS shall ensure that a users persistence data has an availability of 100%</td>
<td>Non-Functional</td>
<td>Availability</td>
<td>Could</td>
<td>Not Tested</td>
</tr>
<tr><td>Nw1</td>
<td>The DCS shall support 100 concurrent sessions</td>
<td>Non-Functional</td>
<td>Capacity</td>
<td>Would</td>
<td>Not Tested</td>
</tr>
<tr><td>Nw2</td>
<td>The DCS shall be easily scalable to accommodate more concurrent users</td>
<td>Non-Functional</td>
<td>Capacity</td>
<td>Would</td>
<td>Not Implemented</td>
</tr>
</tbody></table>

<br><a class="btn-resp" href="#top">^ Back to Top</a>

<hr>

<a class="anchor" id="performance"></a>

## Performance Testing

To make sure the web application performs well with reasonably sized datasets, we tested the final system with a series of artificially generated datasets, ranging from less than 1MB in size to over 100MB. We tested 5 main functionalities of the system, including:

* Upload the dataset
* Impute missing values in a column (with 95.8% values missing) with the column mode
* Perform a find and replace operation using regex on a column
* Generate a scatter plot between 2 numerical columns
* Split a column into 3 columns using a delimiter

We measured the time the system takes to perform each of these operations using a stopwatch.

Specification of the machine used for testing:

* MacBook Pro 15-inch (Late 2013)
* 2.0 GHz (i7-4750HQ) quad-core Intel Core i7 Haswell with 6 MB on-chip L3 and 128 MB L4 cache (Crystalwell)
* 8 GB built-in onboard RAM
* Intel Iris Pro 5200 Graphics with DDR3L SDRAM shared with main memory
* Running on Google Chrome 50

### Results

<div class="imgCapContainer">
    <img src="{{site.baseurl}}/assets/performance1.png" alt="result1"
     class="titleImage wideImage">
     <br>
     Results of performance testing.
</div>

<div class="imgCapContainer">
    <img src="{{site.baseurl}}/assets/performance2.png" alt="result2"
     class="titleImage wideImage">
     <br>
     The effect of file size on the time taken by each operation.
</div>

**N.B.** Most operations performed by the system works on *columns* rather than *rows* of a dataset so the performance of the system depends more on the number of rows in the dataset.

The results were not surprising to us as most basic operations performs well enough even with a large file size. Some operations are resource intensive in its nature and there's little we can do to improve their performance, but they still work well with smaller datasets. When compared to other software such as OpenRefine and Excel, our system performs as well if not better on some of the features. For example, both OpenRefine and Excel failed to load the 106.8MB file while our system loaded it under 30 seconds. Overall we are satisfied by the performance of our system.

<br><a class="btn-resp" href="#top">^ Back to Top</a>

<hr>

<a class="anchor" id="uat"></a>

## User Acceptance Testing (UAT)

This is the last phase of the software engineering process. During UAT the completed software is tested by potential users of the system to ensure it can handle required tasks in real-world scenarios. In order to carry out UAT we designed several test cases which covered most of our key requirements. We then presented these test cases to our client who in turn decided to pass them on to potential users of the system to carry out the UAT. Our client informed us that they will send us the feedback they may receive regarding bugs and usability. However it is worth mentioning that our clients were extremely pleased with each individual feature offered by the system as well as the overall User Experience.

<br><a class="btn-resp" href="#top">^ Back to Top</a>
