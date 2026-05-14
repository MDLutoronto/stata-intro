---
title: Reshaping Data
parent: Introduction to Stata
layout: default
nav_order: 7
---

### **Reshaping Data**

To reshape a data set between wide and long format, use the **reshape long** or **reshape wide** commands. For a data set in wide format, the variables that denote the repetition should be named with the variable name followed by a number (i.e. variablename#). For example, in our data set we have **drug1**, **drug2** and **drug3**. The numbers do not need to be consecutive.

```
clear
use https://maps.library.utoronto.ca/workshops/Stata1/statawide, clear
list

```
![]({{ '/assets/images/Stataworkshop7.1.jpg' | relative_url }}) 

 

```
describe
list
reshape long drug, i(id) j(drugtype)
list

```
![]({{ '/assets/images/Stataworkshop7.2.jpg' | relative_url }}) 

 

```
table drugtype, contents(n drug mean drug sd drug)

```
![]({{ '/assets/images/Stataworkshop7.3.jpg' | relative_url }}) 

 

```
reshape wide
list

```