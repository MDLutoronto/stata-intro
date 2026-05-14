---
title: Managing Data
parent: Introduction to Stata
layout: default
nav_order: 6
---

### **Managing Data**

**Subsetting Data**

**Keep** can be used to extract a part of the dataset. You can extract specific variables or observations based on criteria.

```
* Subsetting Data : Variables
use flights, clear
keep originstate origin deptime depdelay deststate
save departure, replace

```

```
* Subsetting Data : Observations
use flights, clear
keep if deststate=="Hawaii" & dayofmonth==1
save hawaii, replace

```
 

**Merging Data**

**DATA**: [airlinecodes.xlsx](https://maps.library.utoronto.ca/workshops/Stata1/airlinecodes.php)

Download the airlines dataset by clicking on the link above or using the url *uoft.me/airlinesexcel*.

To merge two datasets, **sort** each one by the merging variable first then use the **merge** command to combine them. Whenever you merge two data files, a variable called _merge is created in the merged dataset. This variable helps you identify the observations that were successfully merged.

```
use flights, clear
sort carrier
save flights, replace

```

```
import excel using "airlinecodes.xlsx", clear firstrow
sort carrier
merge carrier using flights
save flightsmerged, replace

```

```
tab _merge
tab airline diverted, row

```
 

**Exporting Data**

In this section, we create two new variables **departureflights** and **arrivalflights** that represent the total number of departing and arriving flights for each airport using _N. This total will be repeated in every row for a particular airport. To obtain a simple table of these totals by airport, we use the **collapse** command to shrink the dataset to contain only the first value of departureflights and arrivalflights variables for each airport. Then we export this dataset as an excel file using the **export excel** command.  
The commands **preserve** and **restore** are used to temporarily modify a dataset and export it before returning back to the way the dataset was before the preserve command. In our example, after the airport dataset is created and exported, it returns us back to the flights dataset. For this code to work, you will need to run the lines from preserve to restore together.

```
use flights, clear
bysort origin : gen departureflights = _N
bysort dest : gen arrivalflights = _N
gen airport = origin

```

```
preserve
collapse (first) departureflights (first) arrivalflights, by(airport)
export excel "Airports.xlsx", replace firstrow(var)
restore

```