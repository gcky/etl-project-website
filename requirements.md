---
layout: default
title: Requirements | ETL for Data Science
---

# Requirements and Use Cases

Click the buttons below to jump to the corresponding section.

<a class="btn-resp" href="#initial-requirements">1. Initial Requirements</a>
<a class="btn-resp" href="#requirements-gathering">2. Requirements Gathering</a>
<a class="btn-resp" href="#moscow-requirements">3. MoSCoW Requirements</a>
<a class="btn-resp" href="#use-cases">4. Use-Cases</a>

<a class="anchor" id="initial-requirements"></a>

## Initial Requirements

The implementation should include a functional web-based UI for the key features, including data loading, data analysis and visualisation. Sample data will be provided. All or parts of all of the project will be made available as an open-source project.

<br><a class="btn-resp" href="#top">^ Back to Top</a>

<hr>

<a class="anchor" id="requirements-gathering"></a>

## Requirements Gathering

The requirements should take into consideration feedback from the following stakeholders: 

* The Seldon team
* Selected Seldon enterprise customers (i.e. the customer providing a data sample)
* Surveys to the wider Seldon developer community

### Questionnaire

A questionnaire was devised in the early stages of the project, intended for Seldon customers and developer community. The aim of this questionnaire is to identify the general needs and desires of potential users in a data analysis program.

<br><a class="btn-resp" href="#top">^ Back to Top</a>

<hr>

<a class="anchor" id="moscow-requirements"></a>

## MoSCoW Requirements

This is a list of all the requirements as agreed with our client. These requirements are subject to change over the course of the development phase of this project.

