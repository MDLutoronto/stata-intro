---
title: Importing Data
parent: Introduction to Stata
layout: default
nav_order: 2
---

### **Importing Data**

**Working directory**

The working directory is the home directory that Stata works from by default. **Pwd** gives the current working directory. Use **cd** to change the working directory to the location of your datasets. You are advised to save all the datasets from this tutorial in the same folder and to make this folder the working directory using the **cd** command.

**Dir** and **ls** both show the content of the current directory.

```
pwd 
cd "[enter path here]" 
dir 
ls
```
**Importing Data**

**DATA**: [flights.dta](https://maps.library.utoronto.ca/workshops/Stata1/flightsstata.php)

Download the flights dataset by clicking on the link above or using the url *uoft.me/flightsstata*.

The **use** command can be used to import a Stata dataset. Every time you import a dataset, it is good practice to add the clear option to clear any dataset that is loaded in memory. Options are added after the comma.

```
use flights, clear

```
Once you import the dataset, the variables are listed in the variables window. You can check the number of rows and the number of observations in the properties window.
