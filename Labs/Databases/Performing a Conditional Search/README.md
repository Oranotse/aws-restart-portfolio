# Performing a Conditional Search 🔍

The detailed steps for this lab can be seen clearly in the folder titled **Lab Steps Screenshots**.

## What This Lab Is About

In this lab, I worked with a relational database called **world** that contains three tables: `city`, `country`, and `countrylanguage`. The goal was to write SQL queries using the `SELECT` statement and `WHERE` clause to filter records from the `country` table based on different conditions. According to AWS, using the `WHERE` clause allows you to define conditions that records must match before being included in the result set, which makes it easier to work with large datasets by reducing the number of records returned.

## Connecting to the Command Host

I started by connecting to an **EC2 instance** called the **Command Host**, which had a database client already installed. In the **EC2 Management Console**, I selected the Command Host instance and clicked **Connect**, then chose the **Session Manager** tab and clicked **Connect** to open a terminal window. Once connected, I ran `sudo su` to switch to the root user and `cd /home/ec2-user/` to navigate to the home directory. I then connected to the MySQL database by running `mysql -u root --password='re:St@rt!9'`, which logged me into the database server.

## Querying the World Database

I ran `SHOW DATABASES;` to verify that the **world** database was available, then ran `SELECT * FROM world.country;` to review the table schema and see all the records in the `country` table. The result set was very large, so I needed to use a `WHERE` clause to filter the data and make it easier to work with.

### Using the WHERE Clause with AND Operator

To reduce the number of records, I ran a query that combined two conditions using the `AND` operator. The query was `SELECT Name, Capital, Region, SurfaceArea, Population FROM world.country WHERE Population >= 50000000 AND Population <= 100000000;`, which returned only countries with populations between 50 million and 100 million. This demonstrated how the `>=` and `<=` operators can be used together to define a range condition.

### Using the BETWEEN Operator

Instead of using `>=` and `<=`, I rewrote the same query using the `BETWEEN` operator, which makes the query easier to read. The query was `SELECT Name, Capital, Region, SurfaceArea, Population FROM world.country WHERE Population BETWEEN 50000000 AND 100000000;`, and it returned the same result set as the previous query. The `BETWEEN` operator is inclusive, meaning it includes both the starting and ending values in the range.

### Using the LIKE Function with Wildcards

I used the `LIKE` function to search for string patterns in the `Region` column. The query `SELECT sum(Population) from world.country WHERE Region LIKE "%Europe%";` returned the total population of all European countries by using the `SUM` function. The percent symbol (`%`) is a wildcard character that represents any number of characters before or after the word "Europe", so it matched regions like "Southern Europe", "Eastern Europe", and "Western Europe".

### Using the AS Operator for Column Aliases

To make the output easier to read, I added a column alias using the `AS` operator. The query `SELECT sum(population) as "Europe Population Total" from world.country WHERE region LIKE "%Europe%";` returned the same information as the previous query, but the result column was labelled "Europe Population Total" instead of just showing the raw `sum(population)`.

### Using the LOWER Function for Case-Insensitive Searches

To perform a case-insensitive search, I used the `LOWER` function in the `WHERE` clause. The query `SELECT Name, Capital, Region, SurfaceArea, Population from world.country WHERE LOWER(Region) LIKE "%central%";` converted the `Region` column to lowercase before comparing it to the string "%central%", which ensured that regions like "Central America" and "Central Africa" were both returned regardless of how the data was stored in the database.

## Challenge: Querying North America

For the challenge, I needed to write a query that returned the sum of the surface area and sum of the population of North America. I first queried the table to see how North America was represented in the `Region` column, then wrote a query that used the `LIKE` function to match the region and the `SUM` function to calculate the totals.

## What I Learned

This lab taught me how to use the `WHERE` clause to filter records based on different conditions, which is essential when working with large datasets. I learned the difference between using `>=` and `<=` operators versus the `BETWEEN` operator, and how the `BETWEEN` operator makes queries easier to read. The `LIKE` function with wildcard characters (`%`) is very useful for searching string patterns, and the `AS` operator helps make query results more understandable by creating column aliases. I also learned that using functions like `LOWER` in the `WHERE` clause can help with case-insensitive searches, which is important when you are not sure how the data is stored in the database. Working with **Session Manager** to connect to the Command Host and running SQL queries directly on a MySQL database gave me hands-on experience with database operations in AWS. 🎉
