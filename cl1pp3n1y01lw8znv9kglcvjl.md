## A List of PostgreSQL Commands for Beginners

## Yes, My First-ish Time

I've dabbled with SQL a couple times, but never truly dove all the way in. I took [Google's Data Analytics](https://grow.google/certificates/data-analytics/#?modal_active=none) certification last year, and it gave a nice cursory overview of SQL, Big Query, Tableau and the R language. But, I'm ready to sink my teeth into understanding how to use PostgreSQL out in the wild.

## It's in Beta

I'm firing up [this certification](https://www.freecodecamp.org/learn/relational-database/) now, and I'm encouraged that it will be more impactful. Everything I've done on freeCodeCamp has been focused on learning through building. The projects are extensions of the lessons that make you actually have to re-learn what you've just been over in order to complete. 

The browser version is in beta still, but I had significant issues on my PC when I tried to go through the earlier version solely through VS Code. I'm stoked to be starting now.

I've already been through the introduction to Bash section which was a nice overview of navigating the command line. If you're familiar at all with this type stuff, it won't take you longer than 20-30 mins to complete.

### A Word of Caution

After completing 70% of the project, I encountered issues logging back in to finish it. I've had to delete the container and start from scratch. **If you work on this certificate while it's in Beta, I recommend leaving each project open in your browser from start to finish.**

## Mario Database


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1649005400878/O3C1C9YuT.png)

### Some PostgreSQL commands I'm learning in this lesson:

> I'm having to adjust to using the backslash `\` rather than the forward slash `/` for these commands

1. `CREATE DATABASE your_db_name;` = yes, this indeed creates a new database 😀
1. `DROP DATABASE your_db_name;` = delete your_db_name.
1. `\l` = lists the databases 
![list of databases](https://cdn.hashnode.com/res/hashnode/image/upload/v1649007630717/pgdGzETzH.png)
1. `\c your_db_name` = connects to a your_db_name database
1. You can tell which database you're currently connected to based on what the terminal prompt says...i.e. I'm connected to `second_database` in the screenshot below:
![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1649005956123/dn8Tz1xjR.png)
1. `\d`: display the tables in the database you're currently connected to. 
![displays tables in database](https://cdn.hashnode.com/res/hashnode/image/upload/v1649007576392/P5-E6jUJp.png)
1. `\d your_table_name`: displays the details of `your_table_name` ![displays details of a table](https://cdn.hashnode.com/res/hashnode/image/upload/v1649007535723/3pZ8yRGob.png)

1. `CREATE TABLE your_table_name()`: yep, create a table
1. `DROP TABLE your_table_name`: deletes the table
1. `ALTER TABLE table_name ADD COLUMN column_name DATATYPE;`: creates a new column in your table
1. `ALTER TABLE table_name DROP COLUMN column_name`: removes a column
1. `ALTER TABLE table_name RENAME COLUMN old_name TO new_name`: renames a column.
1. `ALTER DATABASE database_name RENAME TO new_database_name`: renames database.
1. `INSERT INTO table_name(column_1,column_2...) VALUES(value_1, value_2...)`: insert the data via rows into the tables. 
![row of data values in table](https://cdn.hashnode.com/res/hashnode/image/upload/v1649008296545/GQop6MX1O.png)
1. `SELECT column(s) FROM table_name;`: view data in table. (use an `*` between SELECT and FROM to select all the columns)
![view data from table](https://cdn.hashnode.com/res/hashnode/image/upload/v1649009102890/BXUUXhQZd.png)
1. `DELETE FROM table_name WHERE condition`: deletes a row where the condition is met. i.e. condition(username='Luigi') 
![deleted row](https://cdn.hashnode.com/res/hashnode/image/upload/v1649009377587/16smZ3jf3.png)
1. `UPDATE table_name SET row_to_update = new_value WHERE condition`: update a value in a row.
![update value](https://cdn.hashnode.com/res/hashnode/image/upload/v1649030923990/-FFb8rpjP.png)
1. `SELECT columns FROM table_name ORDER BY column_name;`: put stuff in proper order.
1. `ALTER TABLE table_name ADD PRIMARY KEY(column_name);`: sets a primary key to one of the columns.
1. `ALTER TABLE table_name DROP CONSTRAINT constraint_name;`: drop a constraint (like removing a primary key)
1. `ALTER TABLE table_name ALTER COLUMN column_name DROP CONSTRAINT constraint_name;`: drop a constraint from a column in the table.
1. `ALTER TABLE table_name ADD COLUMN column_name DATATYPE REFERENCES referenced_table_name(referenced_column_name);`: Holy Toledo! This is how you set a foreign key. So it links tables together. The column added links to the referenced column in the referenced table. 
1. `ALTER TABLE table_name ADD FOREIGN KEY(key_name) REFERENCES(referenced_table_name(referenced_column_name);`: Add a foreign key after the fact instead of with the creation of the column.
1. `ALTER TABLE table_name ADD PRIMARY KEY(column1, column2);`: Creates a composite foreign key from values from two columns.
1. `FULL JOIN`: This is where some magic happens. The full command is here: `SELECT columns FROM table_1 FULL JOIN table_2 ON table_1.primary_key_column = table_2.foreign_key_column;`: This hooks up two columns that we previously linked via keys.

This is awesome! Two previously separate tables are now joined: 

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1649363289895/baPSI_tUC.png)

👇

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1649363259311/bHlYL6Ey-.png)

> Don't forget semicolons at the end of the lines. 

### Cool Datatypes & All in One Commands

1. `VARCHAR(n)`: a short string consisting of *n* number of characters.
1. `SERIAL`: an integer that automatically increments when rows are added. See pic example below. The character_id is automatically assigned a value when I add a row of data.
![serial.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1649030226037/q5BRgi1mm.png)
1. `NUMERIC(4,1)`: decimal data type. In this example, it has up to four digits and one of them has to be to the right of the decimal. 
1. `CREATE TABLE table_name(column_name DATATYPE CONSTRAINTS)`: a one-liner to create a table with column and constraints.
1. **Junction Table**: this creates two "one-to-many" relationships between tables. It's a table created to sort of 'glue' two other tables together.

## Fun With Databases

I honestly had a blast going through the basics of PostgreSQL in this little project. Looking forward to continuing with more of the [Relational Database Certificate](https://www.freecodecamp.org/learn/relational-database/) on freeCodeCamp.

Thanks for reading; you can find me over on Twitter, and I'd love if you said hey! 😊

Have a great one! 👋