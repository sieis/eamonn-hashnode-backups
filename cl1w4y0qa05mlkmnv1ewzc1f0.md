## Encouragement for freeCodeCamp's Relational Database Course

I've run into some hurdles along the way. Hopefully this can save you a bit of trouble.

## Save Often 💾

![ff7.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1649758987657/OeYshqSDQ.png)

Perhaps it's more obvious to me the importance of saving often and in multiple places because I grew up playing Final Fantasy 7 on the PS1 and was in a constant state of terror of my brothers accidentally (or purposely) overwriting one of my save files.

And it did happen. And there was much weeping and gnashing of teeth.

At any rate, I've been relearning the importance of saving my progress during the course of this certification. 

### tldr;

> Complete each project in one sitting if possible; save often if not.

## Forum 🙋‍♀️

First things first, the forum does have some good guidelines and troubleshooting for issues. However, the course is in beta as of the time of this writing, so there are issues cropping up daily. Always be sure to check out the forum first, and this [main thread](https://forum.freecodecamp.org/t/running-the-relational-database-curriculum-in-your-browser/500231) is a good starting point.

## Virtual Machine 📺


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1649709308226/hCJHgr3R1.png)

The browser based version of the certificate was released only recently, and it runs entirely in a virtual instance of VS Code using [CodeAlly](https://codeally.io/) to login and manage the challenges, and the [CodeRoad](https://marketplace.visualstudio.com/items?itemName=CodeRoad.coderoad) extension to execute the challenges within VS Code

This is cool, but not without some occasional glitches.

![glitch.gif](https://cdn.hashnode.com/res/hashnode/image/upload/v1649709533538/P1i_-AP_E.gif)

When I first started this certificate, it was only available to be run directly through VS Code. Also cool, but I ran into significant issues. In fact, after getting setup and loading the first coursework, it would not pass the tests at all on my Windows machine. After much laboring and resetting, all I ever managed was to get the very first (of like 100) test to pass.

> It doesn't work at all?!

I loaded it up on my Macbook Pro and did not have any issues. It was not worth going down the rabbit hole to figure out what the root of the issues on my computer was.

## Persevere 💪

So: persevere through issues! I'm becoming more convinced daily that this may be the motto of software development generally. We will always be confronted with issues--anticipated and unanticipated. Things will break--with and without good reason. The solutions will be non-obvious much of the time. 

**But take heart!**

When embraced, this can be a source of joy and discovery. 

- Solving the riddles of my own misguidance has often been my biggest source of accomplishment. 
- Sharing this with others gives permanence to the struggle/struggle/solution cadence. 
- And a positive attitude becomes more valuable than much knowledge. 

Inching toward the solution has been of greater value to my learning than simply powering through a multitude of lessons.

We're learning to walk here. It does no good to get into an airplane.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1649757510287/SW3YEOYVg.png)

## Leave It Open 📖

In both the [Mario Database](https://www.freecodecamp.org/learn/relational-database/learn-relational-databases-by-building-a-mario-database/build-a-mario-database) and the [Celestial Bodies](https://www.freecodecamp.org/learn/relational-database/build-a-celestial-bodies-database-project/build-a-celestial-bodies-database) projects, I hit issues when I closed the Virtual Machine to come back later and finish the project.

In the case of Mario, I got 70% through and had to start over. [Here's my own forum post](https://forum.freecodecamp.org/t/rdbm-course-stuck-at-mario-dbs-last-challenge/503211/4?u=sieis) regarding the issue I ran into. 

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1649757809647/IbQYa2TNX.png)

Unfortunately, I was a casualty of the beta version of the course, and had to start all over. 

Fortunately, I did start over. And I flew through the parts I'd already done. Honestly, it just solidified the material that much more. I was also writing [an article to reference later](https://blog.eamonncottrell.com/a-list-of-postgresql-commands-for-beginners) with all the commands I was learning. Between those things, I think the intro to PostgreSQL stuck even more for me.

**That said, avoid closing the virtual machine before completing a project if at all possible!** 

Having to start over can be very demoralizing, and is often an excuse to throw in the towel. Don't quit! Even if you lose a bunch of progress like I did. 

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1649759687630/On1anQ8zw.png)

In the case of Mario, it is very doable in one sitting. **It may take 1-2+ hours**, but if you can, knock it out. 

In the case of Celestial Bodies, I did have to delete the container, reload the project, and load my saved data (more on these details below because you really don't want to start this one over imo).

And it was a big longer than Mario. I estimate it took me **roughly 2.5+ hours to complete** the Celestial Bodies project. *Not counting the extra work troubleshooting the issues I hit.*

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1649758265946/5DUsYZyr6.png)

## Celestial Bodies Project 🌌

When you load into this one, instructions for saving a dump of your project into an `.SQL` file are given at the top. 

**Save that file by following those instructions if you have to leave the project before completing it.**

Furthermore, once you save it to your virtual machine workspace, right click and save a copy to your desktop.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1649764915010/CXwSqJJBP.png)

I was perhaps overly cautious, but I really didn't want to retype everything. 

Sure enough, I had to use that file to reload the whole thing. 

I encountered another error where I could not log into `-username=freecodecamp -dbname=postgres` and had to delete everything, load it back up, and upload the saved `.SQL` file from my desktop.

Finally, I encountered an issue where upon clicking to start the project, I was presented with a blank white screen instead of the Run with CodeAlly prompt. 

![startcourse.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1649765070264/edrEhWbpT.png)

This happened in Chrome, and when I loaded in Firefox, it worked correctly. 

I also cleared my cache and browsing history in Chrome and it worked after that. I completed the project in Chrome. I'm not sure what the issue actually was because it didn't immediately work after the cache/browsing clear.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1649765059662/THizUd3OK.png)

So, more than anything, I encourage you to:

1. complete what you can in one sitting without closing the virtual machine mid-project
1. save your progress where possible
1. persevere!

## Thanks for Reading 🙏

I hope this is helpful for you. I'll keep updating as I complete more of the coursework. I've only scratched the surface; there are 11 more projects to go!

Leave me a comment below or find me over on [Twitter](https://twitter.com/EamonnCottrell). I'd love to say hi 👋.

Have a great one❗