<table class="table table-bordered table-hover table-condensed">
<tbody><tr class="headerRow"><td>ID</td>
<td width="60%">Requirement</td>
<td>Type</td>
<td>Category</td>
<td>Priority</td>
</tr>
<tr><td class="seperator" colspan="5">UI/UX</td>
</tr>
<tr><td>Um1</td>
<td>The DCS shall display the user imported dataset as a spreadsheet/table.</td>
<td>Functional</td>
<td>UI/UX</td>
<td>Must</td>
</tr>
<tr><td>Uc1</td>
<td>The DCS shall display all unresolved cleanliness issues</td>
<td>Functional</td>
<td>UI/UX</td>
<td>Could</td>
</tr>
<tr><td>Uc2</td>
<td>The DCS shall offer the user a choice between a pure GUI interface and a notebook style interface.</td>
<td>Functional</td>
<td>UI/UX</td>
<td>Could</td>
</tr>
<tr><td>Uc3</td>
<td>The DCS shall support persistence of user sessions.</td>
<td>Functional</td>
<td>UI/UX</td>
<td>Could</td>
</tr>
<tr><td>Uc4</td>
<td>The DCS shall support partial loading of rows in datasets.</td>
<td>Functional</td>
<td>UI/UX</td>
<td>Could</td>
</tr>
<tr><td>Uw1</td>
<td>The DCS shall allow multiple users to collaborate showing changes in real time</td>
<td>Functional</td>
<td>UI/UX</td>
<td>Would</td>
</tr>
<tr><td>Uw2</td>
<td>The DCS shall compute a &quot;messiness&quot; score.</td>
<td>Functional</td>
<td>UI/UX</td>
<td>Would</td>
</tr>
<tr><td class="seperator" colspan="5">Data Loading</td>
</tr>
<tr><td>Lm1</td>
<td>The DCS shall support loading of user-uploaded CSV files. </td>
<td>Functional</td>
<td>Data Loading</td>
<td>Must</td>
</tr>
<tr><td>Lm2</td>
<td>The DCS shall allow users to specify variable names and types.</td>
<td>Functional</td>
<td>Data Loading</td>
<td>Must</td>
</tr>
<tr><td>Ls1</td>
<td>The DCS shall support a Date variable type.</td>
<td>Functional</td>
<td>Data Loading</td>
<td>Should</td>
</tr>
<tr><td>Ls2</td>
<td>The DCS shall parse dates with a user-provided format string.</td>
<td>Functional</td>
<td>Data Loading</td>
<td>Should</td>
</tr>
<tr><td>Lc1</td>
<td>The DCS shall support loading of user-uploaded structured file formats (JSON, XML).</td>
<td>Functional</td>
<td>Data Loading</td>
<td>Could</td>
</tr>
<tr><td>Lc2</td>
<td>The DCS shall support partial loading of columns in datasets.</td>
<td>Functional</td>
<td>Data Loading</td>
<td>Could</td>
</tr>
<tr><td>Lw1</td>
<td>The DCS shall support loading user-uploaded unstructured data text files. </td>
<td>Functional</td>
<td>Data Loading</td>
<td>Would</td>
</tr>
<tr><td>Lw2</td>
<td>The DCS shall support parsing of unstructured file format.</td>
<td>Functional</td>
<td>Data Loading</td>
<td>Would</td>
</tr>
<tr><td>Lw3</td>
<td>The DCS shall support loading of data files over network.</td>
<td>Functional</td>
<td>Data Loading</td>
<td>Would</td>
</tr>
<tr><td>Lw4</td>
<td>The DCS shall load asynchronously. </td>
<td>Functional</td>
<td>Data Loading</td>
<td>Would</td>
</tr>
<tr><td>Lw5</td>
<td>The DCS shall support loading of data streams.</td>
<td>Functional</td>
<td>Data Loading</td>
<td>Would</td>
</tr>
<tr><td>Lw6</td>
<td>The DCS shall support an Email variable type.</td>
<td>Functional</td>
<td>Data Loading</td>
<td>Would</td>
</tr>
<tr><td>Lw7</td>
<td>The DCS shall intelligently guess variable types. </td>
<td>Functional</td>
<td>Data Loading</td>
<td>Would</td>
</tr>
<tr><td class="seperator" colspan="5">Data Viewing</td>
</tr>
<tr><td>Xs1</td>
<td>The DCS shall support sorting of rows by user-specified column</td>
<td>Functional</td>
<td>Data Viewing</td>
<td>Should</td>
</tr>
<tr><td>Xs2</td>
<td>The DCS shall support searching datasets with a keyword</td>
<td>Functional</td>
<td>Data Viewing</td>
<td>Should</td>
</tr>
<tr><td>Xc1</td>
<td>The DCS shall support querying datasets with SQL</td>
<td>Functional</td>
<td>Data Viewing</td>
<td>Could</td>
</tr>
<tr><td class="seperator" colspan="5">Data Cleaning</td>
</tr>
<tr><td>Cm1</td>
<td>The DCS shall support removing rows as a universal cleaning operation </td>
<td>Functional</td>
<td>Data Cleaning</td>
<td>Must</td>
</tr>
<tr><td>Cm2</td>
<td>The DCS shall support inserting user-specified values as a universal cleaning operation </td>
<td>Functional</td>
<td>Data Cleaning</td>
<td>Must</td>
</tr>
<tr><td>Cm3</td>
<td>The DCS shall show rows with invalid numbers in specified column</td>
<td>Functional</td>
<td>Data Cleaning</td>
<td>Must</td>
</tr>
<tr><td>Cm4</td>
<td>The DCS shall show rows with missing values in specified column</td>
<td>Functional</td>
<td>Data Cleaning</td>
<td>Must</td>
</tr>
<tr><td>Cm5</td>
<td>The DCS shall support cleaning of missing values by inserting an average</td>
<td>Functional</td>
<td>Data Cleaning</td>
<td>Must</td>
</tr>
<tr><td>Cm6</td>
<td>The DCS shall support cleaning of missing values by filling with the most recent value</td>
<td>Functional</td>
<td>Data Cleaning</td>
<td>Must</td>
</tr>
<tr><td>Cm7</td>
<td>The DCS shall support cleaning of missing values by interpolation</td>
<td>Functional</td>
<td>Data Cleaning</td>
<td>Must</td>
</tr>
<tr><td>Cs1</td>
<td>The DCS shall show rows where Date parsing failed</td>
<td>Functional</td>
<td>Data Cleaning</td>
<td>Should</td>
</tr>
<tr><td>Cs2</td>
<td>The DCS shall show duplicate rows</td>
<td>Functional</td>
<td>Data Cleaning</td>
<td>Should</td>
</tr>
<tr><td>Cs3</td>
<td>The DCS shall provide the option to ignore outliers</td>
<td>Functional</td>
<td>Data Cleaning</td>
<td>Should</td>
</tr>
<tr><td>Cs4</td>
<td>The DCS shall provide the option to filter rows using regular expression</td>
<td>Functional</td>
<td>Data Cleaning</td>
<td>Should</td>
</tr>
<tr><td>Cs5</td>
<td>The DCS shall support data normalisation and standarisation</td>
<td>Functional</td>
<td>Data Cleaning</td>
<td>Should</td>
</tr>
<tr><td>Cc1</td>
<td>The DCS shall provide the option to group multiple text representation of the same entity and replace them with a single value</td>
<td>Functional</td>
<td>Data Cleaning</td>
<td>Could</td>
</tr>
<tr><td>Cc2</td>
<td>The DCS shall fix escaped HTML strings</td>
<td>Functional</td>
<td>Data Cleaning</td>
<td>Could</td>
</tr>
<tr><td>Cc3</td>
<td>The DCS shall show values that are not found in English dictionary </td>
<td>Functional</td>
<td>Data Cleaning</td>
<td>Could</td>
</tr>
<tr><td>Cw1</td>
<td>The DCS shall show rows where Email parsing failed</td>
<td>Functional</td>
<td>Data Cleaning</td>
<td>Would</td>
</tr>
<tr><td class="seperator" colspan="5">Data Analysis</td>
</tr>
<tr><td>Am1</td>
<td>The DCS shall show the unique values and their count of every column of the dataset</td>
<td>Functional</td>
<td>Data Analysis</td>
<td>Must</td>
</tr>
<tr><td>Am2</td>
<td>The DCS shall show the mean, median, mode of columns with numerical data</td>
<td>Functional</td>
<td>Data Analysis</td>
<td>Must</td>
</tr>
<tr><td>Am3</td>
<td>The DCS shall show the max and min values of columns with numerical data</td>
<td>Functional</td>
<td>Data Analysis</td>
<td>Must</td>
</tr>
<tr><td>Am4</td>
<td>The DCS shall show the range and standard deviation of columns with numerical data</td>
<td>Functional</td>
<td>Data Analysis</td>
<td>Must</td>
</tr>
<tr><td>As1</td>
<td>The DCS shall show text analysis such as most frequent word for string type data</td>
<td>Functional</td>
<td>Data Analysis</td>
<td>Should</td>
</tr>
<tr><td class="seperator" colspan="5">Data Visualisation</td>
</tr>
<tr><td>Vm1</td>
<td>The DCS shall be able to visualise data using histograms</td>
<td>Functional</td>
<td>Data Visualisation</td>
<td>Must</td>
</tr>
<tr><td>Vm2</td>
<td>The DCS shall be able to visualise data using bar charts</td>
<td>Functional</td>
<td>Data Visualisation</td>
<td>Must</td>
</tr>
<tr><td>Vm3</td>
<td>The DCS shall be able to visualise data using line charts</td>
<td>Functional</td>
<td>Data Visualisation</td>
<td>Must</td>
</tr>
<tr><td>Vs1</td>
<td>The DCS shall be able to visualise data using scatter plots</td>
<td>Functional</td>
<td>Data Visualisation</td>
<td>Should</td>
</tr>
<tr><td>Vs2</td>
<td>The DCS shall be able to visualise data using time-series plots</td>
<td>Functional</td>
<td>Data Visualisation</td>
<td>Should</td>
</tr>
<tr><td>Vs3</td>
<td>The DCS shall be able to visualise data using pie charts</td>
<td>Functional</td>
<td>Data Visualisation</td>
<td>Should</td>
</tr>
<tr><td>Vc1</td>
<td>The DCS shall provide the option to export graphs to image</td>
<td>Functional</td>
<td>Data Visualisation</td>
<td>Could</td>
</tr>
<tr><td>Vw1</td>
<td>The DCS shall be able to visualise data using regression matricies</td>
<td>Functional</td>
<td>Data Visualisation</td>
<td>Would</td>
</tr>
<tr><td class="seperator" colspan="5">Others</td>
</tr>
<tr><td>Nm1</td>
<td>The DCS shall use a browser as its user interface</td>
<td>Non-Functional</td>
<td>Compliance to Standards</td>
<td>Must</td>
</tr>
<tr><td>Nm2</td>
<td>The DCS shall have an uptime of 99%</td>
<td>Non-Functional</td>
<td>Availability</td>
<td>Must</td>
</tr>
<tr><td>Nm3</td>
<td>The DCS shall support the latest versions of Internet Explorer, Chrome, Firefox</td>
<td>Non-Functional</td>
<td>Performance</td>
<td>Must</td>
</tr>
<tr><td>Nm4</td>
<td>The DCS shall be easily installable by an untrained user with the help of documentation</td>
<td>Non-Functional</td>
<td>Deployment</td>
<td>Must</td>
</tr>
<tr><td>Ns1</td>
<td>The DCS shall ensure that a potential user is able to carry out any task in 5 minutes</td>
<td>Non-Functional</td>
<td>Ease Of Use</td>
<td>Should</td>
</tr>
<tr><td>Ns2</td>
<td>The DCS shall have a user interface that has a user satisfaction rate of 90%</td>
<td>Non-Functional</td>
<td>Ease of Use</td>
<td>Should</td>
</tr>
<tr><td>Nc1</td>
<td>The DCS shall ensure that a user is able to complete all task in 5 clicks</td>
<td>Non-Functional</td>
<td>Ease of Use</td>
<td>Could</td>
</tr>
<tr><td>Nc2</td>
<td>The DCS shall ensure that error messages give the users specific instructions for recovery</td>
<td>Non-Functional</td>
<td>Ease of Use</td>
<td>Could</td>
</tr>
<tr><td>Nc3</td>
<td>The DCS shall ensure that a users persistence data has an availability of 100%</td>
<td>Non-Functional</td>
<td>Availability</td>
<td>Could</td>
</tr>
<tr><td>Nw1</td>
<td>The DCS shall support 100 concurrent sessions</td>
<td>Non-Functional</td>
<td>Capacity</td>
<td>Would</td>
</tr>
<tr><td>Nw2</td>
<td>The DCS shall be easily scalable to accommodate more concurrent users</td>
<td>Non-Functional</td>
<td>Capacity</td>
<td>Would</td>
</tr>
</tbody></table>

