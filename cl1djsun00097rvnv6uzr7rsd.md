## Re-Syndicate Hashnode to DEV the Easy Way

## GitHub Actions = Still Cool, But...

Last week I wrote up an [article](https://blog.eamonncottrell.com/re-publishing-hashnode-articles-to-dev-with-github-actions) about auto-posting from Hashnode to DEV by using GitHub Actions. 

This was a great way to learn how to set up an Action, fiddle with the [DEV API](https://developers.forem.com/api) and spend a great deal of time figuring out something that I could have done faster by literally copying and pasting the articles' markdown.

I don't regret it because it was a good learning experience. But I do want you to know the better way.

## Use RSS

Just use the RSS feed of your Hashnode blog. You can just add rss.xml to your blog's main page like this to find it:
 (`https://blog.eamonncottrell.com/rss.xml`)

DEV will let you import an RSS feed to re-syndicate. Go to Settings -> Extensions and then scroll down to the Publishing to DEV Community from RSS section.

![re-syndicate on DEV via RSS](https://cdn.hashnode.com/res/hashnode/image/upload/v1648576612774/_6h_fVDDL.png)

Notice that there are two optional checkboxes. One for canonical tags which I checked because I'm keeping Hashnode as my main canonical_url for my blog. And the other for "self-referential links". This is for when I link to something else I wrote, [like this article about Sacred Geometry](https://blog.eamonncottrell.com/sacred-geometry-with-adobe-illustrator). The link will take me to the DEV article when on DEV instead of to Hashnode. 

I don't want that to happen because I want **Hashnode to be my main**, so I unchecked that box.

![main character](https://cdn.hashnode.com/res/hashnode/image/upload/v1648643368065/37Zt8cy5o.png)
> hashnode is my main

## Thanks, Andy!

During the course of last week's investigative journalism and guinea-pig-like commitment to the cause of setting up my own blog to auto-backup to GitHub ([still a good idea](https://blog.eamonncottrell.com/hashnode-auto-backup-posts-on-github)) and auto-post to DEV, I hit DEV's API rate limit.

A reply from support suggested (graciously, yet simply) that I try importing via RSS if I was going to do more than one import at a time.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1648574260177/q19EjCjwZ.png)

This is by far the better way to accomplish the re-posting. Yay!

%[https://media.giphy.com/media/8WOCI38ldkriE/giphy.gif]

## Publish on DEV

And, just like that: we have success!

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1648573976466/AecY8Ajm_.png)

DEV will pull all the articles over as Drafts immediately. It even properly saw the three I'd already brought over and did not duplicate them. And this has the added bonus of properly including the original published date in the front matter which my previous method did not unless you added that manually.

In order to publish on DEV, you'll need to change the value of published to true in the front matter of the post. Of note: the DEV publication date will not be the original publication date.

![publish.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1648574189917/dOtj98W23.png)

## Found Issues

### Embeds

Hashnode and DEV have different syntax for embedding things like YouTube videos and GIFs in the posts, so you'll want to take note of that and address accordingly.

[Here's Hashnode's Markdown Guide.](https://support.hashnode.com/docs/markdown-guidelines)

[Here's DEV's Editing Guide.](https://dev.to/p/editor_guide)

### Code Blocks

Also, I noticed a weird quirk in code blocks imported via RSS. In Hashnode (on the left below), I've declared the language of the code block, but in the DEV RSS import (on the right), that's missing. In order for the code blocks to be pretty and color-coded the way we like them, that has to be manually added to each block.

![javascript.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1648576997819/UcBO0_sm_.png)

### Cover Images

The cover image doesn't come over either. For some reason, you can't simply upload it to DEV. **If there's a way to do this, please let me know**. Instead, you'll need to add a `cover_img:` value pointing to your image in the front matter.

You can open the cover image in a new tab from Hashnode to grab the url and plug it in.

**Img in new tab:**
![open img in new tab](https://cdn.hashnode.com/res/hashnode/image/upload/v1648577957857/8yiZIXj8T.png)

**copy url:**
![copy img address](https://cdn.hashnode.com/res/hashnode/image/upload/v1648578061600/EIdenNqi8.png)

**add to DEV front matter:**
![put img address in front matter](https://cdn.hashnode.com/res/hashnode/image/upload/v1648578413649/j4iGraLTv.png)

> (No, the upload image section in the screenshot above is not for the cover image. That's just DEV's regular place where you can upload an image for the markdown text and it'll give you the markdown to paste.)

## Thanks & Please Share!

Do you cross-post content? How do you reduce the amount of repeat copy/paste type work? Did you find this helpful? Please let me know below in the comments, and re-share on Twitter or your preferred platform!

I'm growing my developer content portfolio, and am grateful for any additional exposure! 😀

You can find me on [Twitter](https://twitter.com/EamonnCottrell); I'd love to say hey!

Have a great one!

%[https://media.giphy.com/media/KJ1f5iTl4Oo7u/giphy.gif]