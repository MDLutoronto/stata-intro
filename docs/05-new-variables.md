---
title: New Variables
parent: Introduction to Stata
layout: default
created_date: 2017-05-05
staff:
    - name: Nadia Muhe
      link: https://library.utoronto.ca/staff/nadia-muhe
maintainer:
    - name: Nadia Muhe
      link: https://library.utoronto.ca/staff/nadia-muhe
nav_order: 5
---
## New Variables

To generate a new variable that is a function of other variables, use the `gen` command. `gen` is short for `generate`. You will find a few examples of how to create different types of variables below. 

### Example 1: Binary Variable

In the first example, we create an indicator variable called **food_insecure** to identify individuals who have reported being food insecure. 

The `fre` command is used to see the numeric values corresponding to the category labels of food security. 

```
* Example 1: Binary Variable
* Food Insecurity Indicator
fre food_security
```

<img src="{{ '/assets/images/5_1.png' | relative_url }}" alt='Frequency table of food security.' title='' width='500'/>

```
gen food_insecure = .
replace food_insecure = 0 if food_security == 1
replace food_insecure = 1 if food_security != 1 & food_security !=.
* Check
tab food_security food_insecure, m
```

<img src="{{ '/assets/images/5_2.png' | relative_url }}" alt='Two-way table of food security and food insecurity indicator.' title='' width='500'/>


Labels can be created for the entire dataset, for a variable and for the levels of a categorical variable. To label the levels of the variable **food_insecure**, first the label **food_insecure_label** is created using the `label define` command. Then it is assigned to the variable **food_insecure** using the `label values` command.

```
* Add labels
label define food_insecure_label 0 "Secure" 1 "Insecure" 
label values food_insecure food_insecure_label
fre food_insecure
```

<img src="{{ '/assets/images/5_3.png' | relative_url }}" alt='Frequency table of food insecurity indicator with labels.' title='' width='500'/>


### Example 2: Categorical Variable

In the second example, a categorical variable **risk** is created using the values of smoking and drinking.

```
* Example 2: Categorical Variable
* Smoking & Drinking Risk Categories
fre smoking
fre drinking
```

<img src="{{ '/assets/images/5_4.png' | relative_url }}" alt='Frequency tables of smoking and drinking.' title='' width='500'/>


```
gen risk = ""
replace risk = "Both"    if smoking == 1 & drinking == 1
replace risk = "Smoker"  if smoking == 1 & drinking != 1 & drinking != . 
replace risk = "Drinker" if smoking != 1 & drinking == 1 & smoking != .
replace risk = "Neither" if smoking != 1 & drinking != 1 & smoking != . & drinking != .
* Check
tab smoking drinking, m
tab risk, m
```
 
<img src="{{ '/assets/images/5_5.png' | relative_url }}" alt='Two-way table of smoking and drinking, and frequency table of risk categories.' title='' width='500'/>

An alternative to `drinking != .` is `!missing(drinking)`. 

### Example 3: Count Variable

The command `egen` is used to generate new variables using built-in functions. For example, the `rowtotal()` function calculates the row sum and the `mean()` function calculates the mean.

In the third example, we create a count variable that is the total number of chronic conditions reported. 

```
* Example 3: Count Variable
* Total Chronic Conditions Reported
egen chronic_count = rowtotal(diabetes hbp cholesterol mood anxiety fatigue msk cardiovascular)
* Check
tab chronic_count, m
```

<img src="{{ '/assets/images/5_6.png' | relative_url }}" alt='Frequency table of number of chronic conditions.' title='' width='400'/>

Note: `rowtotal()` treats missing values as 0. To set the count to missing when all conditions are missing, add the `missing` option.

### Example 4: Group Summary Variable

Example 4 creates a new variable called **mean_life_sat_province** that is the mean of life satisfaction for each province.

```
* Example 4: Group Summary Variable
* Mean Life Satisfaction by Province
egen mean_life_sat_province = mean(life_sat), by(province)
* Check
tab province, sum(mean_life_sat_province)
```

<img src="{{ '/assets/images/5_7.png' | relative_url }}" alt='Mean life satisfaction by province.' title='' width='400'/>

The CCHS dataset now has 4 new variables. This can be checked in the Variables window. 

**Tool:** [Stata](https://mdlutoronto.github.io/tutorials-search/?tool=Stata)