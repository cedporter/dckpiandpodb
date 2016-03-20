DC KPI and PO DB
A Combination of DC Purchase Order and Performance Metrics Data


Description of Data
-------------------
The Washington, DC municipal government posts a great number of datasets to 
their [DC Open Data](http://opendata.dc.gov/) site. From it, we selected two 
datasets to combine via [MariaDB](https://mariadb.org/) to aid in their 
analysis. The first dataset contains all of the purchase orders from 2013 
totalling over $2500 (District of Columbia Open Data, 2013a). The second 
contains various key performance indicators (KPI) for the various DC 
government agencies (District of Columbia Open Data, 2013b). Both datasets 
are organized by agency, by which we could link the two.


Why Combine the Data?
---------------------
By combining these datasets, we hoped to establish whether or not any 
correlation exists between the total purchase orders of a particular agency 
and their performance metrics performance, i.e., does money spent equal 
performance gains?


Data Analysis
-------------
For analysis of the data present in the two datasets, we combined them on 
basis of the common variable named ‘Agency’. We then tried to analyze if 
there is any relationship between the total amount spent (P.O.Totals) by an 
agency and the percentage of “Fully Achieved” KPIs. First, recognizing the 
extraordinarily wide range of PO Totals, we narrowed our scope to only review 
Agencies with totals between $10 and $100 million in PO Totals. We then 
calculated the percentage of "Fully Achieved" KPIs in with respect to the total 
performance rating amongst categories "Fully Achieved", "Partially Achieved", 
and "Not Achieved." We then created a new Excel worksheet containing the name 
of agency, the total amount spent by agency and the percentage of “Fully 
Achieved” performance ratings.
	
Descriptive Analysis
--------------------
To begin the analysis, we used the command `summary()` in R to determine the 
descriptive analysis and `hist()` to plot histograms (Figures 1 and 2). Finally, 
in order to then determine the relation between the amount spent by an agency 
and the performance rating achieved by an agency, we then used a scatter plot 
for both variables using the R command: `plot()` (Figure 3).

Commands:
    summary(sample$P.O..Totals)
    summary(sample$Fully.Achieved.Percentages)
    hist(sample$P.O..Totals)
    hist(sample$Percentages)
    plot(sample$P.O..Totals, sample$Fully.Achieved.Percentages)

Summary of Data
Measure                                   |       Mean     |      Median
------------------------------------------|----------------|---------------
Purchase Orders                           | $45,342,624.38 | $40,327,080.93
Fully Achieved Key Performance Indicators |      64.93%    |     61.77%


Conclusion
----------
As seen in Figure three, there is a slight negative trend present in the relationship 
between money spent and performance metric achievement. However, with such wide 
variations, it is likely that this trend is not significant. This work represents just 
a first, cursory exploration into the combined datasets including in the SQL file in 
this repo. Further analysis across more of the data available is certainly warranted 
to explore possible trends.


References
----------
District of Columbia Open Data. (2013a). DC Agency Performance Data (KPI’s) - 2013 [Data set]. 
  Retrieved from 
  http://opendata.dc.gov/datasets/aab8213fd7de4e548ffecdd4820815a3_0?uiTab=table&orderByFields=Rating+DESC 
  Access date: March 17, 2016

District of Columbia Open Data. (2013b). DC Purchase Orders - 2013 [Data set]. 
  Retrieved from 
  http://opendata.dc.gov/datasets/abc00ed761234b8387ddaeb4e759fc70_0?orderByFields=Agency+ASC 
  Access date: March 17, 2016

License
-------
We have decided to list this dataset as Attribution 4.0 International. It is free to use 
and adapt even for commercial purposes as long as there is attribution to our original 
dataset.
