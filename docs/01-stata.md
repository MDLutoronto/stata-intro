---
title: Stata
parent: Introduction to Stata
layout: default
created_date: 2017-05-05
staff:
    - name: Nadia Muhe
      link: https://library.utoronto.ca/staff/nadia-muhe
maintainer:
    - name: Nadia Muhe
      link: https://library.utoronto.ca/staff/nadia-muhe
nav_order: 1
---
## Stata

### Running tasks

There are three ways to run tasks in Stata. 

1. You can use point-and-click to execute tasks using the dialogs in the Data, Graphics and Statistics menus.

2. You can type Stata code in the Command window and submit the code by hitting the ENTER/return key.

3. You can type Stata code in the Do-file Editor. To open a Do-file Editor, go to **File > New > Do-file**. Once you type your code in the do-file, you can run it by highlighting the line of code and clicking on the **Execute** (**do**) icon (the play button) in the top-right corner of the Do-file window. If nothing is highlighted, Stata runs the whole do-file.

Results always appear in the Results window. 

Stata is case-sensitive.

### Search and help

Some useful commands to get started:

* `search` *enter_topic_here* returns the list of commands, FAQs, examples, and articles associated with a topic
* `help` *enter_command_here* opens the help file for a specific command
* `clear` removes the dataset that is currently loaded in memory so that you can import a new dataset

```
* Search and Help
search excel 
help import excel
```

### Stata packages

The `ssc install` command can be used to install packages from the [SSC archive](https://ideas.repec.org/s/boc/bocode.html).

```
* Stata Packages
ado dir
ssc install outreg2
ado dir
ssc uninstall outreg2
```

**Tool:** [Stata](https://mdlutoronto.github.io/tutorials-search/?tool=Stata)