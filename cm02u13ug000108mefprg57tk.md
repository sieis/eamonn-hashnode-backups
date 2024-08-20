---
title: "How to Make a Lightbox in a Google Sheet"
datePublished: Tue Aug 20 2024 19:43:02 GMT+0000 (Coordinated Universal Time)
cuid: cm02u13ug000108mefprg57tk
slug: how-to-make-a-lightbox-in-a-google-sheet
canonical: https://www.gotsheet.xyz/p/image-lightbox-in-google-sheets
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1724183054064/cb013ab5-a1b7-4514-9101-ff9dbafca11d.jpeg
tags: google-sheets, excel, spreadsheets, html-image

---

*this originally appeared on my* [*free weekly newsletter, Got Sheet*](https://www.gotsheet.xyz/c/hashnode)*.*

In this article and accompanying video, I'll show you two ways to create a lightbox effect in a spreadsheet. The first will trigger the image to be displayed in a large area **in the sheet**. The second will be an actual HTML popup **on top of the sheet**.

## **What is an Image Lightbox?**

![](https://media.beehiiv.com/cdn-cgi/image/fit=scale-down,format=auto,onerror=redirect,quality=80/uploads/asset/file/17705226-298d-4813-9700-21405d5d53cf/image.png?t=1715779845 align="left")

An image lightbox is what we call it when we hover over or click on an image and it pops up into a bigger version on-screen.

It’s something we’re used to seeing on websites, and it gives things a nice, professional touch when done well.

What about in a spreadsheet, though?

Well, we’ve got two versions of a solution.

1. Using built-in functions to display a larger version in a larger cell.
    
2. Using Apps Script to create a popup box on top of our spreadsheet.
    

As a bonus to the first solution, we’ll also include an optional Apps Script to make things a little smoother…more on that below 😉.

Here’s the full walkthrough on [YouTube](https://youtu.be/J39nMbuycEk)😀 

%[https://youtu.be/J39nMbuycEk] 

Here’s our [**demo sheet**](https://docs.google.com/spreadsheets/d/1Uz9sZJW1ts_YZc2-Ifd-UAQ8Pkgn23XLzmNdE_sDYrg/copy?gid=735811117&utm_source=www.gotsheet.xyz&utm_medium=referral&utm_campaign=image-lightbox-in-google-sheets#gid=735811117) if you want to follow along.

## **Image Popup With Built-In Functions**

First, we need images in cells. From the top menu, `Insert - Image - Insert image in cell` will do the trick.

![](https://media.beehiiv.com/cdn-cgi/image/fit=scale-down,format=auto,onerror=redirect,quality=80/uploads/asset/file/2750a472-e8dc-4668-a37f-a1a48eac0bc7/image.png?t=1715779915 align="left")

Next, we need to merge some cells together so that there’s a larger container that will hold our larger picture after the next step.

You could use one cell and change its the width and height, but in my example sheet, the “lightbox” area is sharing rows with the rest of the data, so I didn’t want to do that.

![](https://media.beehiiv.com/cdn-cgi/image/fit=scale-down,format=auto,onerror=redirect,quality=80/uploads/asset/file/351e6219-44d3-4d2f-bd23-94419d254092/image.png?t=1715779977 align="left")

In the column next to my image thumbnails, I’ve put checkboxes by selecting `Data - Data validation - Criteria: Checkboxes` from the top menu.

This will let us select which image to display in our lightbox area.

![](https://media.beehiiv.com/cdn-cgi/image/fit=scale-down,format=auto,onerror=redirect,quality=80/uploads/asset/file/d5ca1a3c-7574-4622-99a5-083eb86cc46e/image.png?t=1715780097 align="left")

I’ve named the range `A2:A11` as `pics` and the range `B2:B11` as `checkboxes` to allow for easier readability in the function we’ll write next…

![](https://media.beehiiv.com/cdn-cgi/image/fit=scale-down,format=auto,onerror=redirect,quality=80/uploads/asset/file/46ba5cda-7752-4d00-8788-da33d8623176/image.png?t=1715781954 align="left")

*named ranges in google sheets*

Now all that remains is one `XLOOKUP()` function to put inside our lightbox.

`=XLOOKUP(TRUE,checkboxes,pics,"")` is the function that searches for a check and then displays the corresponding image. By putting this in a big cell or range of merged cells, we can display whichever small image we select in the bigger area.

![](https://media.beehiiv.com/cdn-cgi/image/fit=scale-down,format=auto,onerror=redirect,quality=80/uploads/asset/file/3143e8a6-7db2-4dcd-8f42-70742d0926c8/image.png?t=1715780186 align="left")

*xlookup function in google sheets*

Remember, all a checkbox is doing is storing either a `TRUE` (checked) or a `FALSE` (unchecked) value.

![](https://media.beehiiv.com/cdn-cgi/image/fit=scale-down,format=auto,onerror=redirect,quality=80/uploads/asset/file/f2d21278-2b3b-40b6-9d26-0b03ff0ac762/image.png?t=1715780326 align="left")

*checkboxes and image thumbnails in google sheets*

**⚠️WARNING⚠️**

This does have one issue, though. Do you know what it is?

`XLOOKUP()` is going to return whichever checkboxes it comes to first with a TRUE value. So if you have multiple images checked, it’s only going to display the *first one it gets to*, not the most *recently clicked* one.

To get around this, let’s write some code.

## **Apps Script Improvement**

Open up Apps Script by selecting `Extensions - Apps Script` from the top menu.

![](https://media.beehiiv.com/cdn-cgi/image/fit=scale-down,format=auto,onerror=redirect,quality=80/uploads/asset/file/e310d543-85aa-458f-a55e-ca4ebb80c413/image.png?t=1715783060 align="left")

*opening apps script in google sheets*

Delete the built-in function in the code editor that opens. We'll start from scratch with an onEdit function:

```javascript
function onEdit(e) {
```

We need to grab the range that we are currently editing.

```javascript
var range = e.range
```

Then, get the checkboxes range.

```javascript
var checkboxes = SpreadsheetApp.getActive().getRangeByName("checkboxes")
```

Then, we need to check whether what we just edited is in that checkbox range.

```javascript
if (range.getColumn() == 2 && range.getRow() >= 2 && range.getRow() <= 10) {
```

If it was a checkbox, then we want to uncheck all the checkboxes and re-check the one we just checked.

```javascript
// Uncheck all other checkboxes in the range
checkboxes.uncheck();
// Check the edited cell
range.check();
```

Now, there is a slight delay when you run the code. After clicking a checkbox, all of them are cleared right before the one you checked gets checked again.

Here’s what the full code looks like:

```javascript
function onEdit(e) {
  var range = e.range;
  var checkboxes = SpreadsheetApp.getActive().getRangeByName("checkboxes")

  // Check if the edited cell is a checkbox in the desired range
  if (range.getColumn() == 2 && range.getRow() >= 2 && range.getRow() <= 10) {
    // Uncheck all other checkboxes in the range
    checkboxes.uncheck();
    // Check the edited cell
    range.check();
  }
}
```

## **A Real Pop-Up Box with HTML**

![](https://media.beehiiv.com/cdn-cgi/image/fit=scale-down,format=auto,onerror=redirect,quality=80/uploads/asset/file/ba9eb102-9c45-462f-b9e6-11bfe9e088e8/image.png?t=1715780986 align="left")

*modal dialog box in google sheets*

Okay, that’s all fine and dandy. What about the real thing, though?

This takes all Apps Script, but it’s doable thanks to the built-in method `showModalDialog`.

This is basically a pop-up window that can hold HTML. And since the internet is built with HTML, all that we need to do is use a little bit to plug in an image.

📌 This method does require an image to live on the internet somewhere. So, we cannot reference the image that we've embedded in our sheet and use it in the HTML we're going to write.

Weird, I know...

Let’s find an image URL we can use. I’ve grabbed an eagle off of [**unsplash**](https://unsplash.com/?utm_source=www.gotsheet.xyz&utm_medium=referral&utm_campaign=image-lightbox-in-google-sheets).

We’ll hold this in a variable.

```javascript
var imageURL = "https://images.unsplash.com/photo-1715002383611-63488b956401?q=80&w=1887&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D"
```

Then we need to build our HTML. In our case all we want is one element, so we won’t worry yourself with constructing a full, semantically correct page (although we certainly could 😉)

Another variable will hold this `img` element:

```javascript
var html = '<img src="' + imageURL + '" style="max-width: 100%; max-height: 100%;">';
```

We have access to Class Ui in Apps Script where we can “…add features like menus, dialogs, and sidebars.”

```javascript
  var ui = SpreadsheetApp.getUi();
```

And finally, by calling the showModalDialog() method, we can generate HTML from our `html` variable using the Class HtmlService.

```javascript
ui.showModalDialog(HtmlService.createHtmlOutput(html).setWidth(700).setHeight(1000), 'Eagle 🦅');
```

## **Make the Image a Button**

A final touch is to go add a thumbnail version of our eagle image into our spreadsheet so that it is inserted on top of our cells (this next bit won’t work if it’s embedded in a cell itself).

Once it’s in our sheet, we can click the three black dots in the top right corner and assign a script directly to the image.

![](https://media.beehiiv.com/cdn-cgi/image/fit=scale-down,format=auto,onerror=redirect,quality=80/uploads/asset/file/697595e4-c5bd-4cfb-909d-398326f1c513/image.png?t=1715781440 align="left")

*assigning a script to image in google sheets*

We named our script `displayImagePopup`, so this is what we enter. Make sure to leave off the parentheses when typing it into the image's script form.

![](https://media.beehiiv.com/cdn-cgi/image/fit=scale-down,format=auto,onerror=redirect,quality=80/uploads/asset/file/80446bd0-c9c2-43bd-a60b-35c7a860049f/image.png?t=1715782276 align="left")

*assigning script*

Now, anytime we click the small image of the eagle, a pop up box opens with the full image.

Here’s what the full code looks like:

```javascript
function displayImagePopup() {
  // Get the active sheet
  var sheet = SpreadsheetApp.getActiveSheet();
  var imageURL = "https://images.unsplash.com/photo-1715002383611-63488b956401?q=80&w=1887&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D"
  // Create an HTML string for the popup
  var html = '<img src="' + imageURL + '" style="max-width: 100%; max-height: 100%;">';
  
  // Show the dialog
  var ui = SpreadsheetApp.getUi();
  ui.showModalDialog(HtmlService.createHtmlOutput(html).setWidth(700).setHeight(1000), 'Eagle 🦅');
}
```

## Thanks!

Thanks for reading; let me know what you think.

Connect on [Linkedin](https://www.linkedin.com/in/eamonncottrell/)  
Videos on [YouTube](https://www.youtube.com/@eamonncottrell)