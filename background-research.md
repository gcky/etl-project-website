---
layout: default
title: Background Research | ETL for Data Science
---

<a class="btn" href="{{site.baseurl}}/development.html">&lt; Research and Development</a>

# Background Research

This page details the initial research we have done at the start of this project, with the aim to gain a better understand of the problem we will be solving for this project. Click the buttons below to jump to the corresponding section.

<a class="btn-resp" href="#data-cleaning">1. Data Cleaning</a>
<a class="btn-resp" href="#data-exploration">2. Data Exploration</a>
<a class="btn-resp" href="#existing-solutions">3. Existing Solutions</a>
<a class="btn-resp" href="#misc">4. Miscellaneous</a>

<a class="anchor" id="data-cleaning"></a>

## Data Cleaning Methods

Messiness in data generally arise as undesirable properties and characteristics of the data accumulate, making the data difficult make sense of. There are various methods to tackle each of these issues.

### **Missing Values**

One of the biggest problem with raw datasets is missing values (values that should be present but not). Missing values can often lead to inaccurate analysis of the data as it may significantly skew the dataset. Many missing values can be easily detected as they are presented as null values, however sometimes a presence of a default value may also indicate a real value is missing. A solution to this problem is to replace all missing values with the average value of the column, this is often done to minimise the skewness caused by the missing values. Other solutions include removing the rows with missing values and replacing it with a custom value or a probabilistic prediction.

### **Invalid/Illegal Values**

Invalid and illegal values often indicate there is a problem with the dataset as these unexpected values can often interfere with the analysis. This means that it is crucial that these values are detected before any analysis are done on the data. This is often done by comparing the values against a constraint (eg. type constraint; max/min value for numerical data etc.), which may be user defined. Illegal values can also be detected by calculating the cardinality of the column, if it does not match the expected cardinality (eg. gender > 2), then it indicates there are illegal values.

### **Misspellings**

A typical problem with text-based data is misspellings. This kind of inconsistencies within the data can also lead to inaccurate analysis. A method for detecting and correcting misspellings is to sort the values in alphabetical order as the misspelled values are usually brought next to correct values.

### Escaped HTML Strings

Some datasets (such as ones originated from online questionairres) may contain escaped HTML strings which must be detected and unescaped. This can be done using regular expressions.

### Leading/Trailing Whitespaces

Whitespaces after (and sometimes, before) a word are often hard to detect by the human eye but has an impact on the analysis as programs count records with whitespaces as different from ones that don't, even if the rest of the characters are the same. These can be eliminatedbut removing all whitespaces before and after the intended phrase.

### **Duplicates**

Similar to missing values, duplicate records can also skew the dataset; therefore it is important to detect and remove them. Detection of duplicate records can usually be done by comparing the number of rows and the cardinality of a column, if they are not the same then it indicates there are duplicates.

<br><a class="btn-resp" href="#top">^ Back to Top</a>

<hr>
<a class="anchor" id="data-exploration"></a>

## Data Exploration Methods

We also did a brief research on data exploration methods, which included both data visualisation methods and statistical analysis methods. We looked at the most popular charts and diagrams and explored their strengths and limitations.

* ### Histogram
  * Type: Visual
  * Sub-types: Ordinary and cumulative
  * Use case: Numeric against continuous data  (with buckets), probability distributions
  * Limitation: appropriate range for buckets, low spread in dependent variable

* ### Bar chart
  * Type: Visual
  * Use case: Numeric against discrete data
  * Limitation: not too many independent variables, low spread in dependent variable

* ### Pie chart
  * Type: Visual
  * Use case: Proportions against discrete data
  * Limitation: small number of unique discrete data

* ### Line chart
  * Type: Visual
  * Use case: numeric against time
  * Limitation: only for time

* ### Boxplot
  * Type: Visual
  * Use case: comparing or visualizing distribution within numeric data set
  * Limitation: only for visualizing distribution

* ### Average
  * Type: Statistical
  * Sub-types: Mean, median, mode
  * Use case: finding the one value summary
  * Limitation: hides a lot of detail, mean skewed by outliers, mode only when values recur

* ### Standard Deviation
  * Type: Statistical
  * Use case: measuring variation/dispersion of a data set
  
* ### Skewness
  * Type: Statistical
  * Use case: descriptor of how values are distributed around mean, shape of probability distribution curve

<br><a class="btn-resp" href="#top">^ Back to Top</a>

<hr>

<a class="anchor" id="existing-solutions"></a>

## Existing Solutions

We explored various existing tools for data analysis and data cleaning as part of the initial stages of research. This helped us gain a basic idea of some features that we may like to include in our final product.

### **Apache Zeppelin**

