## Responsive YouTube <iframe> Embedding with Bootstrap

## Copy & Paste Doesn't Always Work ☹️

It comes close, but if you copy and paste the embed code off of a YouTube video, you can still run into issues. Particularly on mobile. I found this out just this morning when adding a tutorial video to a [simple web app](https://infinite-memory.netlify.app/) I made using [Bootstrap 5](https://getbootstrap.com/).

![YouTube Embed Code Screenshot](https://cdn.hashnode.com/res/hashnode/image/upload/v1647524338006/C66_RyqE0.png)

This worked fine, and previewed well on localhost:5500. But, it was screwy on mobile when I previewed the live site on my iPhone 11. The fixed width was extending off the screen to the right. If you're like me, anytime I encounter stuff like this, it causes me an infinite amount of strife.

Luckily, there's a pretty easy fix that Bootstrap documents. [Bootstrap 4 handles it this way](https://getbootstrap.com/docs/4.0/utilities/embed/). [Bootstrap 5 handles it this way](https://getbootstrap.com/docs/5.0/helpers/ratio/#example).

## The Code 💾

Both have you wrapping a parent ```html <div>``` with either ```.embed-responsive``` or ```.ratio``` (depending on the Bootstrap version) and then having the iframe within that element. 

### Bootstrap 5

My div looks like this:

```html
<div class="tutorial container text-center my-5 ratio ratio-16x9">
</div>
```

And I stripped all the fluff out of the YouTube copy/paste embed code so that I was left with this for the iframe:

```html
<iframe src="https://www.youtube.com/embed/qgInM6FH8Lk?rel=0"
    allowfullscreen>
</iframe>
```

### Bootstrap 4 

There are different semantics with Bootstrap 4 which accomplish the same thing:

div:

```html
<div class="tutorial container text-center my-5
    embed-responsive embed-responsive-16by9">
</div>
```

iframe:

```html
<iframe class="embed-responsive-item"
    src="https://www.youtube.com/embed/qgInM6FH8Lk?rel=0" 
    allowfullscreen>
</iframe>
```

Interestingly, I accidentally used the Bootstrap 4 solution initially and it worked on mobile while not fully expanding on larger screens. 

## Embedding on Hashnode 🖥️

Bonus! Here's the video in question. And it's super easy to embed right here on Hashnode. All that's required is a handy percent sign 😀. [Here are the embed docs.](https://support.hashnode.com/docs/embeds)

```%[https://www.youtube.com/watch?v=qgInM6FH8Lk]``` 👇

%[https://www.youtube.com/watch?v=qgInM6FH8Lk]

And in writing this article, I realized that @Hashnode has made it even easier to find snazzy shortcuts without jumping all the way to the docs if you choose. There's a Guide link at the top of the article next to the Preview link.

This is a great, quick resource for markdown, embeds, and other commonly used tools for blogging here. 👇

![Hashnode Guide Link](https://cdn.hashnode.com/res/hashnode/image/upload/v1647525964912/9hAcA51Oc.png)

## Say Hey! 👋

Hope this is helpful for you, and you have a great day!

Come say hey to me over on [Twitter](https://twitter.com/EamonnCottrell) and/or [LinkedIn](https://www.linkedin.com/in/eamonncottrell/). 