<br><a class="btn-resp" href="#top">^ Back to Top</a>

<hr>

<a class="anchor" id="use-cases"></a>

## Use-Cases

<table class="table table-bordered table-hover table-condensed">
<tbody>
<tr class="seperator"><td>Use Case ID</td>
<td>Use Case Name</td>
</tr>
<tr><td>UC1</td>
<td>LoadFile</td>
</tr>
<tr><td>UC2</td>
<td>DefineVariableTypes</td>
</tr>
<tr><td>UC3</td>
<td>DeleteSelectedRows</td>
</tr>
<tr><td>UC4</td>
<td>ChangeValueInCell</td>
</tr>
<tr><td>UC5</td>
<td>DisplayRowsWithMissingValues</td>
</tr>
<tr><td>UC6</td>
<td>FillMissingValuesWithAverage</td>
</tr>
<tr><td>UC7</td>
<td>ViewAnalysisOfColumn</td>
</tr>
<tr><td>UC8</td>
<td>DisplayUniqueValues</td>
</tr>
<tr><td>UC9</td>
<td>CreateVisualisation</td>
</tr>
<tr><td>UC10</td>
<td>ChangeVisualisation</td>
</tr>
<tr><td>UC11</td>
<td>DispalyDuplicateRows</td>
</tr>
<tr><td>UC12</td>
<td>SortValuesInColumns</td>
</tr>
<tr><td>UC13</td>
<td>QueryDataWithKeyword</td>
</tr>
<tr><td>UC14</td>
<td>DefineConstraintsOnRange</td>
</tr>
<tr><td>UC15</td>
<td>EnterCodeInNotebook</td>
</tr>
<tr><td>UC16</td>
<td>ClusterData</td>
</tr>
</tbody>
</table>

