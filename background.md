---
layout: default
title: Background | ETL for Data Science
---

# Background and Context

## Our Client

[Seldon](http://seldon.io) is an open-source machine learning platform for data scientists and developers to include recommendations and predictive scoring within their apps and services. Seldon’s REST API ingests data in JSON format of a user, item and action triple for user behavioural data, and arbitrary events JSON for more general predictive data.

## Messy Data

Before data can be injected into Seldon's machine learning platform, the data needs to be prepared and "cleaned". This is because raw data set often contains inaccurate records. In order for any statistical analysis to be performed on the data set, incomplete, incorrect, irrelevant parts of the data set has to be indentified and replaced with correct data. This process is commonly known as data cleaning.

Currently, this process is often done manually by analysing the raw data set in a case-by-case basis; this approach frequrently make this critical process be seen as time consuming and tedious.

## Problem Definition

* Seldon receives messy data from clients.
* Clients aren’t clear on the quality of the data they have available.
* Data collection and analysis often slows down or blocks client projects from progressing.
* Visualising data to to spot patterns and deliver insights can take a long time or require expensive or disparate tools.
* If we don’t understand the data we can’t solve the client’s problem.