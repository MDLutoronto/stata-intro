---
title: Importing Data
parent: Introduction to Stata
layout: default
created_date: 2017-05-05
staff:
    - name: Nadia Muhe
      link: https://library.utoronto.ca/staff/nadia-muhe
maintainer:
    - name: Nadia Muhe
      link: https://library.utoronto.ca/staff/nadia-muhe
nav_order: 2
---
## Importing Data

### Working directory

The working directory is the folder that Stata works from by default. `pwd` gives the current working directory. Use `cd` to change the working directory to the location of your datasets. You are advised to save all the datasets from this tutorial in the same folder and to make this folder the working directory using the `cd` command. You don't have to change the working directory if you are happy working in the existing working directory. 

`dir` and `ls` both show the contents of the current directory.

```
* Working Directory
pwd
cd "/path/to/your/folder"  // paste the path to the new working directory
dir
```

### Importing the data

**Excel Data**: [cchs.xlsx](https://raw.githubusercontent.com/MDLutoronto/stata-intro/main/docs/assets/data/cchs.xlsx)\
**Stata Data**: [cchs.dta](https://raw.githubusercontent.com/MDLutoronto/stata-intro/main/docs/assets/data/cchs.dta)

Download the CCHS datasets above.

The `import excel` command imports an Excel file. Every time you import a dataset, it is good practice to add the `clear` option to clear any dataset that is loaded in memory. Options are added after the comma. `firstrow` treats the first row as variable names.

```
* Import Excel File
import excel using "cchs.xlsx", firstrow clear
```

Use the `use` command to import a Stata dataset. In this guide, we use it for the rest of the examples.

```
* Import Stata File
use cchs.dta, clear
```

Once you import the dataset, the variables are listed in the Variables window. You can check the number of observations (rows) and the number of variables (columns) in the Properties window.

**Tool:** [Stata](https://mdlutoronto.github.io/tutorials-search/?tool=Stata)