<br>

<table><tbody>
<tr><td>USE CASE</td>
<td>LoadFile</td>
</tr>
<tr><td>ID</td>
<td>UC1</td>
</tr>
<tr><td>BRIEF DESCRIPTION</td>
<td>A user attempts to load a file on the system</td>
</tr>
<tr><td>PRIMARY ACTORS</td>
<td>User</td>
</tr>
<tr><td>SECONDARY ACTORS</td>
<td>None</td>
</tr>
<tr><td>PRECONDITIONS</td>
<td>None</td>
</tr>
<tr><td>MAIN FLOW</td>
<td>1. The use case is initiated when the user opens the web app in a browser <br> 2. The system displays a file chooser <br> 3. The user selects a file to upload from a local directory <br> 4. The user selects the upload option</td>
</tr>
<tr><td>POSTCONDITIONS</td>
<td>The file is uploaded into the workspace</td>
</tr>
<tr><td>ALTERNATIVE FLOWS</td>
<td>None</td>
</tr>
</tbody>
</table>

<br>

<table>
<tbody>
<tr><td>USE CASE</td>
<td>DefineVariableTypes</td>
</tr>
<tr><td>ID</td>
<td>UC2</td>
</tr>
<tr><td>BRIEF DESCRIPTION</td>
<td>The user defines a name and a type for each variable</td>
</tr>
<tr><td>PRIMARY ACTORS</td>
<td>User</td>
</tr>
<tr><td>SECONDARY ACTORS</td>
<td>None</td>
</tr>
<tr><td>PRECONDITIONS</td>
<td>The user has selected a file to be uploaded</td>
</tr>
<tr><td>MAIN FLOW</td>
<td>1. The use case is initiated when the user selects a file to be uploaded <br> 2. The system displays a list of all the variable names based on the first value of every column <br> 3. The user selects the name(s) they wish to edit, and enters a new name followed by the next button <br> 4. The system displays a list of the variable names preceded by the type <br> 5. The user selects the appropriate type for each variable</td>
</tr>
<tr><td>POSTCONDITIONS</td>
<td>The type and names of the variables have been set</td>
</tr>
<tr><td>ALTERNATIVE FLOWS</td>
<td>None</td>
</tr>
</tbody>
</table>

