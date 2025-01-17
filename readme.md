#DC KPI and PO DB
A Combination of DC Purchase Order and Performance Metrics Data

-----------
Version 1.0
-----------

Version 1.0 (2016)

-------------------
Description of Data
-------------------
The Washington, DC municipal government posts a great number of datasets to their [DC Open Data](http://opendata.dc.gov/) site. From it, we selected two datasets to combine via [MariaDB](https://mariadb.org/) to aid in their analysis. The first dataset contains all of the purchase orders from 2013 totalling over $2500 (District of Columbia Open Data, 2013a). The second contains various key performance indicators (KPI) for the various DC government agencies (District of Columbia Open Data, 2013b). These have both been converted into two relational tables. We constructed a third table, "agencies," by which we could link the two datasets based on shared agencies.

---------------------
Why Combine the Data?
---------------------
By combining these datasets, we hoped to establish whether or not any correlation exists between the total purchase orders of a particular agency and their performance metrics performance, i.e., does money spent equal performance gains?

---------------
Data Processing
---------------
The process by which the two datasets were merged into MariaDB is documented in [this Word Document](dcdatadb_processing_documentation.docx). The resultant database was dumped into a single .sql file [here](databasedump.sql).

-------------
Data Analysis
-------------
For analysis of the data present in the two datasets, we combined them on basis of the common variable named ‘Agency’. We then tried to analyze if there is any relationship between the total amount spent (P.O.Totals) by an agency and the percentage of “Fully Achieved” KPIs. First, recognizing the extraordinarily wide range of PO Totals, we narrowed our scope to only review Agencies with totals between $10 and $100 million in PO Totals. We then calculated the percentage of "Fully Achieved" KPIs in with respect to the total performance rating amongst categories "Fully Achieved", "Partially Achieved", and "Not Achieved." We then created a new Excel worksheet containing the name of agency, the total amount spent by agency and the percentage of “Fully Achieved” performance ratings.
	
###Descriptive Analysis
To begin the analysis, we used the command `summary()` in R to determine the descriptive analysis and `hist()` to plot histograms (Figures 1 and 2). Finally, in order to then determine the relation between the amount spent by an agency and the performance rating achieved by an agency, we then used a scatter plot for both variables using the R command: `plot()` (Figure 3).

**Commands:**

    summary(sample$P.O..Totals)
    summary(sample$Fully.Achieved.Percentages)
    hist(sample$P.O..Totals)
    hist(sample$Percentages)
    plot(sample$P.O..Totals, sample$Fully.Achieved.Percentages)

###Summary of Data
Measure|Mean|Median
-------|----|------
Purchase Orders|$45,342,624.38|$40,327,080.93
Fully Achieved Key Performance Indicators|64.93%|61.77%


![histogram of total amount spent](assets/figure1-pototalshistogram.png)
*Figure 1. Histogram of total amount spent.*

![Histogram of fully achieved performances](assets/figure2-fullyachievedbyagency.png)
*Figure 2. Histogram of fully achieved performances.*

![Relation between amount spent and performance metric](assets/figure3-scatterplot.png )
*Figure 3. Relation between amount spent and performance metric.*

----------
Conclusion
----------
As seen in Figure three, there is a slight negative trend present in the relationship between money spent and performance metric achievement. However, with such wide variations, it is likely that this trend is not significant. This work represents just a first, cursory exploration into the combined datasets including in the SQL file in this repo. Further analysis across more of the data available is certainly warranted to explore possible trends.

------------------------
How Do You Use the Data?
------------------------
The combined dataset is pretty straightforward to use. Simply spin up a relational database (this has only been tested with MariaDB/MySQL), choose a schema, and run the included .sql script!

----------
References
----------
District of Columbia Open Data. (2013a). DC Agency Performance Data (KPI’s) - 2013 [Data set]. Retrieved from [http://opendata.dc.gov/datasets/aab8213fd7de4e548ffecdd4820815a3_0?uiTab=table&orderByFields=Rating+DESC](http://opendata.dc.gov/datasets/aab8213fd7de4e548ffecdd4820815a3_0?uiTab=table&orderByFields=Rating+DESC) Access date: March 17, 2016

District of Columbia Open Data. (2013b). DC Purchase Orders - 2013 [Data set]. Retrieved from [http://opendata.dc.gov/datasets/abc00ed761234b8387ddaeb4e759fc70_0?orderByFields=Agency+ASC](http://opendata.dc.gov/datasets/abc00ed761234b8387ddaeb4e759fc70_0?orderByFields=Agency+ASC) Access date: March 17, 2016

--------------------
Citation and License
--------------------
Porter, C. E. & Devkar, U. (2016). DC KPI and PO DB [Data set]. 
  Retrieved from https://github.com/cedporter/dckpiandpodb

<a rel="license" href="http://creativecommons.org/licenses/by/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by/4.0/88x31.png" /></a><br /><span xmlns:dct="http://purl.org/dc/terms/" href="http://purl.org/dc/dcmitype/Dataset" property="dct:title" rel="dct:type">DCKPIandPODB</span> by <a xmlns:cc="http://creativecommons.org/ns#" href="https://github.com/cedporter/dckpiandpodb" property="cc:attributionName" rel="cc:attributionURL">C. Edward Porter / Utkarsha Devkar</a> is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by/4.0/">Creative Commons Attribution 4.0 International License</a>.<br />Based on a work at <a xmlns:dct="http://purl.org/dc/terms/" href="http://opendata.dc.gov/" rel="dct:source">http://opendata.dc.gov/</a>.