[Apache Zeppelin](https://zeppelin.incubator.apache.org)￼ is a web-based data analytics, processing and visualization tool that follows the “notebook” format of user interaction akin to iPython/Jupyter, where the user enters snippets of code on a document, and the code is executed on the fly with the results being displayed. A unique feature of Zeppelin is that it allows multiple users to not only access but work on the same document, with changes made by one user being displayed propagated to all other users live, akin to Google Docs. Zeppelin is better described as an interactive, collaborative front-end for existing data processing backends. Users have a choice between multiple backends including Spark and Hive as well as multiple languages such as Python, Scala and SQL.

Zeppelin stands in stark contrast to more user friendly, graphical data analysis and visualization tools like JASP, as it requires users to be proficient with whichever backend and interpreter they choose to use. The learning curve is very steep, thus making it challenging to get even basic functionality out of Zeppelin. However, it is potentially an extremely powerful data analysis and visualization tool. The tasks that can be accomplished with Zeppelin are not bounded by the features as much as it is bounded by the proficiency of the user. A skilled data scientist with experience in Spark can perform virtually any data analysis and manipulation tasks following the parallelized MapReduce programming model.

### Workflow

Every action must be performed manually/programmatically with whichever backend and language the user chooses. The most common pairings are Scala for Spark and Python for Spark. The programming model of MapReduce (data manipulation using functional programming) is extensively used in all stages and is the common theme across all use cases for Zeppelin.

### Loading

User calls function to load a text file over network or from disk, and the function returns a pointer to the data, which is either a string (when importing unstructured data) or a Resilient Distributed Dataset object (RDD, when importing structured data).
Parsing

If the file is not structured i.e. not JSON, CSV, XML, etc, the data is initially stored as a string, and the user must write map and filter statements to convert the string into nested lists and then convert that into an RDD object. If no variable names/types are provided, or the user wants to specify them him/herself, a Class is defined and the nested lists must be mapped to a list containing objects of that class.

### Cleaning

In my opinion, any complex form of data cleaning is very tedious to achieve in Zeppelin, but I may be thinking that because I am not experienced in functional programming or Spark. The method for cleaning is highly dependent on the circumstances of the dataset. For example, missing values can be found by writing a filter expression with a custom evaluation function that returns true when any variables are null, empty or a specific keyword. A string field that still contains URL or XML escape strings would be unescaped by writing a map expression with a custom manipulation function that finds escape strings and replaces them with "".

### Analysis

Once the data is clean, the RDD object is converted to a data frame (DF) object which is automatically saved as a temporary SQL table (can be made persistent). For any nun- numeric analyses, such as a mean for a numeric variable field or the most common word in a string variable field, the user must write more code. For example, a mean can be found with a reduce expression that sums all the values and then divided by the number of rows. For graphical analysis (visualization), one of Zeppelin’s strengths come into play. The user writes SQL queries for the DF object acting as a SQL table, and then the results of these queries are automatically displayed as graphs. Zeppelin supports bar charts, histograms, line graphs and pie charts.

### Advantages

* very powerful for technical users -> data cleaning and analysis functionalities of Zeppelin is theoretically limited only by the user’s coding prowess
* designed to be extremely scalable -> handles large datasets extremely well, thanks to Apache Spark backend
* central storage and access point for notebooks (on server hosting the Zeppelin notebook)
* live collaboration when multiple users edit the document
Disadvantages
* not all visualization techniques
* all actions must be manually performed programmatically -> slow compared to other
tools for common workflows/tasks (unless user is extremely proficient)
* very steep learning curve
* difficult to setup (Zeppelin notebooks are hosted and "executed" on a server)
￼

### **JASP**

[JASP](https://jasp-stats.org/) is an open-source graphical program for statistical analysis. The program accepts only CSV format datasets. As JASP is more statistically oriented compared to other products and services we researched on, JASP place a significant attention to the types of variable in the dataset. Once the dataset has been imported, JASP will try to determine the variable types of the data (eg. nominal, continuous, ordinal). The user has full control over these variable types so if the user feel JASP has determined the types wrongly, they can define it themselves in the program.

JASP can create a descriptive view of the dataset. These descriptive include the number of valid cells in each column, number of missing values, and some basic statistical characteristics such as averages (mean, median, mode), dispersion (standard deviation, range etc.) and distribution (skewness). As mentioned, JASP also offers an extensive range of tools for statistical analysis on the dataset provided by the user. These include T-Tests, ANOVA, Regression and Frequencies.

### **OpenRefine**

[OpenRefine](http://openrefine.org) (formerly Google Refine) is an open-source program which users can use through a web browser. OpenRefine allows users to import a dataset in various formats (including JSON, CSV, XML etc.) and offers various tools to clean any "messiness" in their data. 

OpenRefine supports various data formats such as separator-based files, line based files, XML files, and Open Document Format spreadsheets. For separator-based files, the user can also specify a custom separator. The user can also ignore beginning lines of a file, which may not be part of the data; or discard some rows of the data. 

For any column, the user can create a facet. Facets are essentially filters, for example, a text facet displays all the unique records and shows the number of times it occurs in the data. Clicking on one of them will cause the main window to display only rows with that particular text. It is also possible to edit cells in a column in bulk. Common operations such as trimming leading and trailing whitespaces, unescape HTML entities, and changing letter casing are offered in a menu. 

After the data has been cleaned, it can be exported in various file formats with user specified structures. The list of operations performed on the data can also be extracted and applied to a different dataset. Although OpenRefine offers extensive tools for data manipulation, unlike other services such as Amazon Web Services and Microsoft Azure, OpenRefine does not offer any data visualisation tools.

<br><a class="btn-resp" href="#top">^ Back to Top</a>

<hr>

<a class="anchor" id="misc"></a>

## Miscellaneous

### **Kaggle Competition**

[Exploring Springleaf](http://kaggle.com/darraghdog/springleaf-marketing-response/explore-springleaf)

Language: R

* R is generally a powerful and effective language for manipulating and exploring data
potentially useless data <* find columns that have only one unique value>
* detects text vs numeric values in a column "e.g. numeric vs text" <* filter which columns to focus on>
* list the unique text occurrences sorted by frequency
* use regular expression to select columns
* parse dates in user-defined format
* quickly generate histograms/bar graphs
* non-destructive editing "e.g. US states" <* generate heat-maps on maps> "e.g. NA/invalid percentage & chart, unique values per variable chart" <* overview statistics/graphs>
"Pearson, Spearman" <* visualization to display all potential correlations between variables with color coded correlation “matrix”>

<br><a class="btn-resp" href="#top">^ Back to Top</a>