<br>

<table>
<tbody>
<tr><td>USE CASE</td>
<td>DeleteSelectedRows</td>
</tr>
<tr><td>ID</td>
<td>UC3</td>
</tr>
<tr><td>BRIEF DESCRIPTION</td>
<td>The user selects on a row/rows to be deleted</td>
</tr>
<tr><td>PRIMARY ACTORS</td>
<td>User</td>
</tr>
<tr><td>SECONDARY ACTORS</td>
<td>None</td>
</tr>
<tr><td>PRECONDITIONS</td>
<td>A file has been uploaded to the system</td>
</tr>
<tr><td>MAIN FLOW</td>
<td>1. The user selects on multiple rows within the spreadsheet <br> 2. The system highlights all the selected rows <br> 3. The user selects the delete rows option in the sidebar</td>
</tr>
<tr><td>POSTCONDITIONS</td>
<td>The selected rows are deleted</td>
</tr>
<tr><td>ALTERNATIVE FLOWS</td>
<td>None</td>
</tr>
</tbody>
</table>

<br>

<table>
<tbody>
<tr><td>USE CASE</td>
<td>ChangeValueInCell</td>
</tr>
<tr><td>ID</td>
<td>UC4</td>
</tr>
<tr><td>BRIEF DESCRIPTION</td>
<td>The user updates the value of cells within the spreadsheet</td>
</tr>
<tr><td>PRIMARY ACTORS</td>
<td>User</td>
</tr>
<tr><td>SECONDARY ACTORS</td>
<td>None</td>
</tr>
<tr><td>PRECONDITIONS</td>
<td>A file has been uploaded to the system</td>
</tr>
<tr><td>MAIN FLOW</td>
<td>1. The user selects the cell to be updated <br> 2. The user types in the new value of the cell <br> 3. The system checks if the value entered conforms with the variable type <br> 4. The system displays the updated value in the cell</td>
</tr>
<tr><td>POSTCONDITIONS</td>
<td>The old value is replaced with the new value</td>
</tr>
<tr><td>ALTERNATIVE FLOWS</td>
<td>ValueEnteredDoesNotMatchType</td>
</tr>
<tr><td>ID</td>
<td>UC4.1</td>
</tr>
<tr><td>BRIEF DESCRIPTION</td>
<td>The value entered does not conform with the type of the variable</td>
</tr>
<tr><td>PRIMARY ACTORS</td>
<td>System (App)</td>
</tr>
<tr><td>SECONDARY ACTORS</td>
<td>None</td>
</tr>
<tr><td>PRECONDITIONS</td>
<td>The user enters a value that is of an incorrect type</td>
</tr>
<tr><td>MAIN FLOW</td>
<td>The alternative flow starts after step 3 of the main flow The system replaces the value of the updated cell with an N/A</td>
</tr>
<tr><td>POSTCONDITIONS</td>
<td>The value is replaced with N/A</td>
</tr>
</tbody>
</table>

<br>

<table>
<tbody>
<tr><td>USE CASE</td>
<td>DisplayRowsWithMissingValues</td>
</tr>
<tr><td>ID</td>
<td>UC5</td>
</tr>
<tr><td>BRIEF DESCRIPTION</td>
<td>The system displays all the rows in a particular column that have missing values</td>
</tr>
<tr><td>PRIMARY ACTORS</td>
<td>User</td>
</tr>
<tr><td>SECONDARY ACTORS</td>
<td>None</td>
</tr>
<tr><td>PRECONDITIONS</td>
<td>A file has been uploaded to the system</td>
</tr>
<tr><td>MAIN FLOW</td>
<td>1. The user selects a column in the spreadsheet <br> 2. The user selects the missing value option in the sidebar <br> 3. The system updates the spreadsheet to display only those rows consisting of missing values within the specified column</td>
</tr>
<tr><td>POSTCONDITIONS</td>
<td>The spreadsheet is updated</td>
</tr>
<tr><td>ALTERNATIVE FLOWS</td>
<td>None</td>
</tr>
</tbody>
</table>

<br>

