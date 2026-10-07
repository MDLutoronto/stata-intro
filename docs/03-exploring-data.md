---
title: Exploring Data
parent: Introduction to Stata
layout: default
created_date: 2017-05-05
staff:
    - name: Nadia Muhe
      link: https://library.utoronto.ca/staff/nadia-muhe
maintainer:
    - name: Nadia Muhe
      link: https://library.utoronto.ca/staff/nadia-muhe
nav_order: 3
---
## Exploring Data

### Data overview

`describe` lists the variables, their data storage type and their labels. `codebook` gives a frequency table for variables with very few values, basic statistics (mean, std dev etc) for continuous variables, and the number of missing observations for all variables.

```
* Data Overview
describe
codebook
```

<img src="{{ '/assets/images/3_1.png' | relative_url }}" alt='describe command results.' title='' width='600'/>

<img src="{{ '/assets/images/3_2.png' | relative_url }}" alt='codebook command results' title='' width='600'/>

`list` can be used to print or display data values in the Results window. It allows users to specify the variables and observations to print.

```
* Displaying Rows & Columns
list age_group in 1
list age_group in 1/3
list health mental_health activity in 60000/60005
```

<img src="{{ '/assets/images/3_3.png' | relative_url }}" alt='list command results' title='' width='400'/>

### Frequency tables

`tab` is an abbreviation for `tabulate`. The `m` option is used to display the number of missing values for the specified variables. The `cell`, `row` and `col` options display the cell, row and column percentages.

```
* Frequency Table
tab mental_health
tab mental_health, m
```
<img src="{{ '/assets/images/3_4.png' | relative_url }}" alt='Frequency table of mental health.' title='' width='400'/>

```
* Two-Way Frequency Table
tab mental_health income_quintile, m
tab mental_health income_quintile, m row col cell
```

<img src="{{ '/assets/images/3_5.png' | relative_url }}" alt='Two-way frequency table of mental health and income quintile.' title='' width='500'/>

<img src="{{ '/assets/images/3_6.png' | relative_url }}" alt='Two-way frequency table of mental health and income quintile including row and column percentages.' title='' width='600'/>

`fre` shows frequencies with both value labels and codes.

```
* Frequency Table Using fre
ssc install fre
ado dir
fre mental_health
```

<img src="{{ '/assets/images/3_7.png' | relative_url }}" alt='Frequency table of mental health using fre command' title='' width='400'/>

### Missing data

`misstable summarize` shows how many missing values each numeric variable has.

```
* Missing Data
misstable summarize
```

<img src="{{ '/assets/images/3_8.png' | relative_url }}" alt='Missing data summary statistics for all the variables.' title='' width='600'/>

### Summary statistics

`sum` is an abbreviation for `summarize`. It gives summary statistics of numeric variables. We can add conditions to a line of code using the `if` qualifier. For example, we can get the summary statistics of life satisfaction scores for Ontario only using the province variable and setting it equal to "ON". Two equal signs are used for the equal to condition.

```
* Summary Statistics
sum life_sat
sum life_sat if province=="ON"
```

<img src="{{ '/assets/images/3_9.png' | relative_url }}" alt='Summary statistics of life satisfaction.' title='' width='500'/>

### Grouped summary statistics

`bysort` can be used to run a line of code for every category of a second variable. For example, we can get the summary statistics of life satisfaction for each province.

```
* Grouped Summary Statistics
bysort province: sum life_sat
```

<img src="{{ '/assets/images/3_10.png' | relative_url }}" alt='Summary statistics of life satisfaction by province.' title='' width='500'/>

```
bysort food_security: sum life_sat
```

<img src="{{ '/assets/images/3_11.png' | relative_url }}" alt='Summary statistics of life satisfaction by food security status.' title='' width='500'/>

```
* Alternative approach to bysort
tab food_security, sum(life_sat)
```

<img src="{{ '/assets/images/3_12.png' | relative_url }}" alt='Mean, standard deviation, and frequency of life satisfaction by food security status.' title='' width='400'/>

**Tool:** [Stata](https://mdlutoronto.github.io/tutorials-search/?tool=Stata)