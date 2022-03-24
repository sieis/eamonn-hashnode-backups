---
title: Infinite Memory
cover_image: 'https://blog.eamonncottrell.com/_next/image?url=https%3A%2F%2Fcdn.hashnode.com%2Fres%2Fhashnode%2Fimage%2Fupload%2Fv1645985389253%2FW5e_iWYIN.jpg%3Fw%3D1600%26h%3D840%26fit%3Dcrop%26crop%3Dentropy%26auto%3Dcompress%2Cformat%26format%3Dwebp&w=1920&q=75'
published: true
canonical_url: 'https://blog.eamonncottrell.com/infinite-memory'
tags: 'netlify,javascript,netlifyhackathon,html5,css'
---

## Infinite Memory

## The Product

I have created a memory tool. 

Check it out [here](https://infinite-memory.netlify.app/). And the code is [here](https://github.com/sieis/infinite-memory).

The world is digital, but the mind remains tactile and hungry. I am participating in a two year study with 12 other guys in which, among other things, we are memorizing scripture along the way. I began to ponder a web app to help in this, and Infinite Memory was born.

Most of my own experience in memorizing anything has come from exposure and repetition. Reading and reciting passages. Writing out verses and formulas. Practicing music over and over. Listening to the piece or the passage.

And it appears the science backs this up too. My friend [Anthony](https://twitter.com/ajcwebdev) pointed me towards a concept called [spaced repetition](https://en.wikipedia.org/wiki/Spaced_repetition) after I'd initially published this article. Tools like [Quizlet](https://quizlet.com/) utilize repetition methods you may remember from flashcards if you, like me, are old enough to have used pen and paper in school. 

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1646098536266/AoW77LDjs.png)

In a nutshell, the spaced repetition technique has you putting more space between reviewing the items that you remembered more easily while you continue to review the things that you have difficulty with. (I hope I'm not butchering the premise...but this holds perfectly true in what my own experience has shown to be effective.)

And this is exactly why I've been using tools like Infinite Memory to burn into my consciousness the things I want to remember.

In designing the app, I wanted to provide a place to be exposed to the verse in three formats: 
  1. the visual, written passage
  1. an audio recitation
  1. an interactive opportunity to write (type) the verse

On the whole it didn't seem much, and furthermore it appeared something easy to accomplish with vanilla JavaScript. 

> I embarked on a minimalist creation in which I could use the least amount of tooling possible to get the job done.

![infinite-memory.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1645986184756/qGcX6eRte.jpg)

## The Code

I find the process of creation most invigorating when drawing up plain HTML, CSS and Javascript rather than firing up a Node server or installing a gazillion dependencies.

An ```H1``` title on the page was all I needed to start. I added a ```div``` to hold my eventual verses, and also a ```div``` to serve as a sidebar to select different verses.

I wanted the code to be as clean as I could make it, so I made a JSON file for the three pieces of information I wanted to use throughout the app. An array of objects was all that was necessary, and within each object was the reference location of the verse i.e. Psalm 27:4, the text of the verse, and a string ID from my podcast host to let me embed audio for each verse.

Having my HTML and JSON, I needed to manipulate the date with Javascript to display and interact with. I did not want to style everything from scratch, so I used [Bootstrap 5](https://getbootstrap.com/docs/5.0/getting-started/introduction/) with only a couple pieces of custom CSS in main.css. More on style in a moment...

## The Functionality

I didn't want to use any frameworks like React, so I did a lot of ```document.getElementById()``` to create variables and add pieces of my JSON to my HTML. 

I was able to accomplish the bulk of the work with ```forEach``` loops going through the JSON and setting the innerHTML of the proper ```div```.

```javascript
data.forEach(i => {
        list.innerHTML += `<div id="${i.location + "verse"}" class="card" style="display:none">
                            <div class="card-body text-center">
                                <h3 class="m-3 card-title">${i.location}</h3>
                                <p class="m-5 fs-5 card-text" id="${i.location + "text"}" >${i.verse}</p>
....
```

After having set ```display:none``` on all the created cards in the innerHTML, I had each of the reference buttons at the top of the page have an ```onclick``` to toggle the visibility of individual verses.


![toggle.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645986102693/Ky_vopX-Q.png)

```javascript
x.onclick = showCard = () => {
            if (y.style.display === "none") {
                y.style.display = "block"
            } else {
                y.style.display = "none";
            }
        }
```

For interactivity, I wanted a few things to be possible:
1. removing words one at a time from the verse
1. toggling the whole verse's visibility
1. typing the verse and checking for accuracy against the original.

To remove words one at a time, I turned the verse into an array of strings: ```let verse = i.verse.split(" ")``` and then added a button that would, when clicked, remove a randomly selected string from the array:
``` javascript
b.onclick = memorize = () => {
            let randNum = Math.floor(Math.random() * verse.length);
            // remove one word from verse array based on random position
            verse.splice(randNum, 1);
            // join remaining words into string
            t.innerHTML = verse.join(" ");
            randNum = Math.floor(Math.random() * verse.length);
            console.log(t.innerHTML)
        }
```

> I actually really enjoyed all the vanilla Javascript and adding ```onclick``` functions to all the buttons :)

To toggle the whole verse's visiblity, it was simply another button to toggle the display from none to block and back: 
``` javascript
hideVerse.onclick = showWords =() =>{
            if(wholeVerse.style.display === "none"){
                wholeVerse.style.display = "block"
            } else{
                wholeVerse.style.display = "none"
            }
        }
```

And then I added a form within each of the verse's cards to practice typing out the verse.

```html
<form>
  <div class="px-5 my-3">
    <label for="memorySample" class="my-3 fs-4 form-label">Try to Type Verse</label>
    <textarea name="textarea" cols="6" rows="6" class="form-control" 
    id="${i.location+"memory"}"></textarea>
  </div>
</form>
```

I wanted to have something happen when you checked for accuracy, so I built in another button that checked the value of the textarea from the form with the original verse. This way, even if you'd deleted some of the words from the array, you'd still be checking against the original verse. If you got it right, the background turns green, and if wrong, it turns red. 

Small touch, but very satisfying!

```javascript
verseChecker.onclick = () =>{
            let typedVerse = document.getElementById(`${i.location+"memory"}`)
            console.log("typed verse: ",typedVerse.value.toLowerCase(),"\noriginal verse: ", originalVerse.toLowerCase())
            if(typedVerse.value.toLowerCase() === originalVerse.toLowerCase()){
                // change background of card to green
                // downside: punctuation matters. this'll only turn green if you get everything exactly right (other than capitalization)
                y.style.backgroundColor = "#62fc89"
            }else{
                // change background of card to red
                y.style.backgroundColor = "#fc6262"
            }
        }
```

And then, a final ```onclick``` button to reset the card without refreshing the whole page:

```javascript
resetVerse.onclick = () =>{
            let typedVerse = document.getElementById(`${i.location+"memory"}`)
            y.style.backgroundColor="#fff"
            typedVerse.value = ""
        }
```

## UX/UI

Again, for the sake of simplicity, I wanted the initial version to be as barebones as possible. There is no navbar, there is no footer, there is nothing except for the app itself. For issue submissions, please see the [Github page](https://github.com/sieis/infinite-memory/issues), but for now, I wanted the app to be very much a minimalist, usable tool to meet my very niche use case.

I adopted Bootstrap 5 because it is very easy to implement, I'm comfortable with the basics, and it takes very little effort to make at least a clean, well aligned page. 

I adjusted some of the coloring on buttons to a color that I preferred over the stock Bootstrap colors, and then grabbed a couple of svgs from [Undraw](https://undraw.co/illustrations) in matching colors to round off the hero section. 

Bootstrap has several examples [here](https://getbootstrap.com/docs/5.0/examples/) that are great starting points. I snagged the code for one of the hero sections after the main functionality of the site was up and running. 

> Confession: I can lose hours in Adobe Illustrator tweaking design stuff. I was careful to tackle the functionality of Infinite Memory before trying to make it look good. In the same way, I tried to write this whole article before creating the banner image. Spoiler: I did not make it all the way. I made the banner about 2/3 through writing! ;)

![banner.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645987586238/Uu-DhPYFw.png)

## Summary

This was an extremely fun project to work on, and I enjoyed making a web app that solves a real world problem that I've been experiencing. This is perhaps as edge-case as it gets, what with scripture memory not being a very sought after skill afaik...but it made for a great project nonetheless!

I decided to enter way late in the month, so I expect my app is about as lite as it gets while still meeting the criteria. And I look forward to future hackathons as I continue to build out my own skill sets.

Check out [Infinite Memory](https://infinite-memory.netlify.app/) and let me know what you think. 

Here's the [Github](https://github.com/sieis/infinite-memory).

And I'd love to say hey...shoot me a line on [Twitter](https://twitter.com/EamonnCottrell) and/or [LinkedIn](https://www.linkedin.com/in/eamonncottrell/).

Thanks for reading and have a great one!