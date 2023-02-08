# Excel Tutorial – How to Clean Data with the TRIM() and CLEAN() Functions

> [Originally published for freeCodeCamp](https://www.freecodecamp.org/news/excel-tutorial-clean-data-with-the-trim-and-clean-functions/)

Without clean data, your spreadsheet is knocking on death's door. In this tutorial, I will show you two fast ways to clean up the data in your Excel or Google Sheets spreadsheet.

When dealing with data sets, especially large ones and/or those that you didn't create, it is likely that you will have to clean the data in large or small ways to get it fully functional.

Both of the built-in functions we'll discuss – `=TRIM()` and `=CLEAN()` – are available in Microsoft Excel as well as Google Sheets. And both of them have the potential to save you a lot of head-scratching.

Let's examine:

1. What do we mean by clean data?
    
2. Why isn't it already clean?
    
3. How do we clean it fast and thoroughly?
    

![a man flipping his messy desk and it becoming magically organized](https://www.freecodecamp.org/news/content/images/2023/01/clean-desk.gif align="left")

*pssst*: I have a video walkthrough at the bottom 👇 of the article too 😉

## **What is Clean Data?**

In Excel and Google Sheets, the data that we work with is located in cells. In a perfect world, these cells contain properly formatted data like numbers, amounts, names, and other pieces of information.

However, we often encounter things in the cells which don't belong and which will prevent us from using that data in the way we need.

Things like non-printable characters, extra white spaces and letters in cells that should contain numbers are a few examples of unclean data which will negatively affect our work.

What are non-printable characters, you ask? They are the first 32 control characters in the ASCII table.

Check out the table below of the ASCII characters. The first 32 are non-printable control codes. These can cause issues if they somehow make it into your data set.

![screenshot of ascii table in Excel](https://www.freecodecamp.org/news/content/images/2023/01/char-1.png align="left")

You can generate this table by using the character function for all the numbers from 0 to 255: `=CHAR(<number>)`.

The other common offenders are spaces that shouldn't be there – leading or trailing spaces in a cell. Or simply spaces in the middle that shouldn't be there.

Compound these finicky cells throughout a spreadsheet that contains thousands or millions of cells, and we've got quite a mess on our hands.

![a woman waving hands and saying, "this is a mess"](https://www.freecodecamp.org/news/content/images/2023/01/a-mess.gif align="left")

## **Why Isn't the Data Clean?**

Because we live in a fallen world.

🤣 Well, it's not that dramatic. But there can be many reasons the data isn't already clean. Many times human error is the culprit.

Whoever or wherever you're getting your data from simply made some mistakes with it before you got your hands on it.

Or maybe you messed it up when you started to manipulate the data.

As we'll see in the example below, the data could be perfectly fine wherever you're getting it from on the internet. But then when you import it into your spreadsheet, the conversion from HTML to Spreadsheet brings in a bunch of non-printable characters and spaces.

And, of course, because we're dealing with computers and people and data, we may never figure out why the data we've received isn't clean. It simply isn't. And despite our confusion, we have to clean it up to use it and extract meaning from it.

![Obi Wan visibly confused](https://www.freecodecamp.org/news/content/images/2023/01/confusion.gif align="left")

## **How to Clean Data in Excel and Google Sheets**

Let's first get some data. In both Excel and Google Sheets, we can import data from the web. I want to bring in a table of Recipes and Ingredients from a video game website that looks like this online.

Here's Link...I mean, [here's the link](https://www.ign.com/wikis/the-legend-of-zelda-breath-of-the-wild/All_Recipes_and_Cookbook). ⚔️

![Zelda recipe table](https://www.freecodecamp.org/news/content/images/2023/01/image-153.png align="left")

To address the obvious question first: yes, I could just copy and paste the table. And, yes, it will in this case paste the table straight into Excel.

But it'll also bring in the pictures which I don't need, the links which I don't want, some formatting that I'll have to reset, and potentially some of the non-printable characters and/or spaces that we'll discuss below.

![Table of Recipe ingredients copied straight off website](https://www.freecodecamp.org/news/content/images/2023/01/image-154.png align="left")

Above is what it will look like after copying and pasting. But we are interested in preserving data and cleaning it, so we'll import it another way for the sake of the rest of our discussion.

If you're using Excel, it has some pretty robust cleaning features out of the box. When importing data from IGN, we enter the address where it lives, and it will pull down any data that it detects as available for import.

![screenshot of data import from web in Excel](https://www.freecodecamp.org/news/content/images/2023/01/import.png align="left")

Let's get the table of Poultry and Meat Entrée receipts from Zelda: Breath of the Wild.

The Navigator window shows us a handy list of data tables detected on the page as well as a preview pane on the right that can be toggled between table and website views.

![Excel data import navigator window screenshot](https://www.freecodecamp.org/news/content/images/2023/01/recipe-table-1.png align="left")

### **Excel Power Query**

Once we've selected our data and loaded it, we'll have imported a table into our spreadsheet just fine. Excel's Power Query features allow us to then go into this particular table and extract the values in the Ingredients column into a list of items delimited by a selector of our choice.

In other words, Excel is smart enough to extract the individual list items in the Ingredients column and put them in a cell one by one and separated by commas (or whatever we select to separate them).

The following three screenshots show this process:

![Screenshot of Excel Power Query menu](https://www.freecodecamp.org/news/content/images/2023/01/expand-values.png align="left")

![Screenshot of delimiter for expanded values](https://www.freecodecamp.org/news/content/images/2023/01/delimiter.png align="left")

![Screenshot of Expanded list values in Ingredient column](https://www.freecodecamp.org/news/content/images/2023/01/extracted.png align="left")

The end result is a comma separated list of values that is seemingly pretty clean. We can then split it up by using the `=SPLIT()` function into separate cells if we choose, or simply use it as is.

This is an ideal situation. But what if we encounter those spaces and non-printable characters?

### **Clean and Trim Functions**

Here's a screenshot of the same table when imported into Google Sheets with `=IMPORTHTML()`. It pulls the data correctly, but you can see the extra spaces that were also brought into the sheet.

![Imported data from webpage in Google Sheets](https://www.freecodecamp.org/news/content/images/2023/01/sheets-trim.png align="left")

By using `=CLEAN()` on the ingredients cells, we can get rid of some non-printable carriage returns causing the line breaks.

![Table after Cleaning cells](https://www.freecodecamp.org/news/content/images/2023/01/justclean.png align="left")

By using `=TRIM()` on the cells, we can get rid of all the leading spaces.

![Table after Trimming white spaces](https://www.freecodecamp.org/news/content/images/2023/01/justtrim.png align="left")

And by nesting the two with `=CLEAN(TRIM())`, we can do both. The result is a list of values separated by dashes. Similarly to our resultant table in Excel where we were left with a comma-separated list, we can then go and `=SPLIT()` these values further if need be.

![Table after cleaning and trimming at once](https://www.freecodecamp.org/news/content/images/2023/01/both.png align="left")

These functions work the same in Excel, but for illustrative purposes we used Google Sheets since it wasn't able to import the data as neatly there.

## **Sample Spreadsheet & Video Walkthrough**

[Here is a link to the sample Google Sheet](https://docs.google.com/spreadsheets/d/11j6ajxvN6dSd9U7y6LQT6IhAJvM99jRGPFcDIBtBMkM/edit?usp=sharing) that I made for this tutorial.

The first page is a table of the non-printable characters.

![image-155](https://www.freecodecamp.org/news/content/images/2023/01/image-155.png align="left")

And the second page is the Zelda example we talked about. Feel free to make a copy of this spreadsheet if you'd like to mess around with it further (File -&gt; Make a copy).

We'll be building a really cool project with some of this Zelda data soon...[follow me on YouTube](https://www.youtube.com/@eamonncottrell) to keep an eye out for that.

%[https://youtu.be/mgAHQWrTcCg] 

## **Thanks**

Thanks for reading, and I hope this has been useful for you. Come say hey 👋 on [LinkedIn](https://www.linkedin.com/in/eamonncottrell/) and [YouTube](https://www.youtube.com/@eamonncottrell), and I'll talk to you in the next article!