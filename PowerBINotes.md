# DATA ANALYSIS

- data analysis is the process of collecting , cleaning , transforming and modeling data to discover meaningful and useful information.

- Power BI is a tool used by analysts to create and manage reports 

- The flow of Power BI is:

1. Connect to data with Power BI Desktop.
2. Transform and model data with Power BI Desktop.
3. Create visualizations and reports with Power BI Desktop.
4. Publish report to Power BI service.
5. Distribute and manage reports in the Power BI service.

The Power BI service also allows you to create high-level dashboards that drill down to reports, and apps to easily group related reports to users in a simple format.

- building blocks of power bi are semantic models and visuals.

- Power Bi service is sued to distribute content to consumers and use reoprts to create dashboards.

# SEMANTIC MODEL
- consists of all connected data, transformations, relationships and calculations.

- first connect to data, transform data, and create relationships and calculations to create a semantic model.

- dashboards can be created after publishing reports to power bi service

- dashboards contain single page made up of tiles.

- tiles are added by pinning a visual in a report to dashboard. Tiles are not interactive.



# WORKSPACE

- reports are published in a WORKSPACE in power BI service  
- we can create apps in a WORKSPACE
- apps are simplified interface to access reports and dashboards
- app configuration -> set up the app , select the content to include and choose audience
- whenever items in workspace are changed, app must be updated -> allows you to control what version of content is visible to audience
- apps are ideal for sharing

- template apps -> use an existing app that suits your needs and then connect your data.

- we can configure scheduled refreshes of semantic models in power bi service for ever changing data.


# DYNAMIC REPORTS

- dynamic reports are reports in which the data can be changed by a developer according to user specifications.



# QUERY FOLDING

- Query folding in Power BI refers to the ability of Power Query to push data transformation logic back to the source system (such as a database) rather than performing these transformations locally. 
- It allows the Power Query engine to translate the transformation steps into queries that the data source can execute, improving performance and efficiency.
-  if you can translate a transformation into a Select SQL statement, which includes operators and clauses such as GROUP BY, SORT BY, WHERE, UNION ALL, and JOIN, you can use query folding.


## QUERY DIAGNOSTICS

- can be accessed through tools in query editor 
- start diagnostics when you start making edits and stop diagnostics when done => this gives the length of time taken to run the step


# ERRORS FIX
- if power Bi shows error "We couldn't find any data formatted as table" then go to excel select the data you want to import and press CTRL+T to make first row as headers.

- Couldn't find file -> change the source of the file in tansform data -> gear icon next to source


- Data type errors -> when we import to poer bi the columns might appear blank beacause of an error in interpreting the data type in power bi -> specify the correct type at data source to avoid errors

use 
```sql
SELECT CAST(CustomerPostalCode as varchar(10)) FROM Sales.Customers
```



- column distribution in view ribbon gives the number of distinct and unique values in a column -> if distinct and unique number is same then all the values in the column are unique


- tables are called as queries in power bi

# TRANSFORM
## PIVOT COLUMNS

- used to transform rows into columns based on the values of a specific column 
- You can use the Pivot Column feature to convert your flat data into a table that contains an aggregate value (Count, Minimum, Maximum, Median, Average, Sum) for each unique value in a column. 
- How to implement?
    - go to tranform
    - select the column you want to pivot (their row values will be column headers)
    - select pivot columns
    - select the column to provide the values for new columns
    - in advanced select the aggregate function you want to implement


- rename query names an d column names to relevant names
- we can replace values in a column using replace values in transform ribbon

- remove duplicates -> right click on header name 


## COMBINING DIFFERENT TABLES

- two ways : merging or appending

- appending -> you'll be adding rows of data to another table ,when you combine the queries, the pertinent columns that you require in your combined table must be named the same in your original data tables to see one consolidated view.

- to append -> Home -> append queries -> select the tables to want to append 

- merging -> you'll be adding columns from one table into another
- to merge you must have a common column that is the key between two tables

- You can also choose how to merge the two tables together. These join options include:

     1. Left Outer - Displays all rows from the first table and only the matching rows from the second.

     2. Full Outer - Displays all rows from both tables.

     3. Inner - Displays the matched rows between the two tables.



## DATA PROFILING
- determining anomolies, examining and developing underlying data structures and querying data statistics (row counts, value distributions, maximum, minimum, average)
- Distinct values are all the different values in a column(total count of how many values are present), including duplicates and null values, while unique values do not include duplicates or nulls(how many of those values only appear once).
- value distribution graph gives the count for each distinct value in that column.


# STAR SCHEMA

- design principle
- classifies model tables as fact or dimension
- in a diagram fact table forms center of star
- dimension tables are placed around fact table(points of the star)

## FACT TABLES
- stores rows that represent observations that record a specific business activity
- contains quantitative data 
- stores vast amount of data
- Eg : sales revenue, quantity, profit
- can be summarized or aggregated ( total sales, average profit)

## DIMENSION TABLES
- contains descriptive attributes 
- provides context to facts
- Eg: product names, customer details
- primary key that related to fact table
- relatively smaller
- fact table refere to dimension tables using foreign key
- use to filter and group data

- Example Query:
To calculate total sales by category, the SalesAmount from the fact table can be joined with the Category from the product dimension table.

- dimension are related to fact using one-to-many-relationships
- when filters are applied to dimension table columns, related facts are summarized
