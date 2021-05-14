
# Data Modeling with Cassandra

## Introduction

A startup called Sparkify wants to analyze the data they've been collecting on songs and user activity on their new music streaming app. The analysis team is particularly interested in understanding what songs users are listening to. Currently, there is no easy way to query the data to generate the results, since the data reside in a directory of CSV files on user activity on the app.

## Overview

This project aims to create ETL pipeline for loading user songs event data into NoSQL database. The resulting database is used by analytics team to query and analyze the data.

## Datasets

For this project, you'll be working with one dataset: event_data. The directory of CSV files partitioned by date. Here are examples of filepaths to two files in the dataset:

```
event_data/2018-11-08-events.csv
event_data/2018-11-09-events.csv

```

## Database schema modeling

Cassandra is a Partitioned row store.
In cassandra ,data modeling is done with the query first approach.
We can't have one unified schema design to cater any query requirements so, here tables are designed as per query requirements

Example:
```
  Based on event data file
  Query : Give me only the following: name of artist, song (sorted by itemInSession) and user (first and last name) for userid = 10, sessionid = 182
  
  Approach: Here query is asking some fields based on userId ,sessionId and along with that song field to be sorted by itemInSession
  so here 
  Partition key will be (userId,sessionId) [it tells how our data is partitioned and stored].
  Clustering key will be (itemInSession) [it tells how our data is sorted within the partition].
  Primary composite key (Partition key,clustering key) as ((userId,sessionId),itemInSession)
  
```

# Prerequisits

- python3
- cassandra and pandas packages
- cassandra database on localhost

# Files/Directories
- event_data : It contains data sets (ie.all the csv files)
- Project_1B_ Project_Template.ipynb : It contains all the codes required for ETL flow and further querying the newly created database
- README.md : Project description document
- images : It contain sample data image file

# Running the module

- Launch and run Project_1B_ Project_Template.ipynb notebook 