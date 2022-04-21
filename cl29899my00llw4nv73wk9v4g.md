## Animate an Element Using CSS

## CSS Animations 🏃‍♂️

These things are powerful. You don't need Javascript libraries and complicated know-how to add neat animations to your plain ol' website.

Just a little bit of work can put some pep into the step of your developer toolkit.

This small touch goes a long way on [Jen's](https://twitter.com/lunchbag) [Lunch Money app](https://lunchmoney.app/).

%[https://media.giphy.com/media/UuQ2thBL0UCOJUcKSY/giphy.gif]

I saw this animation back in early 2020 after listening to an Indie Hacker podcast interview with Jen, and it's stuck with me ever since. 

Now, I'm a bit on the quirky side when it comes to details. But I think the point is still valid: **animations (used well) draw attention and make an impact.**

## Make an Element Spin 💫

I have a small use case--a curiosity, really--where I wanted to make a `<div>` spin.

%%[spinner]

Simple enough, eh? But also pretty eye-catching, right!?

## The HTML

Let's make it. I just used a div for simplicity's sake. You can do this to whatever element you want.

```html
<div class=circle></div>
```

## The CSS Class 🖼

> You're only limited by your imagination + your perseverance. 

I want a circle, so:

```css
.circle{
    border-radius: 50%;
    height: 200px;
    width: 200px;
}
```

I want to see that it's spinning, so I'll add a dashed border:
```css
.circle{
    border-radius: 50%;
    height: 200px;
    width: 200px;
    border: dashed white thick;
```

Then to cap it off, we'll add the animation property:


```css
.circle{
    border-radius: 50%;
    height: 200px;
    width: 200px;
    color: white;
    border: dashed white thick;
    animation: spinner 2s infinite linear;
}
```

Okay, that's not going to do anything yet, though. Because we need to direct that [animation](https://developer.mozilla.org/en-US/docs/Web/CSS/animation) property with some `keyframes` 👇.

## The CSS Keyframes 🎬

[Keyframes](https://developer.mozilla.org/en-US/docs/Web/CSS/@keyframes) are going to specify what needs to be happening at different points in time.

If you look at the Lunchmoney example again, the coin starts out at the top, it goes down, and it bounces back to the top. 

Think about the keyframes like key **points** in time. When time is zero (or 0%), the little coin icon is at the top. When time is halfway (50%), it's at the bottom. And then when the loop is concluded (100%), it's back at the top and ready to plunge down again.

All we have to do is instruct the CSS to go through one iteration, and then keep repeating for a certain amount of time. (In our case, that's for all eternity😂).

Check this out:

```css
@keyframes spinner{
  0% {background-color: #3B82F6;}
  50% {background-color:#1E293B;transform:rotate(180deg);}
  100% {background-color: #3B82F6;transform:rotate(360deg);}
}
```
We declare the keyframe (`@keyframes`), we name it (`spinner`), and then we let it know what it needs to do at points in time (`0%,50%,100%`).

In my example above for the spinning circle, I'm changing the background-color from one blue to another and back as well as rotating from 0deg to 180deg to 360deg.

Now that the directions for 1 iteration are in place, take another look at the animation line of our css class:

```css
.circle{
    animation: spinner 2s infinite linear;
}
```

Our CSS now knows to use the keyframes named spinner. We've also told it some other important things. `2s` is of course 2 seconds. We're instructing it to go through the keyframe iteration from 0% to 100% over the course of 2 seconds. `infinite` lets it know to keep doing it forever. 

And `linear` lets it know to keep a constant rate of change. For our circle, we don't want it spinning faster or slower around the transition points (the 0%,50%,100% points).

There are a ton of other options to check out, and as per usual, [MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/animation) is the place to go.

Here's what happens if you make the time 10s instead of 2s and then change linear to ease-in-out:

%%[spinner2]

```css
.spinner2{
    animation: spinner2 10s infinite ease-in-out;
}
```
It slows down overall because the whole rotation now takes 10 seconds to complete. And it also starts slow, eases into "full-speed" and then slows back down at the end of each rotation.

## Thanks! 🙏

I hope that was helpful for you. CSS animations can do a lot to spruce up a page if used well.  Let me know what you think, and how you've used animations in your projects. Leave a comment down below, or connect with me over on [Twitter](https://twitter.com/EamonnCottrell)! 👋

%[https://media.giphy.com/media/l3q2wJsC23ikJg9xe/giphy.gif]