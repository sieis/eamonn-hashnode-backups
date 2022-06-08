## Learn SQL By Building A Student Database

## Back to the SSQL 🎶

I'm glad to be back in SQL for this course. Bash was great, but let's make some more databases!

%[https://media.giphy.com/media/Rm1p7xp3Odl2o/giphy.gif]

If you, like me, need a cheat sheet for some of the PostgreSQL commands from the first course, check out my previous article in this series, [A List of PostgreSQL Commands for Beginners](https://blog.eamonncottrell.com/a-list-of-postgresql-commands-for-beginners). I'm pulling it up in a second tab now.

This course has us making a four table student database using data in two .csv files. One has a bunch of student data and the other a bunch of course data:

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1650653499862/WoF2TT6so.png)

The first 30% of the course is a rehash of setting up the tables and beginning to insert data into them.

Then we combine what we learned in the bash course to create a script file.

## New Commands

* `cat <filename>`: prints the contents of a file...can also be used to pipe the contents into a loop to do stuff to each line! 😃
    * for instance, this will read the major and course values on each row and then echo the majors 

```bash
cat courses.csv | while IFS="," read MAJOR COURSE
do
    echo $MAJOR
done
```

* `IFS`: Internal Field Separator. Used to determine word boundaries, and defaults to spaces. So if we want to echo more than the first word of a major, we need to add this to our loop:

```bash
cat courses.csv | while IFS="," read MAJOR COURSE
do
    echo $MAJOR
done
```

* `psql` command can be used to run a single command and exit 
* `TRUNCATE <table_name>`: delete all the data in a table. You can do this for multiple tables at once by separating <table_names> with commas i.e. `TRUNCATE <table_one>,<table_two>`.

For me, the most difficult part in this course has been getting used to the syntax of writing in bash and not making silly mistakes that the CodeAlly tester doesn't like. It continues to be very particular that everything is written precisely as intended.

## Finish Line & One Issue

By the end of this course, we've successfully programmed a bash file to loop through .csv files and add the items therein into a PostgreSQL database.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1654715984759/19QN5kqKd.png align="left")

There is a part two that promises to get a little more advanced by combining information from multiple tables with join commands. 

On the whole, this was a good exercise in a more practical example of building a database as most data will need to come from somewhere like a .csv file in the real world.

I have encountered a nagging issue that is addressed in the freeCodeCamp forums [here](https://forum.freecodecamp.org/t/running-the-relational-database-curriculum-in-your-browser/500231). I've been unable to get a checkmark for completion back on my freeCodeCamp page after finishing the project.

There are several steps to take to remedy this, and it's happened I believe on every project in this certification. However, this is the first time that I've gone through all the steps a few times to no avail. Not a huge deal as it's not measured in the formal certification, but I hate not getting those progress checkmarks! ✔

## Thanks for Reading!

Come say hey 👋 on Twitter, I'd love to meet you and get your feedback: twitter.com/EamonnCottrell