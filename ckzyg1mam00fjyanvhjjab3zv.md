## D3 Beginner's Scatterplot Project

I've been working through freeCodeCamp's Data Analytics with [D3 certificate program](https://www.freecodecamp.org/learn/data-visualization/#data-visualization-projects) for a while now, and have thusfar completed the first two of the projects in the certificate: the [Bar Chart](https://codepen.io/Diarin/pen/MWEMjmw?editors=1111) and the [Scatterplot](https://codepen.io/Diarin/pen/jOaaWjq?editors=0110).

I have to admit that D3 has proven more strenuous than I at first imagined. As with many things, the concept of a javascript library to produce sweet graphs and charts seemed really easy to implement. However, to fully grok and to use correctly has been a fun exercise.

And the [documentation](https://d3js.org/) is overwhelming to say the least.

From the very beginning, I was Googling how to do things...and I do mean from the very beginning. I failed to put all of my code within the .then declaration at first. 

And such was my cadence (as is rightly the case) from then on: search for how exactly to do something...try it out...search again...tweak it till it works.

I've utilized the healthy habit of console.log()ing practically everything under the sun too. Especially towards the beginning of a project, I'll make a bunch of variables (some I need, others I need to dummy-proof code) and then console.log() everything to make sure it's working properly. This has saved me a bunch of heartache, I'm sure.

Here's the beginning of my scatterplot project where I first set up a timeParse variable that I have to use later to properly setup the times for my y-axis data and scale. Then I grab info from the data to setup my domain values.


``` javascript
  let minutes = d3.timeParse("%M:%S")
  let minYear =(d3.min(data,(d)=>d.Year))
  let maxYear =(d3.max(data,(d)=>d.Year))
  let minTime =minutes((d3.min(data,(d)=>d.Time)))
  let maxTime =minutes((d3.max(data,(d)=>d.Time)))

``` 

I encountered formatting issues galore throughout my time in the scatterplot project. And it was here where I particularly had a lot of trial and error to figure things out. I used [scaleTime()](https://observablehq.com/@d3/d3-scaletime) for the scale and axes since we're dealing with dates and times on the x and y axes, respectively: 

``` javascript
  const xScale = d3.scaleTime()
    .domain([minYear-1,maxYear])
    .range([padding, w-padding])
  const xAxis = d3.axisBottom(xScale)
    .tickFormat(d3.format(".0f"))
```

An area that held me up from passing the tests for a long time was with the "cy" value. I failed to use the minutes() timeParsing variable at first, and almost trashed the whole thing before I realized my omission:

``` javascript
 svg.selectAll(".dot")
    .data(data)
    .enter()
    .append("circle")
    .attr("class","dot")
    .attr("r", 8.5)
    .attr("cx",(d)=>xScale(d.Year))
    .attr("cy",(d)=>yScale(minutes(d.Time)))
```

I made a simple if statement within the style section to setup the color of the dots:

``` javascript
  .style("fill",function(d,i){
      if(d["Doping"]===""){
        return ("rgb(251,180,174)");
      }else{
        return("rgb(179,205,227)")
      }
```

For the legend, I found a helpful article [here](https://www.d3-graph-gallery.com/graph/custom_legend.html#cont1) that I used. In it, I also learned about [scaleOrdinal()](https://observablehq.com/@d3/d3-scaleordinal) which is a sweet way to "...consistently return the same value for the same thing"

This was way overkill for my small dataset, but a fun learning opportunity, nonetheless!

``` javascript
  let key = ["No doping allegations", "Yes doping allegations"]
  let colors = d3.scaleOrdinal()
    .domain(key)
    .range(d3.schemePastel1)

```

Writing out the code for all this was much longer than just hard-coding the short, two item legend, but again, I enjoyed learning about this: 

``` javascript
svg.append("text")
    .text("Legend go here")
    .attr("id","legend")
    .attr("x", w-padding*4.5)
    .attr("y", 150)
  svg.selectAll("legenddots")
    .data(key)
    .enter()
    .append("rect")
      .attr("x",w-padding*2).attr("y",(d,i)=>175+i*(20+5)).attr("width",20).attr("height",20).style("fill",(d)=>colors(d))
    svg.selectAll("legendlabels")
      .data(key)
      .enter()
        .append("text")
        .attr("x",w-padding*7).attr("y",(d,i)=>185+i*(20+5)).attr("width",20).attr("height",20).style("fill",(d)=>colors(d)).attr("text-anchor","left").style("alignment-baseline", "middle")
        .text((d)=>d)
```

Check out my complete code on Codepen [here](https://codepen.io/Diarin/pen/jOaaWjq?editors=0110), but a word of caution if you are yourself working through this certification: don't just copy something here because it works (you can do that straight from the example they've given at freeCodeCamp). 

I learned a ton through the headache of not understanding why something wasn't working at first. I encourage you to walk through that pain, search around, and try a lot of stuff out. This is where the learning truly takes place! 

Follow me on [Twitter](https://twitter.com/EamonnCottrell), I'd love to say hi!

Same deal on [LinkedIn](https://www.linkedin.com/in/eamonncottrell/)!

Good luck and happy coding!