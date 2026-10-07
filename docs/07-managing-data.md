---
title: Managing Data
parent: Introduction to Stata
layout: default
created_date: 2017-05-05
staff:
    - name: Nadia Muhe
      link: https://library.utoronto.ca/staff/nadia-muhe
maintainer:
    - name: Nadia Muhe
      link: https://library.utoronto.ca/staff/nadia-muhe
nav_order: 7
---
## Managing Data

`keep` can be used to extract a part of the dataset. You can extract specific variables or observations based on criteria. 

### Subsetting by variables

```
* Subsetting by Variables (Columns)
use cchs_analysis, clear
keep id sleep_hours activity fruit_veg screen_workday screen_offday
save lifestyle, replace
```

### Subsetting by observations

```
* Subsetting by Observations (Rows)
use cchs_analysis, clear
fre age_group screen_workday screen_offday
keep if age_group == 2 & screen_workday != . & screen_offday != .
save young_adult_screen_complete, replace
```

### Sorting data

Use `sort` to sort a dataset by a variable. To sort in descending order, use the `gsort` command instead with a minus sign before the variable name.

```
* Sorting Data
use cchs_analysis, clear
sort income
gsort -income   // highest to lowest
```

**Tool:** [Stata](https://mdlutoronto.github.io/tutorials-search/?tool=Stata)