<table>
<tbody>
<tr><td>USE CASE</td>
<td>FillMissingValuesWithAverage</td>
</tr>
<tr><td>ID</td>
<td>UC6</td>
</tr>
<tr><td>BRIEF DESCRIPTION</td>
<td>The user replaces all the missing values within a selected column using an average</td>
</tr>
<tr><td>PRIMARY ACTORS</td>
<td>User</td>
</tr>
<tr><td>SECONDARY ACTORS</td>
<td>None</td>
</tr>
<tr><td>PRECONDITIONS</td>
<td>A file has been uploaded to the system</td>
</tr>
<tr><td>MAIN FLOW</td>
<td>1. The user selects a column within the spreadsheet <br> 2. The user selects the replace missing values option in the sidebar <br> 3. The system displays a list consisting of the different averages depending on the type of column <br> 4. The user selects on the appropriate average, then selects the run option The system replaces all the missing values within the column with the chosen average</td>
</tr>
<tr><td>POSTCONDITIONS</td>
<td>The spreadsheet is updated</td>
</tr>
<tr><td>ALTERNATIVE FLOWS</td>
<td>None</td>
</tr>
</tbody>
</table>

<br>

<table>
<tbody>
<tr><td>USE CASE</td>
<td>ViewAnalysisOfColumn</td>
</tr>
<tr><td>ID</td>
<td>UC7</td>
</tr>
<tr><td>BRIEF DESCRIPTION</td>
<td>The system displays an analysis of each variable within the spreadsheet</td>
</tr>
<tr><td>PRIMARY ACTORS</td>
<td>User</td>
</tr>
<tr><td>SECONDARY ACTORS</td>
<td>None</td>
</tr>
<tr><td>PRECONDITIONS</td>
<td>A file has been uploaded to the system</td>
</tr>
<tr><td>MAIN FLOW</td>
<td>1. The user selects the analyse tab at the top <br> 2. The system carries out an analysis of each variable depending on its type <br> 3. The system displays the analysis of each variable in a table</td>
</tr>
<tr><td>POSTCONDITIONS</td>
<td>None</td>
</tr>
<tr><td>ALTERNATIVE FLOWS</td>
<td>None</td>
</tr>
</tbody>
</table>

<br>

<table>
<tbody>
<tr><td>USE CASE</td>
<td>DisplayUniqueValues</td>
</tr>
<tr><td>ID</td>
<td>UC8</td>
</tr>
<tr><td>BRIEF DESCRIPTION</td>
<td>The system displays a list of the frequency of values within a variable</td>
</tr>
<tr><td>PRIMARY ACTORS</td>
<td>User</td>
</tr>
<tr><td>SECONDARY ACTORS</td>
<td>None</td>
</tr>
<tr><td>PRECONDITIONS</td>
<td>File uploaded to system</td>
</tr>
<tr><td>MAIN FLOW</td>
<td>1. The use case is initiated when the user is in the analyse tab <br> 2. The system will display the analysis results of each variable in a table <br> 3. The user toggles the display unique value feature in the appropriate table <br> 4. The system displays the frequencies of all values within the selected variable</td>
</tr>
<tr><td>POSTCONDITIONS</td>
<td>None</td>
</tr>
<tr><td>ALTERNATIVE FLOWS</td>
<td>None</td>
</tr>
</tbody>
</table>

<br>

<table>
<tbody>
<tr><td>USE CASE</td>
<td>CreateVisualisation</td>
</tr>
<tr><td>ID</td>
<td>UC9</td>
</tr>
<tr><td>BRIEF DESCRIPTION</td>
<td>The user creates a visualisation by selecting a chart type followed by the variables</td>
</tr>
<tr><td>PRIMARY ACTORS</td>
<td>User</td>
</tr>
<tr><td>SECONDARY ACTORS</td>
<td>None</td>
</tr>
<tr><td>PRECONDITIONS</td>
<td>A file has been uploaded to the system</td>
</tr>
<tr><td>MAIN FLOW</td>
<td>1. The use case is initiated when the user selects the visualise option at the top The system displays a list of chart types and variable names <br> 2. The user selects the graph The system limits the number of variables a user is able to select depending on the chart <br> 3. The user selects the variable names <br> 4. The system displays the graph</td>
</tr>
<tr><td>POSTCONDITIONS</td>
<td>The system displays the graph that is generated</td>
</tr>
<tr><td>ALTERNATIVE FLOWS</td>
<td>None</td>
</tr>
</tbody>
</table>

<br>

