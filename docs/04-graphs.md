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
## Graphs

The `hist`, `scatter` and `graph bar` commands can be used to make a histogram, a scatterplot and a bar chart respectively. There are many options that can be added to modify all graphs. These options come after the comma. The list of options possible can be found in the help file of each command. Some options can be applied for all or most graphing commands. **Title()** can be used to add a main title. `xtitle()` is used to specify the label of the x-axis. `ytitle()` is used to specify the label of the y-axis.


### Bar chart

The bar chart is usually used to plot summary statistics on the y-axis such as the number of observations for each category of another variable. The count statistic is specified in parenthesis to make a bar chart of the count of observations. The variable on the x-axis is specified in the `over()` option. `b1title()` is used to label the x-axis of bar charts instead of `xtitle()`.

```
* Bar Chart
graph bar (count), over(stress)
graph bar (count), over(stress) title(Stress Levels in the 2022 CCHS) ytitle(Frequency) b1title(Stress Level)
```
<img src="{{ '/assets/images/barchart.png' | relative_url }}" alt='Barchart of stress levels.' title='Stress Levels in the 2022 CCHS' width='600' />

### Histogram

The `discrete` option . `frequency` . The `color()` and `lcolor()` are used to specify the color of the bin and the border around the bin.

```
* Histogram
hist life_sat
hist life_sat, discrete frequency
hist life_sat, discrete frequency title(Life Satisfaction) xtitle(Life Satisfaction Score) color(ltblue) lcolor(white)
```
<img src="{{ '/assets/images/histogram.png' | relative_url }}" alt='Histogram of life satisfaction score.' title='Life Satisfaction' width='600'/>

### Scatterplot

The `msymbol()`, `msize()` and `mcolor()` options can be used to specify the shape, size and color of each point on the scatterplot.

```
* Scatterplot
scatter life_sat sleep_hours
scatter life_sat sleep_hours, jitter(5)
scatter life_sat sleep_hours, jitter(5) msymbol(+) msize(small) mcolor(maroon)
scatter life_sat sleep_hours, jitter(5) msymbol(+) msize(small) ///
colorvar(sex) colordiscrete colorlist(red black) coloruseplegend ///
title(Sleep Hours and Life Satisfaction by Sex) ///
ytitle(Life Satisfaction Score) ///
xtitle(Sleep Hours) ///
plegend(order(1 "Male" 2 "Female") ring(0) position(5))
```

<img src="{{ '/assets/images/scatterplot.png' | relative_url }}" alt='Scatterplot of sleep hours and life satisfaction colour coded by sex.' title='Sleep Hours and Life Satisfaction by Sex' width='600'/>

You can continue a line of code over multiple lines by adding three forward slashes at the end of the lines that continue.

**Tool:** [Stata](https://mdlutoronto.github.io/tutorials-search/?tool=Stata)