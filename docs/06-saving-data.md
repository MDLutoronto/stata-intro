---
title: Saving Data
parent: Introduction to Stata
layout: default
created_date: 2017-05-05
staff:
    - name: Nadia Muhe
      link: https://library.utoronto.ca/staff/nadia-muhe
maintainer:
    - name: Nadia Muhe
      link: https://library.utoronto.ca/staff/nadia-muhe
nav_order: 6
---
## Saving Data

### Saving Stata dataset

The `save` command can be used to save a dataset after you modify it. The `replace` option overwrites the file if it already exists. Use a new file name, like **cchs_analysis**, so you don't overwrite your original data.

```
* Saving Stata Dataset
save cchs_analysis, replace
```

### Exporting data as Excel

Use `export excel` to save the dataset as an Excel file. The `firstrow(variables)` option writes the variable names in the first row. 

```
* Exporting Data as Excel
export excel using "cchs_analysis.xlsx", replace firstrow(variables)
```

`export excel` writes value labels by default. Add `nolabel` to export the numeric codes instead.

**Tool:** [Stata](https://mdlutoronto.github.io/tutorials-search/?tool=Stata)