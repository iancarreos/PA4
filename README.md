# PA4
# ECE2112 Experiment 4

**Name:** Carreos, Christian Benedict R. **Section:** 2ECE-D

## Description

This experiment uses **Pandas** and **Matplotlib** in Python to work with student data from an Excel file. It includes calculating student averages, filtering students based on different conditions, grouping data by categories, and creating bar charts.

## Part A – Visayas Communication DataFrame

The `board2.xlsx` file is loaded using Pandas:

**import pandas as pd**

**df = pd.read_excel("board2.xlsx")**

The average of the four subjects is calculated for every student using:

**df["Average"] = df[["Math", "GEAS", "Electronics", "Communication"]].mean(axis=1)**

The `mean()` function calculates the average, while `axis=1` means the calculation is done across each row.

Students from **Visayas** whose Track is **Communication** are selected using two conditions:

**VisComm = df[(df["Hometown"] == "Visayas") & (df["Track"] == "Communication")][["Name", "Gender", "Math", "Electronics", "Average"]]**

The `&` symbol means **AND**, so both conditions must be true.

Only the following columns are retained:

* Name
* Gender
* Math
* Electronics
* Average

The number of rows is checked using:

**len(VisComm)**

The result has **5 rows**.

## Part B – Visayas Female DataFrame

A second DataFrame named `VisFemale` is created by selecting students whose Hometown is **Visayas** and whose Gender is **Female**.

**VisFemale = df[(df["Hometown"] == "Visayas") & (df["Gender"] == "Female")][["Name", "Track", "GEAS", "Electronics", "Average"]]**

The selected columns are:

* Name
* Track
* GEAS
* Electronics
* Average

The complete `VisFemale` DataFrame is displayed using:

**display(VisFemale)**

Students with an Average of at least **60** are then displayed using:

**display(VisFemale[VisFemale["Average"] >= 60])**

This second filter does not overwrite the original `VisFemale` DataFrame.

The `>=` operator means **greater than or equal to**.

## Part C – Category-Average Visualization

The mean Average is calculated for the categories **Track, Gender, and Hometown**.

First, Matplotlib is imported:

**import matplotlib.pyplot as plt**

The mean Average for each Track is calculated using:

**mean_track = df.groupby("Track")["Average"].mean()**

The mean Average for each Gender is calculated using:

**mean_gender = df.groupby("Gender")["Average"].mean()**

The mean Average for each Hometown is calculated using:

**mean_hometown = df.groupby("Hometown")["Average"].mean()**

The `groupby()` function groups the students according to a category, while `mean()` calculates the average for each group.

The three summary tables are displayed using:

**display(mean_track.reset_index())**

**display(mean_gender.reset_index())**

**display(mean_hometown.reset_index())**

The `reset_index()` function changes the grouped index back into a regular column for easier viewing.

### Bar Charts

Three bar charts are created in one figure using:

**plt.figure(figsize=(20, 5))**

The first chart shows the mean Average by Track:

**plt.bar(mean_track.index, mean_track.values)**

The second chart shows the mean Average by Gender:

**plt.bar(mean_gender.index, mean_gender.values)**

The third chart shows the mean Average by Hometown:

**plt.bar(mean_hometown.index, mean_hometown.values)**

`plt.subplot(1, 3, ...)` is used to place the three charts in one row.

The chart is displayed using:

**plt.show()**

### Findings

Based on the calculated sample means:

* **Track:** Communication has the highest sample mean Average.
* **Gender:** Male has the highest sample mean Average.
* **Hometown:** Luzon has the highest sample mean Average.

