---
title: Graphs
parent: Introduction to Stata
layout: default
created_date: 2017-05-05
staff:
    - name: Nadia Muhe
      link: https://library.utoronto.ca/staff/nadia-muhe
maintainer:
    - name: Nadia Muhe
      link: https://library.utoronto.ca/staff/nadia-muhe
nav_order: 4
---

### **Graphs**

The **hist**, **scatter** and **graph bar** commands can be used to make a histogram, a scatterplot and a bar chart respectively. There are many options that can be added to modify all graphs. These options come after the comma. The list of options possible can be found in the help file of each command. Some options can be applied for all or most graphing commands. **Title()** can be used to add a main title. **Xtitle()** is used to specify the label of the x-axis. **Ytitle()** is used to specify the label of the y-axis.

The **normal** option adds a normal curve on the histogram. **Bin()** allows the user to specify the number of bins. **Color()** and **lcolor()** are used to specify the color of the bin and the border around the bin.

```
hist deptime
hist deptime, normal bin(30) color(ltblue) lcolor(white) xtitle(Departure Time)

```
<img src='{{ '/assets/images/Stata3.1.png' | relative_url }}' alt='' title='' width='508' height='368' />

The **msymbol()**, **msize()** and **mcolor()** options can be used to specify the shape, size and color of each point on the scatterplot. The **xlabel()** is specify the ticks on the x-axis. The **plotregion()** is used to specify the margin between the plot region and the axes.

```
scatter deptime dayofweek
scatter deptime dayofweek, msymbol(+) msize(huge) mcolor(maroon) xlabel(1(1)7) plotregion(margin(10 10 2 2))

```
<img src='{{ '/assets/images/Stata3.2.png' | relative_url }}' alt='' title='' width='508' height='367' />

The bar chart is usually used to plot summary statistics on the y-axis such as the number of observations for each category of another variable. The count statistic is specified in parenthesis to make a bar chart of the count of observations. The variable on the x-axis is specified in the **over()** option. **B1title()** is used to label the x-axis of bar charts instead of xtitle().

```
graph bar (count), over(dayofweek)
graph bar (count), over(dayofweek) title(Frequency of Flights by Day of the Week) ytitle(Frequency) b1title(Day of Week)

```
<img src='{{ '/assets/images/Stata3.3.png' | relative_url }}' alt='' title='' width='510' height='372' />

You can continue a line of code over multiple lines by adding three forward slashes at the end of the lines that continue.

**Tool:** [Stata](https://mdlutoronto.github.io/tutorials-search/?tool=Stata)