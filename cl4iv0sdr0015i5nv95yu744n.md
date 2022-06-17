## More PostgreSQL Commands for freeCodeCamp Projects

## More Commands 🌟

We're creating more bash files to do some of the heavy lifting and querying for us. Here are a list of commands used in Learn SQL by Building a Student Database: Part 2. 
They'll be useful to (definitely) my future self and (hopefully) you! 😁👊

![more.gif](https://cdn.hashnode.com/res/hashnode/image/upload/v1655401208251/I2a8KSAGX.gif align="center")

### Conditions ❔
There are all sorts of ways to ...sort 😊 and specify query results 

1. `LIKE` && `NOT LIKE`: use this to query a table and find matches to certain criteria. `SELECT * FROM courses WHERE course LIKE '_lgorithms'`; will match any row with a word that has exactly one letter before the 'lgorithms' part. 
1. `...LIKE '%lgorithms'` will not constrain it to one letter in front of the 'lgorithms' part. So `%` lets anything come before.
1. `ILIKE` will ignore case. So you don't need to specify capital or lower case.
1. `AND` and `OR` conditions will enable you to combine query criteria. e.g. `SELECT * FROM courses WHERE course LIKE '% %' AND course NOT ILIKE '%b%';`. This will select rows with a space in it and without a capital or lowercase 'b' in it.
1. `echo -e`: this lets you use the escape character like '\n' to create a newline.
1. `IS NULL`: let's you query fields that are blank or empty. e.g. `SELECT <column_name> FROM <table> WHERE <column> IS NULL`.
1. `IS NOT NULL`: let's you query fields that are not blank or empty.
1. `ORDER BY <column_name>`: specifies the order in which results are displayed. Defaults to ascending (`ASC`) order. add `DESC` (descending) to the end of the query to reverse that displayed order. e.g. `SELECT * FROM <table> ORDER BY <column> DESC`.
1. To order by multiple columns, add those columns separated by commas at the end of the `ORDER BY` query. e.g. `...ORDER BY <column_name1>,<column_name2>`. Now, if there are matching values from ordering by column1, they will order by column2. *if you specify `DESC` while using multiple ordering columns, you will do that immediately following each column name in the query.* `ORDER BY <column_name1> DESC, <column_name2> DESC`.
1. `LIMIT`: limits the returned number of rows from a query. The order of keywords matters in the query, too: You cannot put `LIMIT` before `ORDER BY` or either of them before `WHERE`.

### Mathematics ➗

1. `MIN` && `MAX`: two of many mathematic functions. MIN & MAX find the lowest or highest values, respectively, in a column. e.g. `SELECT MIN(<column_name>) FROM <table>`
1. `SUM`: sums the values of a column. 
1. `AVG`: averages the values in a column.
1. `CEIL` && `FLOOR`: rounds results to the nearest whole number. `CEIL` rounds up, `FLOOR` rounds down.
1. `ROUND` simply rounds to the nearest whole number. Add a comma and a number to round to a specified number of decimal places. e.g. `SELECT ROUND(AVG(major_id),5)`
1. `COUNT`: how many entries in a table for the column. e.g. `SELECT COUNT(*) FROM majors` counts total rows and `SELECT COUNT(gpa) FROM students` counts only those rows with non-null values in the gpa column.
1. `DISTINCT`: shows only the unique values from a query. e.g. `SELECT DISTINCT(<column_name>) FROM <table>`.
1. `GROUP BY`: works similarly to `DISTINCT`. e.g. `SELECT <column_name> FROM <table> GROUP BY <column_name>`. The advantage of using `GROUP BY` is that it allows you to add any of the aggregate functions like `MIN`, `MAX`, and `COUNT` to get more info from your results. `SELECT COUNT(*) FROM <table> GROUP BY <column_name>` will count the number of distinct column values in that query.
1. `HAVING`: use at the end of a query where condition must be an aggregate function with a test. e.g. `HAVING COUNT(*) > 0`
1. `AS`: rename a column. e.g. `SELECT <column> AS <new_column_name>`

## JOINS

We tackled only FULL JOINS (and only those briefly) in my initial list of commands [here](https://blog.eamonncottrell.com/a-list-of-postgresql-commands-for-beginners). As you might imagine, there's plenty more to do with JOINS.

1. `LEFT JOIN`: gets all the rows from the left table (the table mentioned first (furthest to the left on the line) in the query). e.g. `SELECT * FROM students LEFT JOIN majors ON students.major_id = majors.major_id`
2. `RIGHT JOIN`: same thing only returns rows from right table.
3. `INNER JOIN`: combines the two above. Will return rows from LEFT table if they have a RIGHT table counterpart and visa versa.
4. `USING`: keyword you can use in the event that the foreign key has the same name in each table. e.g. `SELECT * FROM <table_1> FULL JOIN <table_2> USING(<column>)`


