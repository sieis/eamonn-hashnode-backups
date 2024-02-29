---
title: 6 Ways to number in Excel
seoDescription: Easy ways to increase your productivity in Excel by automating ways to number and sequence things.
datePublished: 'Thu Feb 29 2024 13:26:25 GMT+0000 (Coordinated Universal Time)'
cuid: clt79ee75000b0al26kca1ur0
slug: 6-ways-to-number-in-excel
canonical: 'https://got-sheet.beehiiv.com/p/numbering-in-excel'
cover: 'https://cdn.hashnode.com/res/hashnode/image/upload/v1709212836313/fa92b70b-ba90-48e6-b828-0dae5bc6c964.jpeg'
tags: 'productivity, excel, spreadsheets'
id: 1776163
---

Since last we spoke I’ve been recording several new long and short form videos. Check out the [YouTube Channel](https://flight.beehiiv.net/v2/clicks/eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1cmwiOiJodHRwczovL3d3dy55b3V0dWJlLmNvbS9AZWFtb25uY290dHJlbGw_dXRtX3NvdXJjZT1nb3Qtc2hlZXQuYmVlaGlpdi5jb20mdXRtX21lZGl1bT1yZWZlcnJhbCZ1dG1fY2FtcGFpZ249Ni13YXlzLXRvLW51bWJlci1pbi1leGNlbCIsInBvc3RfaWQiOiJlNDVmNmUzMS1lZGIyLTRkNjYtYTYxMi04YTY0MjJiMWM0YTMiLCJwdWJsaWNhdGlvbl9pZCI6IjA2MWZiMmRhLWIxYTItNGU4My04MWI4LTdkNjc2NzhjNTM2NiIsInZpc2l0X3Rva2VuIjoiY2MxZDUwZGUtMjNlMy00NmQxLTliMTMtODQ1OGRmOGU2YmNjIiwiaWF0IjoxNzA5MjEyNzk0LCJpc3MiOiJvcmNoaWQifQ.ghV8a1dCtLY00Hqdq72Pwz3NVFjjyH5rirVfvyjacLs) if you haven’t.

I’ve also wrapped up training for a marathon I’ll be racing on March 3rd… 🤞🤞

Now to the sheets…

Do you ever feel lost in Excel? Like you should know a lot but struggle to grasp the basics?

Fear not. Today's tips are all about some fundamentals that will be useful and speed up your spreadsheet work.

Here's the brief video walkthrough if you're a visual learner:

%[https://youtu.be/awNe9MEO8no] 

## **6 Ways to Number Things**

1. **Manual** - You’re familiar with this, though you hang your head in shame at how often you use it. This is when you manually type everything in. Don’t worry, we all start here.
    
2. **Drag** \- Level 1. At the bottom right corner of an active cell or range you can click and drag down. Excel is pretty smart. It will expand the sequence of numbers (or dates, or days) and fill in the missing values.
    
3. **Double Click** - Now we’re getting up to speed. By double clicking that bottom right corner, Excel will fill down just like when you dragged down. Where it stops will depend on other values in your workbook. If you don’t have other values, or a table you’re working in, this may not work.
    
    ![](https://media.beehiiv.com/cdn-cgi/image/fit=scale-down,format=auto,onerror=redirect,quality=80/uploads/asset/file/d425da4c-2c51-4ce4-aa0d-c06a7a1157e3/arrow.png?t=1709064606 align="left")
    
4. **Formula** - The power of spreadsheets lies behind the scenes in all the gritty, delicious minutia. It’s here where the wild things live. It’s here where we can write custom formulas to do darn near anything. And I do mean anything - someone [built a 16-bit CPU inside an Excel workbook](https://flight.beehiiv.net/v2/clicks/eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1cmwiOiJodHRwczovL3d3dy55b3V0dWJlLmNvbS93YXRjaD92PTVyZzd4dlRKOFNVJnV0bV9zb3VyY2U9Z290LXNoZWV0LmJlZWhpaXYuY29tJnV0bV9tZWRpdW09cmVmZXJyYWwmdXRtX2NhbXBhaWduPTYtd2F5cy10by1udW1iZXItaW4tZXhjZWwiLCJwb3N0X2lkIjoiZTQ1ZjZlMzEtZWRiMi00ZDY2LWE2MTItOGE2NDIyYjFjNGEzIiwicHVibGljYXRpb25faWQiOiIwNjFmYjJkYS1iMWEyLTRlODMtODFiOC03ZDY3Njc4YzUzNjYiLCJ2aXNpdF90b2tlbiI6ImNjMWQ1MGRlLTIzZTMtNDZkMS05YjEzLTg0NThkZjhlNmJjYyIsImlhdCI6MTcwOTIxMjc5NCwiaXNzIjoib3JjaGlkIn0.op98vj7D4eJv3ZvdHuSWg8qDozHl2KMTJMmeFZiY9Mc) recently.  
    For our purposes, we can simply reference the first cell and add something to it. Then if we drag that formula down just like in option 3, we can quickly expand the sequence of dates.
    
    ![](https://media.beehiiv.com/cdn-cgi/image/fit=scale-down,format=auto,onerror=redirect,quality=80/uploads/asset/file/735d8a54-2da4-43ab-9545-b1eabd8fe711/image.png?t=1709064401 align="left")
    
5. **Sequence** \- This is an incredibly handy built-in function. It’s like a custom formula, only it’s already baked in to Excel. It allows you to generate sequences of values over a specified number of rows and/or columns. You let Excel know how many of each to use, what value to start with and then what value to increment by. \*Bonus: to count down, you can use a negative value in the final “step” variable.
    
    ![](https://media.beehiiv.com/cdn-cgi/image/fit=scale-down,format=auto,onerror=redirect,quality=80/uploads/asset/file/8697f0a0-2af9-447f-9a7f-e326307a65a5/image.png?t=1709064268 align="left")
    
6. **Row** \- Another nifty function, and lesser known. Row isn’t explicitly for numbering or sequencing things, but we can use it for this. Row will return whatever the numerical value of the current row is. We can use this as is, but if we worry about rows being deleted, we can also explicitly reference a cell using ROW(A1) or something similar. From here we can sequence subsequent rows using one of the above methods if need be.
    

![](https://media.beehiiv.com/cdn-cgi/image/fit=scale-down,format=auto,onerror=redirect,quality=80/uploads/asset/file/5bb74059-16f2-4b80-be25-88fc81b28ef4/image.png?t=1709064710 align="left")

**<mark>What's your favorite method?</mark>**

## **Thank you so much!**

It means a lot that you’ve read this, and I hope it’s informed and/or entertained you for a few moments today!

Would love to say hi. Here are the best places to find me:

* 📺️ Videos on [YouTube](https://flight.beehiiv.net/v2/clicks/eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1cmwiOiJodHRwczovL3d3dy55b3V0dWJlLmNvbS9AZWFtb25uY290dHJlbGw_dXRtX3NvdXJjZT1nb3Qtc2hlZXQuYmVlaGlpdi5jb20mdXRtX21lZGl1bT1yZWZlcnJhbCZ1dG1fY2FtcGFpZ249Ni13YXlzLXRvLW51bWJlci1pbi1leGNlbCIsInBvc3RfaWQiOiJlNDVmNmUzMS1lZGIyLTRkNjYtYTYxMi04YTY0MjJiMWM0YTMiLCJwdWJsaWNhdGlvbl9pZCI6IjA2MWZiMmRhLWIxYTItNGU4My04MWI4LTdkNjc2NzhjNTM2NiIsInZpc2l0X3Rva2VuIjoiY2MxZDUwZGUtMjNlMy00NmQxLTliMTMtODQ1OGRmOGU2YmNjIiwiaWF0IjoxNzA5MjEyNzk0LCJpc3MiOiJvcmNoaWQifQ.ghV8a1dCtLY00Hqdq72Pwz3NVFjjyH5rirVfvyjacLs)
    
* 💾 Products on [Gumroad](https://flight.beehiiv.net/v2/clicks/eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1cmwiOiJodHRwczovL2VhbW9ubi5ndW1yb2FkLmNvbS8_dXRtX3NvdXJjZT1nb3Qtc2hlZXQuYmVlaGlpdi5jb20mdXRtX21lZGl1bT1yZWZlcnJhbCZ1dG1fY2FtcGFpZ249Ni13YXlzLXRvLW51bWJlci1pbi1leGNlbCIsInBvc3RfaWQiOiJlNDVmNmUzMS1lZGIyLTRkNjYtYTYxMi04YTY0MjJiMWM0YTMiLCJwdWJsaWNhdGlvbl9pZCI6IjA2MWZiMmRhLWIxYTItNGU4My04MWI4LTdkNjc2NzhjNTM2NiIsInZpc2l0X3Rva2VuIjoiY2MxZDUwZGUtMjNlMy00NmQxLTliMTMtODQ1OGRmOGU2YmNjIiwiaWF0IjoxNzA5MjEyNzk0LCJpc3MiOiJvcmNoaWQifQ.D3D-ngTkLNlO5krX5XLZ_rhbccSA3VXZWN3ly9M5Wfg)
    
* ✉️ Connections on [LinkedIn](https://flight.beehiiv.net/v2/clicks/eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1cmwiOiJodHRwczovL3d3dy5saW5rZWRpbi5jb20vaW4vZWFtb25uY290dHJlbGwvP3V0bV9zb3VyY2U9Z290LXNoZWV0LmJlZWhpaXYuY29tJnV0bV9tZWRpdW09cmVmZXJyYWwmdXRtX2NhbXBhaWduPTYtd2F5cy10by1udW1iZXItaW4tZXhjZWwiLCJwb3N0X2lkIjoiZTQ1ZjZlMzEtZWRiMi00ZDY2LWE2MTItOGE2NDIyYjFjNGEzIiwicHVibGljYXRpb25faWQiOiIwNjFmYjJkYS1iMWEyLTRlODMtODFiOC03ZDY3Njc4YzUzNjYiLCJ2aXNpdF90b2tlbiI6ImNjMWQ1MGRlLTIzZTMtNDZkMS05YjEzLTg0NThkZjhlNmJjYyIsImlhdCI6MTcwOTIxMjc5NCwiaXNzIjoib3JjaGlkIn0.SA3RqUwdSxcGen6dlMwIzG86CMt0JWHbfeNdw8e9e4A)
    

It's been a while since I've posted one of my articles on Hashnode. Never fear - I'll be repurposing some of my content from the past year or so to keep you in the loop!
