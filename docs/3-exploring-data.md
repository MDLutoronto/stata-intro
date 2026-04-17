---
title: Exploring Data
parent: Introduction to Stata
layout: default
nav_order: 3
---

### **Exploring Data**

**Describe** enumerates the list variables, their data type and their labels. **Codebook** gives a frequency table for character variables, basic statistics (mean, std dev etc) for numeric variables and the number of missing observations for both types of variables.

```
describe
codebook

```
**List** can be used to print data values in the results window. It allows users to specify the variables and observations to print.

```
list originstate in 1
list originstate deptime depdelay in 1000/1005

```
**Tab** is an abbreviation for **tabulate.** The **m** option is used to display the number of missing values for the specified variables. The **cell**, **row** and **col** options display the cell, row and column percentages.

```
tab depdelay, m
tab depdelay arrdelay, m
tab depdelay arrdelay, m cell row col

```
**Sum** is an abbreviation for **summarize**. It gives summary statistics of numeric variables. We can add conditions to a line of code using the if qualifier. For example, we can get the summary statistics of flight distance for flights that took place on Mondays only using the dayofweek variable and setting it equal to 1 which represents Monday. Two equal signs are used for the equal to condition.

```
sum distance
sum distance if dayofweek==1

```
**Bysort** can be used to run a line of code for every category of a second variable. For example, we can get the summary statistics of flight distance for each day of the week.

```
bysort dayofweek: sum distance

```