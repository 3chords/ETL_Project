# ETL_Project

Team Members: Yuan-Hung Chien, Nick Adams, Jeff Simonson

# Overview:

  * Our ETL project will be combining two CSV files of commercial real estate statistics with labor statistics at the metro level into one table that allows the end user to do a time series analysis using indicators from both tables. We will be using a relational database to build these tables.

  * Steps for ETL project
    * Combine tables on geography (find a way to match using non-matching geographies)
    * Use the CRE stats table as the guide, we want to keep all rows in the CRE stats table and only bring in those records that match from the labor data.
    * We will bring the labor data into the cre stats table so that each time series data point in a row.
    * The labor table data only goes back to 2001 so we need to remove any pre-2001 rows from the CRE stats table.
    * When data is not available we will replace with nulls
    * The data in the labor file is yearly. The data in the CRE stats file is quarterly. We want to eliminate all non Q4 rows in the CRE table because the Q4 data is a snapshot.
    * We may need to identify any columns where there is text and clean it out (e.g. % or commas)
    * We need to create a new 'year' column in the final table
    * We will develop a master table with all metrics
    * We will develop two tables for future query development
    

  * Process thoughts:
    * We will probably need to use a combination of text-to-columns and concatenation like operations on each table independently first to enable the geography key to match.

# Files used in the project
* Source Data:
  * cre_stats_data.csv
  * labor_data.csv

# Files generated from this project
* initial clean-up data (adding MSA Number and name to cre_stat_data according to labor data):
  * new_cre_stats_data2.csv

* data generated from new_cre_stats_data2.csv and labor_data.csv by using excel:
  * new_cre_stats_final_labor_columns.csv

* clean-up csv data generating by Pandas:
  * cre_stats_labor2.csv

* final cleanup-data(cre_stats_labor2.csv droppinh columns: 'ID', 'Yr Lookup', 'Slice', 'Unnamed: 59'):
  * cre_stats_labor3.csv

* final csv file for create sql database:
  * CRE Data.csv

* sql file to create Data base:
  * ETL_Sql_Merge.sql