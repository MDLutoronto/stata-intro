---
title: New Variables
parent: Introduction to Stata
layout: default
nav_order: 5
---

### **New Variables**

To generate a new variable that is a function of other variables, use the **generate** command. You will find a few examples of how to create different types of variables below. In the first example, the variable **distancemiles** (distance in units of miles) is created by converting distance in kilometers to miles.

```
* Example 1
gen distancemiles = distance * 0.621
sum distance distancemiles

```
 

```
* Example 2
gen instate = .
replace instate = 1 if originstate==deststate
replace instate = 0 if originstate!=deststate
tab instate, m

```
 

Labels can be created for the entire dataset, for a variable and for the levels of a categorical variable. To label the levels of the variable instate, first the label instatelabel is created using the **label define** command. Then it is assigned to the variable instate using the **label values** command.

```
label define instatelabel 1 "Within State" 0 "Between State"
label values instate instatelabel
tab instate, m

```
 

```
* Example 3
gen delay = ""
replace delay = "not delayed" if depdelay==0 & arrdelay==0
replace delay = "delayed at departure only" if depdelay==1 & arrdelay==0
replace delay = "delayed at arrival only" if depdelay==0 & arrdelay==1
replace delay = "delayed at both" if depdelay==1 & arrdelay==1
tab delay, m

```
 

The command **egen** is used to generate new variables using built\-in functions. For example, the **mean()** function generates mean. Example 4 creates a new variable called meandistance that is the mean of distance. Example 5 creates a new variable meandistancebycarrier which is the mean distance for each carrier or airline.

```
* Example 4
egen meandistance = mean(distance)
tab meandistance

```

```
* Example 5
egen meandistancebycarrier = mean(distance), by(carrier)
tab meandistancebycarrier

```
 

The original flights dataset now has 5 new variables. This can be checked in the variables window. The **save** command can be used to save this flights dataset. It is good practice to use the **replace** option.

```
save flights.dta, replace

```