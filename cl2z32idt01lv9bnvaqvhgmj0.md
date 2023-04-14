---
title: "How To Quickly Create a Lightbox Photo Gallery in Your Bootstrap 5 Site"
datePublished: Mon May 09 2022 18:54:42 GMT+0000 (Coordinated Universal Time)
cuid: cl2z32idt01lv9bnvaqvhgmj0
slug: how-to-quickly-create-a-lightbox-photo-gallery-in-your-bootstrap-5-site
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1652122146187/v12I-ll-e.jpg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1652122189524/HghJ1VkAm.jpg
tags: tutorial, bootstrap, design, javascript-library

---

## 2023 Update: Video Walkthrough

%[https://youtu.be/P_DaJpTeQ84] 

## Solution

Let's lead with the goods: **bs5-lightbox**. This little javascript library solved my problem quickly, efficiently, and with little effort.

Here's the [GitHub page](https://github.com/trvswgnr/bs5-lightbox) if you want to cut to the chase and install.

Keep reading to find out more about using it in a Bootstrap 5 project 👇

## Project 🏢

I'm building a portfolio site for an independent game developer who needs a marketing page to showcase the game, and I like grabbing [Bootstrap 5](https://getbootstrap.com/) to get things running quickly.

I, like you, am pretty bored with the sameness of many of the Bootstrap sites out there. So, in addition to adding some custom CSS, we wanted to add a lightbox photo gallery component.

> A little tweaking can really help sections to not feel like they were simply `CTR+C | CTR+V` from Bootstrap examples.

%[https://media.giphy.com/media/YAy9NNu16pYYg/giphy.gif] 

## Problem 🤔

There's not an out of the box solution for this. We had three options as I saw it:

1. Use Modals from Bootstrap
    
2. Write custom JS and probably use the Modals on top of it
    
3. Find somebody smarter who wrote better JS and use their solution
    

## Bootstrap Modals 📷

![pic of bootstrap modal](https://cdn.hashnode.com/res/hashnode/image/upload/v1652120076566/ayGUY8Xkk.png align="left")

Bootstrap has [modals](https://getbootstrap.com/docs/5.1/components/modal/) which allow for this behavior. However, they are best used for one or two things at a time. When multiple photos are required, you'd have to repeat a bunch of CSS that gets ugly and unruly quickly.

Don't do this.

## Custom Javascript 👨‍💻

You could also write custom JS to prevent the repeat code. But this requires you doing a lot of querySelecting and such that is great if you're learning how JS works and how to write stuff from scratch.

But it's not great when you need to ship a product and want the thing to be functional and as clean as possible.

## BS5-Lightbox 🖼

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1652120127830/wJKSwfVWK.png align="left")

Here's what I found that works like a charm. [BS5-Lightbox](https://github.com/trvswgnr/bs5-lightbox) is written by [Travis A. Wagner](https://github.com/trvswgnr), and solves the lightbox Bootstrap riddle very succinctly.

> A pure JavaScript Bootstrap 5 lightbox that supports images, galleries, YouTube, Vimeo, and Instagram—built around Bootstrap's Modal and Carousel plugins.
> 
> \--<cite>from bs5-lightbox GitHub description</cite>

## Installation ⚙

Three options:

1. [NPM](https://www.npmjs.com/package/bs5-lightbox)
    
2. [Direct Download](https://raw.githubusercontent.com/trvswgnr/bs5-lightbox/main/dist/index.bundle.min.js) (right-click, Save As)
    
3. CDN (add **after** Bootstrap 5's CDN):
    

```html
<script src="https://cdn.jsdelivr.net/npm/bs5-lightbox@1.8.0/dist/index.bundle.min.js"></script>
```

Because I'm simple, I grabbed the CDN approach for our project.

Throw the script at the bottom of your `<body>` and you're good to use this handy library.

### Don't Forget BootstrapJS and Popper 😉

Much of Bootstrap works fine without Javascript and Popper, so I don't use it unless I need it for cases like this. See the documentation for further information, but you can include them both by adding this script at the bottom of your `<body>` as well:

```html
<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/js/bootstrap.bundle.min.js" integrity="sha384-ka7Sk0Gln4gmtz2MlQnikT1wXgYsOg+OMhuP+IlRH9sENBO0LRn5q+8nbTov4+1p" crossorigin="anonymous"></script>
```

## Use ⚒

Add two things to the elements you want to target for the lightbox:

1. `data-toggle="lightbox"`
    
2. `data-src="src-of-asset"`
    

I was targeting images, and wanted to have them appear as links, so I wrapped them in an `<a>` tag:

```html
<a href="/assets/img/small-screen3.jpg">
    <img class="img-fluid rounded pb-1" data-toggle="lightbox" 
    data-src="/assets/img/small-screen3.jpg" src="/assets/img/small-screen3.jpg" 
    alt="screenshot">
</a>
```

## Go and Do Likewise! 🏆

Hope this has been helpful to you! It was a great find for me in this project, and surprisingly took a fair bit of googling before stumbling across. There are many other custom built components that I came across, but this seemed the cleanest.

Drop a star over on its [repo](https://github.com/trvswgnr/bs5-lightbox), and let me know if you've used something else similar.

Come say hey 👋...you can find me on [Twitter](https://twitter.com/EamonnCottrell).

Have a great one!