<table>
<tbody>
<tr><td>USE CASE</td>
<td>ChangeVisualisation</td>
</tr>
<tr><td>ID</td>
<td>UC10</td>
</tr>
<tr><td>BRIEF DESCRIPTION</td>
<td>The user changes the type of chart used to display results</td>
</tr>
<tr><td>PRIMARY ACTORS</td>
<td>User</td>
</tr>
<tr><td>SECONDARY ACTORS</td>
<td>None</td>
</tr>
<tr><td>PRECONDITIONS</td>
<td>A chart is already generated</td>
</tr>
<tr><td>MAIN FLOW</td>
<td>1. The use case is initiated when the user has already generated a chart <br> 2. The system displays a list of chart types <br> 3. The user the chart type they wish to change to <br> 4. The system displays the new chart</td>
</tr>
<tr><td>POSTCONDITIONS</td>
<td>The new chart is displayed</td>
</tr>
<tr><td>ALTERNATIVE FLOWS</td>
<td>UnableToGenerateGraph</td>
</tr>
<tr><td>ID</td>
<td>UC10.1</td>
</tr>
<tr><td>BRIEF DESCRIPTION</td>
<td>The chosen chart supports a different number of variables to that previously selected</td>
</tr>
<tr><td>PRIMARY ACTORS</td>
<td>System</td>
</tr>
<tr><td>SECONDARY ACTORS</td>
<td>User</td>
</tr>
<tr><td>PRECONDITIONS</td>
<td>The user selects a chart that supports a different number of variables</td>
</tr>
<tr><td>MAIN FLOW</td>
<td>1. The alternate flow starts after step 3 of the main flow <br> 2. The system prompts the user to select an appropriate number of variables depending on the newly selected chart <br> 3. The user selects the variables <br> 4. The newly generated graph is displayed</td>
</tr>
<tr><td>POSTCONDITIONS</td>
<td>The new graph is displayed</td>
</tr>
</tbody>
</table>

<br>

<table>
<tbody>
<tr><td>USE CASE</td>
<td>DispalyDuplicateRows</td>
</tr>
<tr><td>ID</td>
<td>UC11</td>
</tr>
<tr><td>BRIEF DESCRIPTION</td>
<td>The system displays all rows within a column that have duplicate values</td>
</tr>
<tr><td>PRIMARY ACTORS</td>
<td>User</td>
</tr>
<tr><td>SECONDARY ACTORS</td>
<td>None</td>
</tr>
<tr><td>PRECONDITIONS</td>
<td>A file has been uploaded to the system The user is in the clean tab</td>
</tr>
<tr><td>MAIN FLOW</td>
<td>1. The user selects a column in the spreadsheet <br> 2. The user selects on the duplicate values option in the side bar <br> 3. The system groups together rows that have the same value in a particular column and displays this in the spreadsheet</td>
</tr>
<tr><td>POSTCONDITIONS</td>
<td>Rows with duplicate values are grouped together</td>
</tr>
<tr><td>ALTERNATIVE FLOWS</td>
<td>None</td>
</tr>
</tbody>
</table>

<br>

<table>
<tbody>
<tr><td>USE CASE</td>
<td>SortValuesInColumns</td>
</tr>
<tr><td>ID</td>
<td>UC12</td>
</tr>
<tr><td>BRIEF DESCRIPTION</td>
<td>The user sorts values in a particular column</td>
</tr>
<tr><td>PRIMARY ACTORS</td>
<td>User</td>
</tr>
<tr><td>SECONDARY ACTORS</td>
<td>None</td>
</tr>
<tr><td>PRECONDITIONS</td>
<td>A file has been uploaded to the system The user is in the clean tab</td>
</tr>
<tr><td>MAIN FLOW</td>
<td>1. The user selects a column <br> 2. The user selects the sort option in the sidebar <br> 3. The system displays a list of sorting techniques <br> 4. The user selects the sorting technique <br> 5. The system sorts the values in the variable according to the technique selected</td>
</tr>
<tr><td>POSTCONDITIONS</td>
<td>The column is sorted</td>
</tr>
<tr><td>ALTERNATIVE FLOWS</td>
<td>None</td>
</tr>
</tbody>
</table>

<br>

<table>
<tbody>
<tr><td>USE CASE</td>
<td>QueryDataWithKeyword</td>
</tr>
<tr><td>ID</td>
<td>UC13</td>
</tr>
<tr><td>BRIEF DESCRIPTION</td>
<td>The user is able to query data in a particular column using a keyword</td>
</tr>
<tr><td>PRIMARY ACTORS</td>
<td>User</td>
</tr>
<tr><td>SECONDARY ACTORS</td>
<td>None</td>
</tr>
<tr><td>PRECONDITIONS</td>
<td>A file has been uploaded to the system</td>
</tr>
<tr><td>MAIN FLOW</td>
<td>1. The user selects a column within the spreadsheet The user selects on the query data option in the sidebar <br> 2. The system displays a textbox in which the user can enter a keyword <br> 3. The user enters the keyword <br> 4. The system updates the spreadsheet to display only those rows which contain the keyword in the chosen variable field.</td>
</tr>
<tr><td>POSTCONDITIONS</td>
<td>The spreadsheet is updated to display rows that match</td>
</tr>
<tr><td>ALTERNATIVE FLOWS</td>
<td>None</td>
</tr>
</tbody>
</table>

