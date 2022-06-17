## How to Query Data in Google Sheets

> This article appeared first on [freeCodeCamp's news publication](https://www.freecodecamp.org/news/querying-like-an-sql-boss-in-google-sheets/).

I built a spreadsheet and wanted to display some of the data in a small table which would update based on the day of the week.

After some digging, querying seemed the best option to pull this off.

In this article, you'll learn several things about Google Sheets tables, functions, queries, data validation and formatting including:

1. Creating a clean, usable data table.
1. Creating a data validation drop down list
1. Naming ranges for easier use and cleaner data management
1. Querying basics including SELECT, WHERE and the TEXT() and TODAY() functions
1. The funky syntax to reference cells within Google Sheet queries
1. Where to go in the official docs for further information.

## Google Sheets is Similar to SQL

Google Sheets indeed has a built in "Google Visualization API Query Language". Check out the docs [here](https://developers.google.com/chart/interactive/docs/querylanguage).

Some of the syntax is the same and much of the functionality is similar to SQL, so you should pick it up quickly if you are familiar with SQL at all.

I know but a little when it comes to SQL, but I was able to parse my way through some basic queries with little trouble.

In fact, the thing that gave me the most trouble was **cell referencing syntax**. And I hope this post can save you some head scratching that I went through today.

![barney-head-scratch.gif](https://cdn.hashnode.com/res/hashnode/image/upload/v1655486619777/ZYWm1JZLk.gif align="left")

## Setup Your Table

First things first: get all the data in a well organized table. This is sometimes the hardest part of any data analysis: simply getting the data in an orderly, usable format.

![neat.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1655487140364/iQWEG--mO.png align="left")

I used data validation for the days of the week to ensure I didn't have a typo in there since our query will depend on those days.

![validate.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1655487787872/sZeOuw67B.png align="left")

## Create a Named Range

Select the entire table to create a named range. This will make things cleaner and easier in the next step. It's good practice to keep data as tidy as possible.

![query.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1655487816830/7_j_wDbGu.png align="left")

Confirm and name the range to save it.

![confirm.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1655487940991/g98mgMZWk.png align="left")

## How to Write the Query

Now, let's make another sheet to put our query into. I only need two columns for our data: one for the person and one for the task. Make room for more if your data requires it.

The first step requires a little trick to make the current day display when the sheet is loaded and for this to be used in our query.

There is a built-in `=Today()` function, but using it alone is not enough even when you change the formatting. They query won't recognize it as matching the days of the week text in our table.

Instead, wrap the `Today()` function inside the `Text()` function as shown below. The `Text()` function accepts a number and a format as arguments. When we pass it `Today()`, it can convert that date number into text using the format "dddd". Neat, right? 😊

![functions.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1655488026267/BLgJRauSw.png align="left")

In Google Sheets, `=QUERY` is also a built in function. As you type it in the cell (`B22` in my example) you can click the drop down arrow in the top right to get more information on the parameters accepted.

![more info.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1655488054236/23ycBqL7V.png align="left")

We'll select our data. Type the name of the range you created and it will automatically select that table.

![range.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1655488085416/UOfYkGIrj.png align="left")

You can manually select the range for the table to query if you choose. But you want to be as awesome as possible, so use that named range! 🙌

We want to select and return the first two columns (the names and tasks) in our data sheet based on the fourth column (the day of the week).

The query reads `=QUERY(heat,"select B,C where D='"&B21&"'",1)`.

And yes, that nastiness with the single quotes, double quotes and ampersands is necessary for the conditional statement we are creating.

We're telling the query to match the D column in our data sheet with the value in `B21` which is now text thanks to our previous formula manipulating the day of the week.

The syntax to match the text in the cell is gross, but it's just how you have to do it.

![query-function.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1655488113233/-vxa-yH5c.png align="left")

That last parameter `1)` is letting the query know that there is one row of headers to display (name, task).

And, voilà! We've got ourselves an automatically updating task list based on the current day of the week. All that's left is cleaning up the final result! 🎁

![format.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1655488142221/w6pMMF_dS.png align="left")

##Official Examples

I referenced [this article](https://support.google.com/docs/answer/3093343?hl=en) from the QUERY function page on Google Support to learn, and it has a Google Sheet you can copy with a bunch of examples in it. Super helpful.

![ex.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1655488178956/fFt7ObLQf.png align="left")

## My Example Spreadsheet

[Here is the sheet](https://docs.google.com/spreadsheets/d/1oO5SMyVlk2KbqXmW534JH2kYSoqfP1IgVf80KRwpQgY/edit#gid=0) I built for this article. You are free to make a copy of it and use yourself.

![copy.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1655488214144/bQzdWJeF6.png align="left")

## Thanks for Reading!

I write about web design and development from a solopreneur's perspective at https://blog.eamonncottrell.com/ and you can find me on Twitter: https://twitter.com/EamonnCottrell

Have a great one! 🎉

![bye.gif](https://cdn.hashnode.com/res/hashnode/image/upload/v1655488225692/RweE5Hosk.gif align="left")
