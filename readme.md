#DCDATADB
A Combination of DC Purchase Order and Performance Metrics Data

-----------
Version 1.0
-----------

Version 1.0 (2015)


-------------------
Description of Data
-------------------
The Washington, DC municipal government posts a great number of datasets to their Open Data ([http://opendata.dc.gov/](http://opendata.dc.gov/)) site. From it, we selected two datasets to combine via MariaDB to aid in their analysis. The first dataset contained all of the purchase orders from 2013 totalling over $2500 (District of Columbia Open Data, 2013a). The second contained various key performance indicators for the various DC government agencies (District of Columbia Open Data, 2013b).Both datasets are organized by agency, by which we could link the two.

---------------------
Why Combine the Data?
---------------------
By combining these datasets, we hoped to establish whether or not any correlation exists between the total purchase orders of a particular agency and their performance metrics performance, i.e., does money spent equal performance gains?

----------
References
----------
District of Columbia Open Data. (2013a). DC Agency Performance Data (KPI’s) - 2013 [Data set]. Retrieved from [http://opendata.dc.gov/datasets/aab8213fd7de4e548ffecdd4820815a3_0?uiTab=table&orderByFields=Rating+DESC](http://opendata.dc.gov/datasets/aab8213fd7de4e548ffecdd4820815a3_0?uiTab=table&orderByFields=Rating+DESC) Access date: March 17, 2016
District of Columbia Open Data. (2013b). DC Purchase Orders - 2013 [Data set]. Retrieved from [http://opendata.dc.gov/datasets/abc00ed761234b8387ddaeb4e759fc70_0?orderByFields=Agency+ASC](http://opendata.dc.gov/datasets/abc00ed761234b8387ddaeb4e759fc70_0?orderByFields=Agency+ASC) Access date: March 17, 2016
