---
title: Re-Publishing Hashnode Articles to DEV with GitHub Actions
published: true
cover_image: 'https://blog.eamonncottrell.com/_next/image?url=https%3A%2F%2Fcdn.hashnode.com%2Fres%2Fhashnode%2Fimage%2Fupload%2Fv1648146153672%2F7cAZKA2CB.jpg%3Fw%3D1600%26h%3D840%26fit%3Dcrop%26crop%3Dentropy%26auto%3Dcompress%2Cformat%26format%3Dwebp&w=1920&q=75'
canonical_url: 'https://blog.eamonncottrell.com/re-publishing-hashnode-articles-to-dev-with-github-actions'
tags: 'github,dev,developerblogging,tutorial'
---
## Re-Publishing Hashnode Articles to DEV with GitHub Actions

## Prerequisite

1. A @Hashnode account w backup to GitHub
1. A DEV account w API key
1. A GitHub account

## Backup Repo

You'll want to backup your @Hashnode articles to your GitHub account first. I wrote about how to do that [here](https://blog.eamonncottrell.com/hashnode-auto-backup-posts-on-github) and it's pretty easy to do.

![Hashnode-AutoBackup.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1648059300218/82Avo86g3.jpg)

## DEV API key

Go [here](https://dev.to/settings/account) and grab an API key. This is the only setup you need over on DEV. 

Don't share the API key! 😁

![Don't Share API Key](https://cdn.hashnode.com/res/hashnode/image/upload/v1648059673161/uwuwT2zmi.png)

## GitHub Actions

If you, like me, have never used GitHub Actions, let me break down a few things as I am learning in real time too.

Actions will "Automate your workflow from idea to production". [Here's the features page](https://github.com/features/actions) from GitHub.

It's just a way to automate stuff that needs to happen. Events are triggered when you make a commit to your repository. For us, it's perfect since we want a commit to our Hashnode backup repository to trigger a new post to be made over on DEV.

[Here is the publish-devto Action](https://github.com/marketplace/actions/publish-to-dev-to) on the GitHub Actions Marketplace. It is not certified by GitHub and is provided by a third-party. 

This was created by [Yohan Lasorsa](https://github.com/sinedied).

[Here is the repo](https://github.com/sinedied/publish-devto) for the publish-devto Action.

It works by "delegat[ing] most of the work to the [devto-cli](https://github.com/sinedied/devto-cli) push command".

![Publish to dev.to .yml screenshot](https://cdn.hashnode.com/res/hashnode/image/upload/v1648059783448/7uTmRN46U.png)

### .yml ftw

The directions for Actions live inside a .yml file at ```yourRepo/.github/workflow/publish.yml```. 

Below is the complete .yml from the [sample devto-github-template](https://github.com/sinedied/devto-github-template/blob/main/.github/workflows/publish.yml).

````yml
# This workflow will push and update articles on dev.to each time a new
# commit is pushed to the main branch.
#
# To make it work, you need a dev.to API key, see:
# https://developers.forem.com/api/#section/Authentication/api_key
#
# Once you have generated the token, you need to add them as a secret in your
# GitHub repository:
# - DEVTO_TOKEN: your dev.to API key
# See https://help.github.com/en/actions/configuring-and-managing-workflows/creating-and-storing-encrypted-secrets#creating-encrypted-secrets
# for more information about GitHub secrets.

name: publish
on:
  push:
    branches: [main]
  pull_request:
    branches: [main]

jobs:
  publish:
    runs-on: ubuntu-latest

    steps:
    - uses: actions/checkout@v2
    - name: Publish articles on dev.to
      uses: sinedied/publish-devto@v2
      id: publish_devto
      with:
        # Your dev.to personal API key to publish and update articles.
        # See https://docs.dev.to/api/#section/Authentication/api_key
        devto_key: ${{ secrets.DEVTO_TOKEN }}
        # Your GitHub personal access token, used to create commits for updated files.
        # If you have a protected branch, you need to use a personal access token
        # with the 'repo' permission.
        # See https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token
        github_token: ${{ secrets.GITHUB_TOKEN }}
        # (Optional) The files to publish. Default is "posts/**/*.md"
        files: 'posts/**/*.md'
        # (Optional) The git branch to use. Default is 'main'.
        branch: main
        # (Optional) Use conventional commit messages. Default is false.
        # See https://www.conventionalcommits.org. 
        conventional_commits: true
        # (Optional) Do not make actual changes on dev.to if it's a pull request.
        dry_run: ${{ github.event_name == 'pull_request' }}

    # (Optional) Add comment with dev.to changes if it's a pull request.
    - uses: actions-ecosystem/action-create-comment@v1
      if: ${{ github.event_name == 'pull_request' }}
      with:
        github_token: ${{ secrets.GITHUB_TOKEN }}
        body: |
          Changes result:
          ```
          ${{ steps.publish_devto.outputs.result_summary }}
          ```
````

## Config for Hashnode Backup Repo

You can clone and use the [devto-github-template](https://github.com/sinedied/devto-github-template), however because Hashnode has us setup to backup straight to the root of our backup repository, we'll need to change a couple things. 

![Github Hashnode Backup Repository](https://cdn.hashnode.com/res/hashnode/image/upload/v1648061320425/HNKud9R9b.png)

### Create and edit a .yml file

I'm going to create the ```.github/workflows/publish.yml``` myself rather than cloning anything. If you've copied the contents of the devto-github-template, you'll want to change the ```files: ``` line to reflect where all the Hashnode articles live in the repo. 


![Files in markdown](https://cdn.hashnode.com/res/hashnode/image/upload/v1648137713475/4b9P_WzbA.png)

### Add Front Matter to Posts

I neglected this part at first, and was met with errors. I'm grateful to [Yohan](https://twitter.com/sinedied), the author of the **publish-devto**, for taking the time to do some troubleshooting with me!

You'll need the front matter to contain at least a title for the Action to recognize the post. [Here](https://github.com/sinedied/devto-github-template/edit/main/posts/example.md) is the example post from the devto-github-template.

And, as you'll see in the issues section at the bottom of this article, you'll probably want to include the `published: true` line below as well.

```yml
---
title: Example article title
published: false
description: A simple test article
tags: 'productivity, beginners, test'
cover_image: ./assets/cat.jpg
canonical_url: null
id: 853728
---

Some random text with a [link](https://code.visualstudio.com).

## Serious title

Add some text here and there!

![and some pictures too](./assets/cat.jpg)

```

## Canonical URL

After having posted to Hashnode, grab the url of the published article so you can include this in the front matter for DEV. 

Honestly, this front matter stuff is the only real hiccup part. In the current state, we'll need to edit the markdown file on GitHub in order for this to work. And doing that is a step in an otherwise seamless automation. I suspect this is something that could be added. I may do some more digging, but for now: onward!

## GitHub Secrets 🤐

You need to plug a couple things into the GitHub Hashnode Backup Repo as **secrets**. This is where you'll put your API key from DEV and your personal access token from GitHub.

![github secrets](https://cdn.hashnode.com/res/hashnode/image/upload/v1648062747015/X_SytDclO.png)

Make a new secret named DEVTO_TOKEN and paste your DEV API key into the value. If you have a protected branch, you'll need to do the same for GITHUB_TOKEN as a new secret: 

![paste dev api](https://cdn.hashnode.com/res/hashnode/image/upload/v1648062837125/WQuZcJVCT.png)

## Push!

You should be good. I am making a small change to one of my previous posts and then adding the front matter to see if it properly triggers the action on my account now...

## Action Status

After a bit of confusion, I found that GitHub has a [status page](https://www.githubstatus.com/), and that Actions are currently experiencing issues! If you happen to be doing this and not triggering the workflow action at all, check out the status page before melting down! 😆

![GitHub Status](https://cdn.hashnode.com/res/hashnode/image/upload/v1648138627504/yRfGZTdKD.png)



## Great Success!

Excellent! This works, and should allow you to cross-post on DEV smoothly! 
[Here's the link](https://blog.eamonncottrell.com/hashnode-auto-backup-posts-on-github) to my previous post on setting up auto-backups from Hashnode to DEV. That's half the job right there.

**Note:** When your post shows up on DEV, it will be a Draft. So you will have to go in and publish it there.

![Draft Post in DEV](https://cdn.hashnode.com/res/hashnode/image/upload/v1648142500967/NlCY-JFSL.png)

### Issues

- I'd used triple ticks for inline code on Hashnode which displayed ok. It fouled things up on DEV where a single tick is expected for inline code.
- If you've used any Hashnode embeds like for YouTube, those won't work. You'll need to reformat over on DEV into regularly accepted markdown format. I found this out when a gif from Giphy didn't work on my post
- Changes to an article made via Hashnode will remove any front matter you've added to your repo and will therefore not be reflected on DEV. You'll have to pull those changes down, add the front matter back in and then push back to GitHub.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1648144845754/LPKpZ6GhG.png)

- **Big issue but fixable: **the unpublished draft on DEV doesn't have a place to publish it at the bottom of the post like usual


![Missing Publish Button](https://cdn.hashnode.com/res/hashnode/image/upload/v1648144254698/gxDpOHTO7.png)

Remarkably, there doesn't seem to be a way to publish it from the web app. I believe it's because of the front matter we added. If you recall above, there are some other values for the front matter including a `published: ` optional value. Apparently, if it's not there, it will default to false.

I added a true value to my next test article, and voila! It worked like a charm!

[Here's one](https://dev.to/sieis/version-releases-and-git-tags-for-beginners-3m0g) of the first articles over on DEV that I successfully imported using this method. 


## Thank You & Please Share 🙏

Let me know if you find any issues or better ways to do this! Also, if anyone has it setup the other way: from DEV to Hashnode, I'd be interested in checking that out too.

Would you share this article for me? I'm building my personal content portfolio and every exposure is helpful! Thanks a ton! 

You can find me over on [Twitter](https://twitter.com/EamonnCottrell); I'd love to say hey!

%[https://media.giphy.com/media/3rgXBvIgbTYX4PWZe8/giphy.gif]