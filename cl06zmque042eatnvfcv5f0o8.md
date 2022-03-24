---
title: Version Releases and Git Tags for Beginners
published: true
cover_image: 'https://blog.eamonncottrell.com/_next/image?url=https%3A%2F%2Fcdn.hashnode.com%2Fres%2Fhashnode%2Fimage%2Fupload%2Fv1646070011808%2Fz8jGZy9Uh.jpg%3Fw%3D1600%26h%3D840%26fit%3Dcrop%26crop%3Dentropy%26auto%3Dcompress%2Cformat%26format%3Dwebp&w=1920&q=75'
tags: 'github,git,versioning,beginnerdevelopers,developertools'
canonical_url: https://blog.eamonncottrell.com/version-releases-and-git-tags-for-beginners
---
## Version Releases and Git Tags for Beginners

I didn't know this was a thing.

Well, I take that back. I knew *about* versioning and releases, i.e., 1.0.2. But until I tried to slap a version on my own web app on Github, I didn't realize there was a little bit of work necessary to set things up correctly.

## Semantic Versioning, What?

Semantic Versioning is something you're probably already familiar with if you've done so much as download an update to one of your iPhone apps. See those three numbers in the picture below? The represent **major**, **minor **and **patch **releases of a piece of software.

Without getting into the weeds too much (you can [read this](https://semver.org/) if you want to go deep):

1. the major number represents changes that break stuff in past big versions.
2. the minor number represents changes that doesn't break stuff in past versions.
3. the patch number represents bug fixes

![version.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1646067289343/7rgZ7L1vT.jpg)

Pretty easy to follow, right?

## Practical Use

I recently released a web application called [Infinite Memory](https://infinite-memory.netlify.app/). I wrote about it [here](https://blog.eamonncottrell.com/infinite-memory). I decided to go ahead and slap on a version when I glanced in the sidebar on [Github](https://github.com/sieis/infinite-memory):


![release.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1646067928189/0FGJM4gIy.png)

Easy enough, eh? Well, almost. When I entered some basic details for a v1.0.0-beta, it let me know that I needed a valid tag. What's this, you ask? Well, I didn't know either. 

![notag.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1646068115096/ua5-GXdaY.png)

## Git Tags

Turns out, in addition to commits, you can create tags with Git. These denote places in the code history where big things happened. Big things like...a version release! Makes total sense. 

[Here's an article](https://git-scm.com/book/en/v2/Git-Basics-Tagging) on Git Tagging Basics. It seemed as straightforward as committing changes, so, I jumped back into VS Code to tag away. I wanted to tag the commit I made today, so I first grabbed my commit history: ```git log --pretty=oneline```. Then I tagged it with: ```git tag -a v1.0.0-beta 63380025```. I entered the first few digits from the checksum from my log to put the tag on the proper place.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1646068776063/aakfy2jGt.png)

Now it's tagged correctly, but sharing tags works differently than pushing changes in the codebase. If you run ```git status``` everything appears up to date.

Instead, I run 
```bash
git push origin v1.0.0-beta
```

and, voila! Everything looks good from the terminal:

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1646068910067/ic33-CKSG.png)

And sure enough, all is well on Github. I can now select my v1.0.0-beta tag to create my release!  I also opted to select the ```pre-release``` box which marks it as a non-production piece of software. 

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1646068968947/EicGV_S54.png)

I hope this was a helpful walkthrough for you! I enjoyed learning a little something new today, and I hope it was an enjoyable walkthrough for you as well! 

Check out the actual release I worked on [here](https://github.com/sieis/infinite-memory/releases/tag/v1.0.0-beta)!

## Contact

I'd love if you said hi! Drop a comment below, or connect with me over on [Twitter](https://twitter.com/EamonnCottrell) and/or [LinkedIn](https://www.linkedin.com/in/eamonncottrell/).