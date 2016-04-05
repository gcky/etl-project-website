---
layout: docs
title: User Documentation | Willow
---

<div class="btn btn-alert">
This page is a work-in-progress, some descriptions may be incomplete/inaccurate. If you have any queries, please contact the team via our GitHub repo.
</div>

<a class="anchor" id="install"></a>

# Installing and Running Willow

<div class="tableOfContents">
    <ol>
        <li><a href="#install-requirements">System Requirements</a></li>
        <li><a href="#install-tungsten">Installing Willow</a></li>
        <li><a href="#install-run">Running Willow</a>
            <ol type="a">
                <li><a href="#install-run-start">Start</a></li>
                <li><a href="#install-run-shut">Shut Down</a></li>
            </ol>
        </li>
        <li><a href="#install-uninstall">Uninstall Willow</a></li>
    </ol>
</div>

<a class="anchor" id="install-requirements"></a>

## System Requirements

- Operating System: Mac OS X 10.7+, Windows 7+, Linux
- Memory: 4GB+
- Browser: Chrome 45+, Safari 9+, Firefox 42+, Edge 25+, IE 11+ (JavaScript Enabled)
- VirtualBox and Vagrant installed

<a class="anchor" id="install-tungsten"></a>

## Installing Willow

1. Install **VirtualBox** if not installed already.
  - Go to the [download page](https://www.virtualbox.org/wiki/Downloads).
  - Follow instructions to install VirtualBox.
2. Install **Vagrant** if not installed already.
  - Go to the [download page](https://www.vagrantup.com/downloads.html).
  - Follow instructions to install Vagrant.
3. Create a directory for Willow and make it the current directory.
  - `mkdir willow`
  - `cd willow`
4. Download the [Willow Vagrantfile](http://students.cs.ucl.ac.uk/2015/group19/assets/file/Vagrantfile) and put it in the directory.
5. Start up the vagrant instance of the box.
  - `vagrant up`

<a class="anchor" id="install-run"></a>

## Running Willow

<a class="anchor" id="install-run-start"></a>

### Start

To start Willow, open the terminal (Mac) or command prompt (Windows), set the current directory to your Willow folder. Enter and execute `vagrant up`. Open the web browser and navigate to `localhost:5000`

<a class="anchor" id="install-run-shut"></a>

### Shut down

To shut down Willow, go to the terminal/command prompt, make sure the current directory is your Willow folder. Enter and execute `vagrant halt`.

<a class="anchor" id="install-uninstall"></a>

## Uninstall Willow

To uninstall Willow, simply delete your Willow directory. You will not be able to retrieve any previously uploaded datasets once you delete that directory. Refer to VirtualBox and Vagrant website for their uninstallation instructions.

<br>
<hr>
<a class="anchor" id="load"></a>

# Data Uploading and Downloading

<div class="tableOfContents">
    <ol>
        <li><a href="#load-upload">Uploading Data</a>
            <ol type="a">
                <li><a href="#load-upload-largeFiles">Large Files</a></li>
                <li><a href="#load-upload-commonIssues">Common Issues</a></li>
            </ol>
        </li>
        <li><a href="#load-download">Saving/Downloading Data</a></li>
    </ol>
</div>

<a class="anchor" id="load-upload"></a>

## Uploading Data

You need to first upload your data into Willow in order to perform any operations. Uploading a dataset creates a new Willow project. Unlike common web services, *uploading* a file in Willow actually stores the project locally on your computer and **not** on the internet. This means that Willow works even if you're offline! Willow currently supports **CSV**, **JSON**, **XLS**, and **XLSX** formatted data files.

When you access Willow using the appropriate address in your web browser, you will be directed to the Upload page. To upload a new file, click the gray box in the middle. This will open a file explorer, simply select the file you want and click *Open*. Alternatively, you can select a file by dragging the file inside the gray box. Click *Upload* to upload the selected file. If the upload is successful, you will be directed to the clean tab in main page.

<a class="anchor" id="load-upload-largeFiles"></a>

### Large Files

If you select a large file to upload, the advanced options section will expand automatically and warn you about potential performance issues. This is because even with the optimisations we have implemented in Willow for dealing with large datasets, its performance will unavoidably degrade as the file size increases.

In this situation, you can choose to upload your file anyway. However, expect slower performances from Willow. Alternatively, if you don't need all of the data in the file, you can select a random sample of your dataset by specifying a percentage (0, 100] under *Advanced Options*. You can also select a seed so you can retrieve the same sample again in the future.

To ensure that you have a good experience with Willow, it is recommended that you only upload files that are less than **100MB**.

<a class="anchor" id="load-upload-commonIssues"></a>

### Common Issues

#### Comments at the start of the file

- Some CSV/XLSX files have comments at the start of the file which are not part of the dataset. While Willow may accept the file, the resulting data structure will likely not to be correct. Luckily, under *Advanced Options*, you can specify the number of initial lines to ignore when uploading your file. If you do so, Willow will skip those lines when parsing your file.

#### Invalid formats

- While Willow is a great tool for cleaning datasets, it wasn't built for dealing with invalid data files. However, it will make its best attempt at parsing your file by **removing** invalid records. If Willow was not able to parse your file, you will have to fix them before being able to upload them into Willow.

#### Text encoding issues

- Text encoding discrepancies may result in Willow not accepting your file. Willow works in **UTF-8**, while it will do its best to detect the encoding of your file using the excellent [chardet](https://chardet.github.io/) library and convert it to UTF-8, it doesn't always succeed. In these cases, you will have to convert the file yourself before uploading it again.

<a class="anchor" id="load-download"></a>

## Saving/Downloading Data

After you have finished operating on the data, you can download it back in **CSV** or **JSON** formats. To do this, simply click on the <i class="material-icons md-16">save</i> button on the right of the top bar. You may be able to access a previously uploaded dataset by going to the same URL as the one generated when the data was first uploaded. However, this is **not guaranteed** and it is recommended that you save your dataset as a CSV or JSON file between sessions.

<br>
<hr>
<a class="anchor" id="view"></a>

# Data Viewing

After Willow has successfully parsed your data file, you will be directed to the **Transform** tab in the main page. The Transform tab consists of two parts, the toolbar on the right and the data table on the left.

<div class="tableOfContents">
    <ol>
        <li><a href="#view-layout">Interface</a>
            <ol type="a">
                <li><a href="#view-layout-dataTable">Data Table</a></li>
                <li><a href="#view-layout-toolbar">Toolbar</a></li>
            </ol>
        </li>
        <li>Filter
            <ol type="a">
                <li>Duplicates</li>
                <li>Missing/Invalid Values</li>
                <li>Outliers</li>
            </ol>
        </li>
        <li>Sort</li>
        <li>Search</li>
    </ol>
</div>

<a class="anchor" id="view-layout"></a>

## Interface

<a class="anchor" id="view-layout-dataTable"></a>

### Data Table

The data table is where your dataset is displayed and works similarly to spreadsheets software such as Excel. You can select cells by clicking on them; select multiple cells by dragging; and select entire column or row by clicking on the column or row headers. Initially, the table will show the first 10 columns and first 50 rows and you can navigate between these rows by scrolling inside the table.

<img class="screenshot" src="assets/product/transform.jpg" width="100%">

The bar beneath the table (bottom bar) has 2 modes, you can toggle between them by clicking on the <i class="material-icons md-16">tune</i> button on the left side of the bar. The first and default mode is table navigation. As mentioned, by default, the table will show the first 10 columns and first 50 rows; you can change which columns/rows to show by editing the values in this bar. The table can show a maximum of 20 columns and 500 rows at once.

The second mode is quick inspect. This shows 3 properties of the column that is currently selected, the column data type, the column mode, and the number of missing/invalid values in the column.

<a class="anchor" id="view-layout-toolbar"></a>

### Toolbar

The toolbar is where you will perform all cleaning and transformation operations. The toolbar has 3 sections, inspect, view, and operate; you can switch between them by clicking on their tabs. The Inspect section shows you the various properties and statistics of the currently selected column. The View sections lets you set filters to what is shown on the data table, and also search through the dataset. The Operate section lets you perform the various operations. These operations are separated into cards and they will show according to your current table selection, click the arrow on the right to expand these cards.

<br>
<hr>
<a class="anchor" id="clean"></a>

# Data Cleaning and Transformation

After Willow has successfully parsed your data file, you will be directed to the **Transform** tab in the main page. The Transform tab allows you to perform various data cleaning and transformation operations that Willow offers.

<div class="tableOfContents">
    <ol>
        <li><a href="#clean-edit-column">Edit Column</a>
            <ol type="a">
                <li><a href="#clean-edit-column-date">Date Format String</a></li>
                <li><a href="#clean-edit-column-delete">Delete Column and Dealing with Empty Strings</a></li>
            </ol>
        </li>
        <li><a href="#clean-edit-row">Edit Row</a></li>
        <li><a href="#clean-edit-cell">Edit Cell</a></li>
        <li><a href="#clean-column-operations">Column Operations</a>
            <ol type="a">
              <li><a href="#clean-column-operations-duplicate">Duplicate Column</a></li>
              <li><a href="#clean-column-operations-split">Split Column</a></li>
              <li><a href="#clean-column-operations-combine">Combine Columns</a></li>
            </ol>
        </li>
        <li><a href="#clean-missing-data">Missing Data</a>
            <ol type="a">
              <li><a href="#clean-missing-data-average">Impute With Column Average</a></li>
              <li><a href="#clean-missing-data-neighboring">Impute With Neighboring Valid Value</a></li>
              <li><a href="#clean-missing-data-interpolation">Impute Using Interpolation</a></li>
              <li><a href="#clean-missing-data-custom">Impute With Custom Value</a></li>
              <li><a href="#clean-missing-data-delete">Delete Entire Row</a></li>
            </ol>
        </li>
        <li><a href="#clean-discretization">Discretization & Quantiling</a></li>
        <li><a href="#clean-feature-scaling">Feature Scaling</a>
          <ol type="a">
              <li><a href="#clean-feature-scaling-minmax">Min-Max Scaling</a></li>
              <li><a href="#clean-feature-scaling-standardize">Standardization</a></li>
            </ol>
        </li>
        <li><a href="#clean-feature-encoding">Categorical Feature Encoding</a></li>
        <li><a href="#clean-custom-transformation">Custom Transformations</a>
            <ol type="a">
              <li><a href="#clean-custom-transformation-find-replace">Find & Replace</a></li>
              <li><a href="#clean-custom-transformation-batch">Batch Replacement Queue</a></li>
            </ol>
        </li>
        <li><a href="#clean-danger-zone"><em>Highway to the Danger Zone</em></a></li>
    </ol>
</div>

<a class="anchor" id="clean-edit-column"></a>

## Edit Column

When you select one whole column, the *Edit Column* card will appear under the View section. In this card, you can change the column name and data type.

<div class="btn btn-alert">
<i class="material-icons md-16">error_outline</i> It is <strong>not</strong> recommended to have duplicate column names.
</div>

Which data types you will be allowed to change your column to will depend on the current type. You can check the current type in quick inspect.

<table>
<tbody><tr class="headerRow"><td>Current Type</td>
<td width="60%">Possible Options</td>
</tr>
<tr><td>object/str</td>
<td>datetime64, float64, int64</td>
</tr>
<tr><td>int64</td>
<td>str, float64</td>
</tr>
<tr><td>float64</td>
<td>str, int64</td>
</tr>
<tr><td>datetime64</td>
<td>str</td>
</tr>
</tbody>
</table>

**N.B.** You will **not** be able to change the type of a column if the column has missing/invalid values. Refer to the *Missing Data* section for ways to deal with missing values.

<a class="anchor" id="clean-edit-column-date"></a>

### Date format string

When changing a column to type datetime64, you can specify a format string, this will make sure that Willow will interpret the date values correctly. Date strings format in Willow is the same as Python's `strftime`, documented [here](https://docs.python.org/2/library/datetime.html#strftime-and-strptime-behavior). Here are some commonly used directives:

<table>
<tbody><tr class="headerRow"><td>Directives</td>
<td width="60%">Meaning</td>
</tr>
<tr><td>%d</td>
<td>Day of month as a decimal number.</td>
</tr>
<tr><td>%m</td>
<td>Month as a decimal number.</td>
</tr>
<tr><td>%Y</td>
<td>Year with century as a decimal number.</td>
</tr>
<tr><td>%H</td>
<td>Hour (24-hour clock) as a decimal number.</td>
</tr>
<tr><td>%M</td>
<td>Minute as a decimal number.</td>
</tr>
</tbody>
</table>

For example, here is 20:18 on July 20th, 1969 in different date-time formats:

<table>
<tbody><tr class="headerRow"><td>Date-time</td>
<td width="60%">Format String</td>
</tr>
<tr><td>20/07/69-20:18</td>
<td><code>%d/%m/%y-%H:%M</code></td>
</tr>
<tr><td>July 20, 1969 (8:18pm)</td>
<td><code>%B%d,%Y(%I:%M%p)</code></td>
</tr>
</tbody>
</table>

#### **Quirks**

- Conversion to datetime64 will fail if **any** values in the column cannot be converted to datetime64.

<a class="anchor" id="clean-edit-column-delete"></a>

### Delete column and dealing with empty strings

Other than changing column name and data type, you can also delete the column entirely by clicking *Delete Selected Column*.

For object/str typed columns, you can convert all empty strings to invalid values by clicking *Treat Empty Strings as Invalid Values*, this can be useful when you're trying to impute missing data.

<a class="anchor" id="clean-edit-row"></a>

## Edit Row

When you select one or more rows, the *Edit Row(s)* card will appear under the View section. In this card, you can delete the rows you have selected by clicking the *Delete Selected Row(s)* button.

<a class="anchor" id="clean-edit-cell"></a>

## Edit Cell

When you select a single cell, the *Edit Cell* card will appear under the View section. In this card, you can change the value of the selected cell. Willow will attempt to convert the entered value back to the data type of the column the cell is in, e.g. 33 to int rather than literal string. However, it may *not* be successful at doing so. In these cases, Willow will treat the value as a string and convert all values in the column to type Object.

<a class="anchor" id="clean-column-operations"></a>

## Column Operations

When you select a single column, the *Column Operations* card will appear under the Operate section.

<a class="anchor" id="clean-column-operations-duplicate"></a>

### Duplicate Column

This option makes a copy of the currently selected column and insert it to the right of the original.

<a class="anchor" id="clean-column-operations-split"></a>

### Split Column

This option splits each value in the selected column using a specified delimiter, put them into multiple columns and inserts them to the right of the original. For example, splitting the following column using the delimiter '/'...

<table style="max-width: 200px">
<tbody><tr class="headerRow"><td>Date</td>
</tr>
<tr><td>20/07/1969</td>
</tr>
<tr><td>21/07/1969</td>
</tr>
<tr><td>22/07/1969</td>
</tr>
<tr><td>23/07/1969</td>
</tr>
<tr><td>24/07/1969</td>
</tr>
<tr><td>...</td>
</tr>
</tbody>
</table>

... will result in the following columns.

<table>
<tbody><tr class="headerRow"><td>Date</td>
<td>Date_0</td>
<td>Date_1</td>
<td>Date_2</td>
</tr>
<tr><td>20/07/1969</td>
<td>20</td>
<td>07</td>
<td>1969</td>
</tr>
<tr><td>21/07/1969</td>
<td>21</td>
<td>07</td>
<td>1969</td>
</tr>
<tr><td>22/07/1969</td>
<td>22</td>
<td>07</td>
<td>1969</td>
</tr>
<tr><td>23/07/1969</td>
<td>23</td>
<td>07</td>
<td>1969</td>
</tr>
<tr><td>24/07/1969</td>
<td>24</td>
<td>07</td>
<td>1969</td>
</tr>
<tr><td>...</td>
<td>...</td>
<td>...</td>
<td>...</td>
</tr>
</tbody>
</table>

The names of the new columns will be in the format: *original-name_(n-1)* where n is the nth column generated.

#### **Quirks**

All empty strings in the newly generated columns will be treated as invalid values. However, the original column will be **unaffected**.

<a class="anchor" id="clean-column-operations-combine"></a>

### Combine Columns

This option combines values of multiple columns into a single column using an optional separator and inserts it in the selected column's position.

Unlike most other operations, the selection of columns to operate on is **not** done via the data table. To add a column to the list of columns to combine, type the column name into the text field, select the column you want and click *Add*. You **must** have 2 or more columns in order to perform this operation.

You can specify a separator that will be inserted between the values-to-combine; the separator can be one or more non-whitespace characters. The name for the new column generated **must** be provided, this name must be unique. Click *Combine Columns* after you've finished all configurations.

Willow will convert all values to strings and combine them by concatenating the values one-by-one, starting from the first column. The resulting column will be of type Object. For example, having selected the columns Year, Month, Day in this order, separator set as '-', new column name set as 'Date' and having selected the column Year on the data table...

<table>
<tbody><tr class="headerRow"><td>Year</td>
<td>Month</td>
<td>Day</td>
</tr>
<tr><td>1969</td>
<td>07</td>
<td>20</td>
</tr>
<tr><td>1969</td>
<td>07</td>
<td>21</td>
</tr>
<tr><td>1969</td>
<td>07</td>
<td>22</td>
</tr>
<tr><td>1969</td>
<td>07</td>
<td>23</td>
</tr>
<tr><td>1969</td>
<td>07</td>
<td>24</td>
</tr>
<tr><td>...</td>
<td>...</td>
<td>...</td>
</tr>
</tbody>
</table>

... will result in the following columns.

<table>
<tbody><tr class="headerRow"><td>Date</td>
<td>Year</td>
<td>Month</td>
<td>Day</td>
</tr>
<tr><td>1969-07-20</td>
<td>1969</td>
<td>07</td>
<td>20</td>
</tr>
<tr><td>1969-07-21</td>
<td>1969</td>
<td>07</td>
<td>21</td>
</tr>
<tr><td>1969-07-22</td>
<td>1969</td>
<td>07</td>
<td>22</td>
</tr>
<tr><td>1969-07-23</td>
<td>1969</td>
<td>07</td>
<td>23</td>
</tr>
<tr><td>1969-07-24</td>
<td>1969</td>
<td>07</td>
<td>24</td>
</tr>
<tr><td>...</td>
<td>...</td>
<td>...</td>
<td>...</td>
</tr>
</tbody>
</table>

#### **Quirks**

Behind the scenes, Willow uses the Python `join` function to combine the values. So, for example, combining 6 empty strings using `'%'` as separator will result in the value `'%%%%%'`. However, Willow **does** ignore invalid values (NaN/NA) when combining. Because of this, combining...

    (nan), 'abc', (nan), (empty string)

... with `'%'` will result in the value `'abc%'`. You can convert all empty strings in a column to NaNs by selecting that column, go to *Edit Columns* under View, and click *Treat Empty Strings as Invalid Values*.

<a class="anchor" id="clean-missing-data"></a>

## Missing Data

When you select a single column, the *Missing Data* card will appear under the Operate section.

<a class="anchor" id="clean-missing-data-average"></a>

### Impute With Column Average

Depending on the data type of the selected column, you can choose to impute all invalid/missing values in the column with:

- The column mean (if the column is of a numerical type)
- The column median (if the column is of a numerical type)
- The column mode aka most frequent value (works on all data types)

#### **Quirks**

- Imputing with column mean on an int64 typed column will change it to type float64.
- If the column has more than one mode, Willow will arbitrarily choose one to use for filling.

<a class="anchor" id="clean-missing-data-neighboring"></a>

### Impute With Neighboring Valid Value

This gives you 2 options, *forward fill* and *backward fill*. Their behaviour is illustrated below.

<table>
<tbody><tr class="headerRow"><td>Original</td>
<td>Forward Filled</td>
<td>Backward Filled</td>
</tr>
<tr><td></td>
<td></td>
<td>Euston Square</td>
</tr>
<tr><td></td>
<td></td>
<td>Euston Square</td>
</tr>
<tr><td>Euston Square</td>
<td>Euston Square</td>
<td>Euston Square</td>
</tr>
<tr><td></td>
<td>Euston Square</td>
<td>King's Cross St. Pancras</td>
</tr>
<tr><td></td>
<td>Euston Square</td>
<td>King's Cross St. Pancras</td>
</tr>
<tr><td>King's Cross St. Pancras</td>
<td>King's Cross St. Pancras</td>
<td>King's Cross St. Pancras</td>
</tr>
<tr><td>Waterloo</td>
<td>Waterloo</td>
<td>Waterloo</td>
</tr>
<tr><td></td>
<td>Waterloo</td>
<td>Goodge Street</td>
</tr>
<tr><td>Goodge Street</td>
<td>Goodge Street</td>
<td>Goodge Street</td>
</tr>
<tr><td>...</td>
<td>...</td>
<td>...</td>
</tr>
</tbody>
</table>

**N.B.** As illustrated above, when performing forward fill, if the first row of the original column has a missing value, all missing values until the **first** valid value will not be filled. This applies similarly to backward fill if the last row has a missing value.

<a class="anchor" id="clean-missing-data-interpolation"></a>

### Impute Using Interpolation

*To be written...*

<a class="anchor" id="clean-missing-data-custom"></a>

### Impute With Custom Value

This option fills in missing values with a custom specified value. Willow will attempt to convert the entered value back to the data type of the column the cell is in, e.g. 33 to int rather than literal string. However, it may *not* be successful at doing so. In these cases, Willow will treat the value as a string and convert all values in the column to type Object.

<a class="anchor" id="clean-missing-data-delete"></a>

### Delete Entire Row

This option deletes (i.e. removes from the table) all rows containing an invalid/missing value in the selected column.

<a class="anchor" id="clean-discretization"></a>

## Discretization & Quantiling

When you select a single column of a numeric type, the *Discretization & Quantiling* card will appear under the Operate section. This option partitions continuous features to discretized intervals by putting them into bins. Discretization put values into evenly spaced bins **according to the values themselves**. On the other hand, quantiling put values into evenly sized bins **according to the values frequencies**. The following example illustrates the behaviour when a column is discretized and quantiled with 5 bins.

<table>
<tbody><tr class="headerRow"><td>Original</td>
<td>Discretized</td>
<td>Quantiled</td>
</tr>
<tr><td>0</td>
<td>(-0.01, 2]</td>
<td>[0, 1.8)</td>
</tr>
<tr><td>1</td>
<td>(-0.01, 2]</td>
<td>[0, 1.8]</td>
</tr>
<tr><td>2</td>
<td>(-0.01, 2]</td>
<td>(1.8, 4.2]</td>
</tr>
<tr><td>3</td>
<td>(2, 4]</td>
<td>(1.8, 4.2]</td>
</tr>
<tr><td>5</td>
<td>(4, 6]</td>
<td>(4.2, 6.4]</td>
</tr>
<tr><td>6</td>
<td>(4, 6]</td>
<td>(4.2, 6.4]</td>
</tr>
<tr><td>7</td>
<td>(6, 8]</td>
<td>(6.4, 8.2]</td>
</tr>
<tr><td>8</td>
<td>(6, 8]</td>
<td>(6.4, 8.2]</td>
</tr>
<tr><td>9</td>
<td>(8, 10]</td>
<td>(8.2, 10]</td>
</tr>
<tr><td>10</td>
<td>(8, 10]</td>
<td>(8.2, 10]</td>
</tr>
</tbody>
</table>

Instead of having evenly spaced/sized bins, you can set custom intervals and quantiles. Check the *Custom Ranges/Quantiles* option and input a comma-seperated list of ranges/quantiles. The following example shows the behaviour when a column is discretized with the ranges: `-0.01, 2.5, 5, 10`; and quantiled with the qunatiles: `0, 0.25, 0.5, 1`.

<table>
<tbody><tr class="headerRow"><td>Original</td>
<td>Discretized</td>
<td>Quantiled</td>
</tr>
<tr><td>0</td>
<td>(-0.01, 2.5]</td>
<td>[0, 2.25]</td>
</tr>
<tr><td>1</td>
<td>(-0.01, 2.5]</td>
<td>[0, 2.25]</td>
</tr>
<tr><td>2</td>
<td>(-0.01, 2.5]</td>
<td>[0, 2.25]</td>
</tr>
<tr><td>3</td>
<td>(2.5, 5]</td>
<td>(2.25, 5.5]</td>
</tr>
<tr><td>5</td>
<td>(2.5, 5]</td>
<td>(2.25, 5.5]</td>
</tr>
<tr><td>6</td>
<td>(5, 10]</td>
<td>(5.5, 10]</td>
</tr>
<tr><td>7</td>
<td>(5, 10]</td>
<td>(5.5, 10]</td>
</tr>
<tr><td>8</td>
<td>(5, 10]</td>
<td>(5.5, 10]</td>
</tr>
<tr><td>9</td>
<td>(5, 10]</td>
<td>(5.5, 10]</td>
</tr>
<tr><td>10</td>
<td>(5, 10]</td>
<td>(5.5, 10]</td>
</tr>
</tbody>
</table>

#### **Quirks**

- When setting custom intervals, make sure that the first value is less than the minimum value of the column. Otherwise the minimum value will become blank when being discretized.
- When a column is discretized/quantiled, the column type will change to Object and the values will act like strings. This means that the column will be sorted alphanumerically when using the sort feature.

<a class="anchor" id="clean-feature-scaling"></a>

## Feature Scaling

When you select a single column of a numeric type, the *Feature Scaling* card will appear under the Operate section.

<a class="anchor" id="clean-feature-scaling-minmax"></a>

### Min-Max Scaling

This option scales the values in the column to a specified range (0 - 1 by default). This operation is also known as *normalization*. When applying this option, Willow will ignore any invalid values, i.e. invalid values will still be invalid values after the column is scaled. This operation will fail if the column has zero range (minimum value is the same as the maximum value).

<a class="anchor" id="clean-feature-scaling-standardize"></a>

### Standardization

This option scales the values in the column so that the column has zero-mean and unit-variance. When applying this option, Willow will ignore any invalid values, i.e. invalid values will still be invalid values after the column is scaled. This operation will fail if the column has zero-variance.

<a class="anchor" id="clean-feature-encoding"></a>

## Categorical Feature Encoding

When you select a single column of a numeric or object type, the *Categorical Feature Encoding* card will appear under the Operate section. This option encode categorical features using a one-hot scheme, i.e. converts each record of the column to a combination of a single high (1) bit and zero or more low (0) bits. The following example illustrates this behaviour when the column 'Model' is encoded.

<table>
<tbody><tr class="headerRow"><td>Model</td>
<td>Model_A340</td>
<td>Model_A350</td>
<td>Model_A380</td>
<td>Model_B-737</td>
<td>Model_B-747</td>
<td>Model_B-787</td>
</tr>
<tr><td>B-737</td>
<td>0</td>
<td>0</td>
<td>0</td>
<td>1</td>
<td>0</td>
<td>0</td>
</tr>
<tr><td>A380</td>
<td>0</td>
<td>0</td>
<td>1</td>
<td>0</td>
<td>0</td>
<td>0</td>
</tr>
<tr><td>A340</td>
<td>1</td>
<td>0</td>
<td>0</td>
<td>0</td>
<td>0</td>
<td>0</td>
</tr>
<tr><td>B-787</td>
<td>0</td>
<td>0</td>
<td>0</td>
<td>0</td>
<td>0</td>
<td>1</td>
</tr>
<tr><td>B-747</td>
<td>0</td>
<td>0</td>
<td>0</td>
<td>0</td>
<td>1</td>
<td>0</td>
</tr>
<tr><td>B-787</td>
<td>0</td>
<td>0</td>
<td>0</td>
<td>0</td>
<td>0</td>
<td>1</td>
</tr>
<tr><td>A340</td>
<td>0</td>
<td>1</td>
<td>0</td>
<td>0</td>
<td>0</td>
<td>0</td>
</tr>
<tr><td></td>
<td>0</td>
<td>0</td>
<td>0</td>
<td>0</td>
<td>0</td>
<td>0</td>
</tr>
<tr><td>B-747</td>
<td>0</td>
<td>0</td>
<td>0</td>
<td>0</td>
<td>1</td>
<td>0</td>
</tr>
<tr><td>A380</td>
<td>0</td>
<td>0</td>
<td>1</td>
<td>0</td>
<td>0</td>
<td>0</td>
</tr>
</tbody>
</table>

The names of the newly generated columns follow the format: *original name*_*value*. If the *Replace Original Column* option is checked, the original column will be deleted once the operation is complete.

**N.B.** Invalid/missing value will **not** generate a new column.

<a class="anchor" id="clean-custom-transformation"></a>

## Custom Transformations

When you select a single column of object or date type, the *Custom Transformations* card will appear under the Operate section.

<a class="anchor" id="clean-custom-transformation-find-replace"></a>

### Find & Replace

This feature gives you the flexibility to perform custom text transforms on a column by replacing certain specified values. By default, upon clicking the *Replace* button, Willow will look for records that **completely** matches your input in the *String to match* field, and replace them with the input in the *Replacement string* field. If the *Match Regular Expression* option is checked, then Willow will replace matched strings inside each record with the replacement string. For example, replacing 'Acton' with 'Harrow' yields the following results.

<table>
<tbody><tr class="headerRow"><td>Original</td>
<td>Replaced (Complete)</td>
<td>Replaced (Regex)</td>
</tr>
<tr><td>Acton</td>
<td>Harrow</td>
<td>Harrow</td>
</tr>
<tr><td>West Acton</td>
<td>West Acton</td>
<td>West Harrow</td>
</tr>
<tr><td>North Acton</td>
<td>North Acton</td>
<td>North Harrow</td>
</tr>
<tr><td>South Acton</td>
<td>South Acton</td>
<td>South Harrow</td>
</tr>
</tbody>
</table>

**N.B.** Willow uses the Python flavoured regex. Read more about it [here](https://docs.python.org/2/library/re.html).

Another example using more advanced regex.

Replacing

`([0-9]*)/([0-9]*)/([0-9]*)`

with

`\3-\1-\2`

yields...

<table>
<tbody><tr class="headerRow"><td>Original</td>
<td>Replaced (Regex)</td>
</tr>
<tr><td>07/20/1969</td>
<td>1969-07-20</td>
</tr>
<tr><td>07/21/1969</td>
<td>1969-07-21</td>
</tr>
<tr><td>07/22/1969</td>
<td>1969-07-22</td>
</tr>
<tr><td>07/23/1969</td>
<td>1969-07-23</td>
</tr>
<tr><td>07/24/1969</td>
<td>1969-07-24</td>
</tr>
<tr><td>07/25/1969</td>
<td>1969-07-25</td>
</tr>
</tbody>
</table>

<a class="anchor" id="clean-custom-transformation-batch"></a>

### Batch Replacement Queue

If you wish to do multiple replacements on a column, rather than performing the operations one by one, you can push each replacement operation into a queue and then execute them all at one go. To add a replacement to the queue, click **Add** instead of **Replace** after entering the details. You can add as many replacements as you want to this queue. To remove a replacement, click the <i class="material-icons md-16">close</i> next to the replacement. To reorder the replacements, click *Edit* and move a replacement up/down a spot by clicking the <i class="material-icons md-16">expand_less</i> or <i class="material-icons md-16">expand_more</i> buttons. When you are ready, click *Batch Replace*, this will apply all the replacement in the queue (in the order they're in) to the selected column. To clear the current queue, click *Edit* and *Clear Queue*.

You can also export a queue for use in a later date or with another dataset. To export a queue, click *Export*, a dialog should pop-up with a JSON string, copy and save the string. To import a queue, simply click *Import* and paste in the JSON string. If the dialogs are not appearing, make sure to disable your browser's dialog blocking functionality.

<a class="anchor" id="clean-danger-zone"></a>

## *Highway to the Danger Zone*

<div class="btn btn-alert">
<i class="material-icons md-16">error_outline</i> This functionality is for developers. Only use it if you know what you're doing as it may result in unintended alterations to your system and lead to the complete loss of your data.
</div>

This feature allows you to execute Python statements to directly manipulate the dataset. This card appears under the **Operate** tab. To show/hide this card, click the word 'and' in the table navigation bar.

The dataset is represented by the Pandas dataframe object and is referenced by the reference named `df`. To execute statements, input them in the *Commands to execute* field and click *Execute*. Multi-line code is supported.

**N.B.** `df` is a reference to the dataframe object so only in-place operations will work, i.e. operations that manipulates the dataframe itself and not ones that returns a copy of a dataframe.

<br>
<hr>
<a class="anchor" id="analyze"></a>

# Data Analysis

<div class="tableOfContents">
    <ol>
        <li><a href="#analyze-layout">Layout</a></li>
        <li><a href="#analyze-numeric">Numerical Analysis</a></li>
        <li><a href="#analyze-text">Text Analysis</a></li>
    </ol>
</div>

<a class="anchor" id="analyze-layout"></a>

## Layout

The Analyze tab consists of two parts - the sidebar and the panels. The sidebar is where you can control which column analyses to show in the panels on the right. Simply start typing the name of the column you wish to analyze, and select the column. It's analysis should show in one of the panels. You can show at most 4 column analyses at once, change the panel grid size by selecting an option in the grid size selector.

<a class="anchor" id="analyze-numeric"></a>

## Numerical Analysis

For columns of a numerical type (int, float), the following statistical attributes will be displayed:

* **Unique values** - total number of unique values in the column
* **Missing/Invalid values** - total number of missing values in the column
* **Mode** - most frequent value(s)
* **Mean**
* **Standard deviation**
* **Minimum**
* **Lower quartile**
* **Median**
* **Upper quartile**
* **Maximum**

A frequency table is also available which shows the 50 most frequent values in the column and their frequencies.

<a class="anchor" id="analyze-text"></a>

## Text Analysis

For columns of type string, the following statistical attributes will be displayed:

* **Unique values** - total number of unique values in the column
* **Missing/Invalid values** - total number of missing values in the column
* **Mode** - most frequent value(s)
* **Total words** - total number of words (*not* values) in the column
* **Unique words** - total number of unique words in the column
* **Most prominent word** - most frequent word(s)
* **Word lengths** - minimum and maximum word lengths
* **Average word length** - mean of word length
* **Words per row** - minimum and maximum of words in values
* **Average words per row** - mean of words per row

A frequency table is available which shows the 50 most frequent values in the column and their frequencies. A word frequency table is also available which shows the 50 most frequent values in the column and their frequencies.

<br>
<hr>
<a class="anchor" id="visualize"></a>

# Data Visualization

<div class="tableOfContents">
    <ol>
        <li><a href="#visualize-layout">Layout</a></li>
        <li><a href="#visualize-numeric">Numerical Analysis</a></li>
        <li><a href="#visualize-text">Text Analysis</a></li>
    </ol>
</div>