<br>

<table>
<tbody>
<tr><td>USE CASE</td>
<td>DefineConstraintsOnRange</td>
</tr>
<tr><td>ID</td>
<td>UC14</td>
</tr>
<tr><td>BRIEF DESCRIPTION</td>
<td>The user is able to define constraints on the range of a variable</td>
</tr>
<tr><td>PRIMARY ACTORS</td>
<td>User</td>
</tr>
<tr><td>SECONDARY ACTORS</td>
<td>None</td>
</tr>
<tr><td>PRECONDITIONS</td>
<td>A file has been uploaded to the system</td>
</tr>
<tr><td>MAIN FLOW</td>
<td>1. The user selects a column in the spreadsheet <br> 2. The user selects the define range option <br> 3. The system displays two checkboxes <br> 4. The user enters the upper and lower bound of the range in the textboxes <br> 5. The system updates the spreadsheet to displays only those rows where the value of the variable is within the defined range</td>
</tr>
<tr><td>POSTCONDITIONS</td>
<td>None</td>
</tr>
<tr><td>ALTERNATIVE FLOWS</td>
<td>InvalidRange</td>
</tr>
<tr><td>ID</td>
<td>UC14.1</td>
</tr>
<tr><td>BRIEF DESCRIPTION</td>
<td>The range entered does not conform with the type of the variable</td>
</tr>
<tr><td>PRIMARY ACTORS</td>
<td>System</td>
</tr>
<tr><td>SECONDARY ACTORS</td>
<td>User</td>
</tr>
<tr><td>PRECONDITIONS</td>
<td>The range entered does not conform with the type</td>
</tr>
<tr><td>MAIN FLOW</td>
<td>1. The alternate flow starts after step 4 of the main flow <br> 2. The system displays a message that the values entered are of a different type <br> 3. The system provides the user with an option to enter the range again or close the feature</td>
</tr>
<tr><td>POSTCONDITIONS</td>
<td>None</td>
</tr>
</tbody>
</table>

<br>

<table>
<tbody>
<tr><td>USE CASE</td>
<td>EnterCodeInNotebook</td>
</tr>
<tr><td>ID</td>
<td>UC15</td>
</tr>
<tr><td>BRIEF DESCRIPTION</td>
<td>The user enters code snippets in a notebook</td>
</tr>
<tr><td>PRIMARY ACTORS</td>
<td>User</td>
</tr>
<tr><td>SECONDARY ACTORS</td>
<td>None</td>
</tr>
<tr><td>PRECONDITIONS</td>
<td>None</td>
</tr>
<tr><td>MAIN FLOW</td>
<td>1. The user selects on the notebook option <br> 2. The system displays a notebook interface <br> 3. The user enters snippets of code in the notebook <br> 4. The user selects the run option The system updates the spreadsheet</td>
</tr>
<tr><td>POSTCONDITIONS</td>
<td>The spreadsheet is updated</td>
</tr>
<tr><td>ALTERNATIVE FLOWS</td>
<td>None</td>
</tr>
</tbody>
</table>

<br>

<table>
<tbody>
<tr><td>USE CASE</td>
<td>ClusterData</td>
</tr>
<tr><td>ID</td>
<td>UC16</td>
</tr>
<tr><td>BRIEF DESCRIPTION</td>
<td>the user clusters data in a particular column</td>
</tr>
<tr><td>PRIMARY ACTORS</td>
<td>User</td>
</tr>
<tr><td>SECONDARY ACTORS</td>
<td>None</td>
</tr>
<tr><td>PRECONDITIONS</td>
<td>A file has been uploaded to the system</td>
</tr>
<tr><td>MAIN FLOW</td>
<td>1. The user selects a column in the spreadsheet <br> 2. The user clicks on the cluster option in the sidebar <br> 3. The system groups all similar values within the column and displays this in the spreadsheet</td>
</tr>
<tr><td>POSTCONDITIONS</td>
<td>The spreadsheet is updated</td>
</tr>
<tr><td>ALTERNATIVE FLOWS</td>
<td>none</td>
</tr>
</tbody></table>

<br><a class="btn-resp" href="#top">^ Back to Top</a>