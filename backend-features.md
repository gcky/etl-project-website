---
layout: default
title: Back-End Features | ETL for Data Science
---

<a class="btn" href="{{site.baseurl}}/development.html">&lt; Research and Development</a>

# Back-End Features Development

This page includes all experiments and prototypes we have done of the various back-end features and details important decisions made while developing these features. Click the buttons below to jump to the corresponding section.

<a class="btn-resp" href="#first-prototypes">1. First Prototypes</a>
<a class="btn-resp" href="#datasets">X. Datasets Used</a>

<a class="anchor" id="first-prototypes"></a>

## First Prototypes

Since we established that the system will use [Pandas](http://pandas.pydata.org), an open-source Python data analysis library, to analyse the data, we decided to experiment with Pandas by attempting to implement some data cleaning features. This gave us the chance to familiarise with the various features of Pandas and also get glimpses of the problems and issues we may run into when developing these back-end features. We used [iPython](http://ipython.org) Notebook as the interface for experimenting with Pandas. Below are the prototypes we produced presented as iPython notebooks.

* **Missing Values** - This prototype focuses on dealing with missing values in a dataset and demonstrates Pandas features such as interpolation.<a class="btn btn-short btn-inline" href="{{site.baseurl}}/external/pandas-prototypes/missing-vals.html" target="_blank">View Notebook</a>
* **Data Normalisation and Standardisation** - This prototype focuses on normalising and standardising data in a dataset.<a class="btn btn-short btn-inline" href="{{site.baseurl}}/external/pandas-prototypes/normalisation.html" target="_blank">View Notebook</a>
* **Detecting Outliers** - This prototype focuses on detecting potential outliers in a dataset using various metrics for center and dispersion.<a class="btn btn-short btn-inline" href="{{site.baseurl}}/external/pandas-prototypes/outliers.html" target="_blank">View Notebook</a>
* **Grouping Alternative Representations of the Same Entity** - This prototype focuses on grouping multiple representations of the same entity in a dataset.<a class="btn btn-short btn-inline" href="{{site.baseurl}}/external/pandas-prototypes/grouping.html" target="_blank">View Notebook</a>

<br><a class="btn-resp" href="#top">^ Back to Top</a>

<hr>

<a class="anchor" id="datasets"></a>

## Datasets Used for Experimentation

Various datasets from the internet were used for experimentation during this project. Datasets used within a prototype are credited in the prototype. Below is (in no particular order) a list of datasets used during the course of this project.

* [Wellcome Trust: Article Processing Charges Paid in 2012-2013](http://figshare.com/articles/Wellcome_Trust_APC_spend_2012_13_data_file/963054)
* [Code for Kenya: Health Facilities in Kenya](http://africaopendata.org/dataset/health-facilities-in-kenya)
* [HK Environmental Protection Department: Past Record of Air Pollution Index (English)](https://data.gov.hk/en-data/dataset/hk-epd-airteam-past-record-of-air-pollution-index-en)
* [Met Office: UK Climate - Historic Station Data](http://www.metoffice.gov.uk/public/weather/climate-historic/)

<br><a class="btn-resp" href="#top">^ Back to Top</a>