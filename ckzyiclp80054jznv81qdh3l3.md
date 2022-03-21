## Hashnode Subdomain with Netlify and Google Domain

If you're like me, you overcomplicate things.

<iframe src="https://giphy.com/embed/qucJWFolJN6rS" width="480" height="244" frameBorder="0" class="giphy-embed" allowFullScreen></iframe><p><a href="https://giphy.com/gifs/avril-lavigne-complicated-music-video-qucJWFolJN6rS">via GIPHY</a></p>

I made a custom Hugo theme for my personal portfolio and blog site last year. Here's the [Github](https://github.com/sieis/cottrell-theme). Here's the [main site](https://www.eamonncottrell.com/). 

I registered the domain with Google. But I deployed the site with Netlify. Because I wanted to be awesome, learn many things, and take a circuitous route to the finished product.

%[https://media.giphy.com/media/Af7ap9r7NzJJe/giphy.gif]

This year, I realized that it may actually be a solid idea to be publishing articles on a proper platform like Hashnode. 

Thankfully, I can do both!

Part of the appeal of Hashnode is the mapping of the blog to a [custom domain](https://support.hashnode.com/docs/mapping-domain/). But when I went into Google Domains, I realized I'd set things up to use the DNS servers at Netlify.

![pic](https://cdn.hashnode.com/res/hashnode/image/upload/v1645555912603/5hL6gFjeE.png)

Fear not! 

Heading over to [Netlify](https://www.netlify.com/), all that is needed is to setup a new record under the DNS settings here. The record type is CNAME, the name is whatever you want...in my case, I wanted it to be blog. And the value is hashnode.network. I left the TTL part blank (it's optional).

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645556104231/ELnDYcRNK.png)

And, that's it. It can take up to 24hrs to propagate, but mine worked at [blog.eamonncottrell.com](https://blog.eamonncottrell.com/) almost immediately. 

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645556055224/1sqV4PF07.png)

Now I've got a couple choices that I'm not fully committed on yet. I could hop back into the code to my [portfolio site](https://www.eamonncottrell.com/posts/) and redirect the blog posts to Hashnode. Or I could have them living in both places. Redundancy here seems dumb, but I do still kind of like that I've got a custom built template over on my domain.

What do you think I should do?

Let me know!

Reach out over on [Twitter](https://twitter.com/EamonnCottrell) and/or [LinkedIn](https://www.linkedin.com/in/eamonncottrell/) and tell me what you think.

Here's my [portfolio site](https://www.eamonncottrell.com/posts/).