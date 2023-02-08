# How to Calculate Percentage Differences Between Two Numbers in Excel - Cell Percentage Change Tutorial

Spreadsheets are powerful and awesome. 💪

In this tutorial I will show you four ways to find the percentage difference between two numbers in Excel. I'll also show you how to use custom functions in Google Sheets. 👍

The four techniques (and one bonus) we'll use are:

1. Using a Formula (lvl 1️⃣ easy mode)
    
2. Using the LAMBDA FUNCTION + Name Manager (lvl 2️⃣ normal mode)
    
3. Using Visual Basic for Applications (VBA) (lvl 3️⃣ hard mode)
    
4. Using the Office JavaScript API (lvl 4️⃣ ultra-mode)
    
5. Using Custom Functions with Google Sheets (💥 bonus level)
    

## **Formula for Percentage Change Between Two Numbers in Excel**

The formula is the first thing most people will reach for when making a calculation in Excel. It allows us to make explicit calculations using data in cells.

Suppose we have sales data for one year in cell `B3` and sales data for the second year in cell `C3`. By typing the formula below we can calculate the percentage difference from the first year to the second:

```javascript
=(C3-B3)/B3
```

![formula for percentage change between two numbers in Excel](https://www.freecodecamp.org/news/content/images/2022/12/image-62.png align="left")

Typing a custom formula has the advantage of being quick and straightforward, especially for simple calculations.

Additionally, formulas may be copied down and/or across cell ranges for quick reuse. And formulas are used in exactly the same fashion in Google Sheets as in Microsoft Excel.

However, when calculations become lengthy and/or complex, it can be helpful to know about some alternative methods.

## **How to Use a LAMBDA Function and Name Manger**

Building on our first example, the LAMBDA function allows us to take a custom operation and codify it for reuse throughout our worksheet.

Using the same data as before (this time in cells `B4` and `C4`) we write the LAMBDA Function like so:

```javascript
=LAMBDA(year1,year2,(year2-year1)/year1)(B4,C4)
```

![Screenshot of Excel Lambda function](https://www.freecodecamp.org/news/content/images/2022/12/image-63.png align="left")

At first glance you might wonder why on earth we should type out this lengthy mess, but hang with me and you'll see it is arguably cleaner for reuse than simply defining a function.

![Gif of woman scratching head and looking confused](https://www.freecodecamp.org/news/content/images/2022/12/confused.gif align="left")

Here's what's happening:

The first thing we're doing is defining the parameters of our function and separating them by commas. You can define as many of those as you need (well, up to 253 that is 🤣). We only have two: `year1` and `year2`.

After listing the parameters, we write the formula we want Excel to calculate. This is the same thing we did in the first Formula section – only this time we're using our parameter names instead of the explicit cell names: `(year1-year2)/year1`.

Last, we close the parenthesis of the LAMBDA function and then call it by writing the actual cells being used: `B4,C4`. This is telling the function that it needs to use the value in cell `B4` for the parameter `year1` and the value in cell `C4` for the parameter `year2`.

What a mess, right!? Yes, and technically, writing out the whole LAMBDA function here is simply good practice to make sure the thing works before we do the next step...

This is the cool part. Click the Formula tab in the Ribbon at the top and select Name Manager.

![Excel Ribbon accessing Name Manager in Formula Tab](https://www.freecodecamp.org/news/content/images/2022/12/name-manager.png align="left")

Select New.

![Screenshot of Name Manager in Excel](https://www.freecodecamp.org/news/content/images/2022/12/name-manager-new.png align="left")

Then enter the Name of your formula and write an optional description in the Comments. In the Refers to line, you'll copy in the LAMBDA Function.

![Screenshot of Named Function in Excel](https://www.freecodecamp.org/news/content/images/2022/12/name-manager2.png align="left")

You'll be able to use it in the same way you would use a built-in function by typing the following into a cell

```javascript
=Percentage_Change(B5,C5)
```

![Screenshot of Excel Formula](https://www.freecodecamp.org/news/content/images/2022/12/percentage-change-lambda.png align="left")

Now we have all the ease of a regular built-in function at our disposal. Google Sheets has similar functionality, which we'll discuss at the end of this article.

## **How to Use Visual Basic for Applications**

If you're using the desktop version of Excel, you have access to Visual Basic for Applications. This is an event-driven programming language by Microsoft and you can use it to do almost anything you can dream (and code) up.

If you wanted to find the percentage difference between two numbers using VBA, you would go to the Developer tab in the Ribbon (or press `alt + F11`).

![Screenshot of Developer Tab in Excel](https://www.freecodecamp.org/news/content/images/2022/12/vba1.png align="left")

If you don't see the Developer tab, you may need to enable it by selecting File -&gt; Options. Then look for Customize Ribbon. From here you can select the box next to Developer.

![Screenshot of Excel Options](https://www.freecodecamp.org/news/content/images/2022/12/vba3.png align="left")

Bonus: If `ALT + F11` doesn't work, GeForce Experience may be interfering with the built-in shortcuts. Change the shortcut for whatever is using `ALT + F11` in the settings. For me it was the Toggle comments on/off while broadcasting to Facebook setting.

![screenshot of GeForce Experience settings](https://www.freecodecamp.org/news/content/images/2022/12/vba2.png align="left")

Once you've opened the VBA window, select Insert -&gt; Module from the menu. This will open up a blank window where we will write our program. Think of this like an IDE inside Excel. We'll program here and then utilize that program in our worksheet.

![Screenshot of VBA menu](https://www.freecodecamp.org/news/content/images/2022/12/vba4.png align="left")

Here we can enter the same type of commands we used with the Named LAMBDA function above.

```javascript
Function PERCENTFUNCTION(year1, year2)
    PERCENTFUNCTION = (year2 - year1) / year1
End Function
```

And voilà! We can now use `PERCENTFUNCTION` in our Excel Sheet in the same way we used the `Percentage_Change` named function.

VBA is useful for more complicated programs and would be overkill for our example. Incidentally, Google Sheets does not have VBA functionality.

## **How to Use the Office JavaScript API**

Now the real good stuff! Did you know you can write JavaScript and TypeScript within Excel? Me either. But you can.

Script Lab is an Add-on by Microsoft that allows us to explore the JavaScript API within Office Apps as well as declare custom functions by writing them as scripts.

You can add it to Excel [here](https://learn.microsoft.com/en-us/office/dev/add-ins/overview/explore-with-script-lab). And read more about it [here](https://learn.microsoft.com/en-us/office/dev/add-ins/overview/explore-with-script-lab).

Unlike VBA, this is usable on the web version of Excel too.

Once it's installed, select it from the Ribbon and click Code.

![Screenshot of Script Lab in Excel Ribbon](https://www.freecodecamp.org/news/content/images/2022/12/script1.png align="left")

This will bring up a legit code editor on the sidebar.

![Screenshot of Script Labs Code Editor in Excel](https://www.freecodecamp.org/news/content/images/2022/12/image-66.png align="left")

We can create a custom function using JavaScript by selecting a New Snippet from the Hamburger menu at the top left of the Scripts Lab window.

![Screenshot of New Snippet menu ](https://www.freecodecamp.org/news/content/images/2022/12/image-67.png align="left")

By typing the following function we can again define a percent difference function, but this time using JavaScript.

```javascript
/** @CustomFunction */
function percent_change_javacscript(year1, year2) {
  return (year2 - year1) / year1;
}
```

In order to use this function, select Script Lab -&gt; Functions from the Ribbon:

![Screenshot of Script Lab Menu in Ribbon](https://www.freecodecamp.org/news/content/images/2022/12/script2.png align="left")

This will open another sidebar tab and because of the first line in the snippet: `/** @CustomFunction */` it will register that custom function.

In the worksheet, you'll be able to use it just like we've been using custom defined functions. This time, though, when you start typing the title, you'll see it registered with a scriptlab prefix on the name. Select this, and it will return the percent change just like the other methods.

![Screenshot of Script Lab Custom Function in Excel](https://www.freecodecamp.org/news/content/images/2022/12/script3.png align="left")

Once again, this is major overkill for a simple function, but quite handy to put in your toolbelt nonetheless! 👍

## **How to Use Custom Functions with Google Sheets**

As promised, here's a bonus for how to create a Named Function in Google Sheets. This is very similar to using the Name Manager in Excel.

Select Data -&gt; Named Functions in Google Sheets.

![Screenshot of Google Sheets Data Menu](https://www.freecodecamp.org/news/content/images/2022/12/sheets1.png align="left")

This will prompt you to name and describe your function as well as provide arguments, if applicable.

Last, you'll define the function's operation.

![Screenshot of naming a custom function in Google Sheets](https://www.freecodecamp.org/news/content/images/2022/12/sheets2.png align="left")

The next screen prompts you to add argument descriptions and examples if you'd like. This is optional, but will be included in the drop down help menu when you use the function in your sheet.

![Screenshot of custom function argument descriptions in Google Sheets](https://www.freecodecamp.org/news/content/images/2022/12/sheets4.png align="left")

Then it's as easy as typing in your custom function and selecting the cells. You can see below how the help menu is displayed with the information you provided.

![Screenshot of using a custom function in Google Sheets](https://www.freecodecamp.org/news/content/images/2022/12/sheets5.png align="left")

## **Conclusion**

Yes, often you will opt for simplicity's sake to use a quick formula in Excel or Google Sheets. But now you know several other ways to find the percentage change between two numbers.

I hope you've found this useful, and good luck in your own spread-sheeting adventures!

You can find and follow me on [LinkedIn](https://www.linkedin.com/in/eamonncottrell/). I'd love if you said hey. 👋

![Jimmy Fallon saying haaaaay and holding up some hay](https://www.freecodecamp.org/news/content/images/2022/12/hey.gif align="center")