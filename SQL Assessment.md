#### Section A: Concept Application





1\. What is the functional difference between SELECT \* and specifying column names, and when is each preferred?



\-> SELECT \* : This retrieves all columns from table. It is use for exploring the table and Quick testing.

\-> specifying column names : This returns only listed columns. It is use in production application, to create reports, in large tables and join between tables.



2\. Which keyword renames a column in the output, and does this alias change the actual table structure in the database?



\-> The AS keyword is used to rename a column in a query's output. This process, known as aliasing, does not change the actual table structure in the database. The modification is purely temporary and exists only for the duration of that specific query.



3\. Why does wrapping a numeric value in quotes (e.g., '5000') in a WHERE clause create a data type conflict in SQL?



\-> Wrapping a number in quotes (e.g., '5000') creates a string literal instead of a numeric type.



4\. Contrast the results of ORDER BY Profit DESC versus ASC when the goal is to identify the top 10 most profitable orders.



\-> To identify the top 10 most profitable orders (the 10 highest profit values), you must use ORDER BY Profit DESC.



5\. What is the T-SQL equivalent of the LIMIT clause in MS SQL Server, and why does syntax vary across SQL engines?



\-> The primary T-SQL equivalent of the LIMIT clause in MS SQL Server is the TOP keyword. For more advanced scenarios like pagination, SQL Server also uses the OFFSET-FETCH clause.



6\. Explain the logical execution order of a query containing SELECT, WHERE, ORDER BY, and LIMIT clauses.



\-> FROM: The database first identifies the source tables to establish the base dataset.



\-> SELECT: The engine then projects the specific columns or expressions you requested. Because this happens after WHERE, you typically cannot use column aliases defined in SELECT within your WHERE clause.



\-> WHERE: It filters individual rows based on your specified conditions to reduce the amount of data processed in subsequent steps.



\-> ORDER BY: The remaining records are sorted based on the specified columns or expressions.



\-> LIMIT: Finally, the database restricts the result set to the specified number of rows.





#### Section B: Practical Task





1\. Execute a query to retrieve the first 20 records from the orders table to verify data ingestion.





**select \* from orders**

**limit 20;**





2\. Select Order ID, Order Date, Sales, and Profit, applying a column alias to display Sales as Total\_Sales.



**select order\_id, order\_date, profit, sales as Total\_sales from orders;**





3\. Filter the dataset to isolate all high-value transactions where the Sales figure exceeds 5000.



**select \* from orders**

**where sales > 5000;**





4\. Generate a report of the top 10 most profitable orders by sorting the records by Profit in descending order.



**select \* from orders**

**order by profit desc**

**limit 10;**





