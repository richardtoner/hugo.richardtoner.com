+++
date = "2016-03-14T00:15:04Z"
draft = false
title = "Ready... Set... Hugo!"

+++

## An Introduction of Sorts...

Hi! This is my first post and I have already hit the backspace key more times than I have in the whole of 2016 put together... I can tell this is going to be a bit interesting (or really time consuming).

The intention of this website is to act as a place for me to ramble on about the things that I like.

-   I like **code**
-   I like **food**
-   I like **games**
-   I like **lists** (especially alphabetically ordered ones like this one)
-   I like **movies**
-   I like **music**
-   I like **travel**

With this being the first post, I'll be dipping into the first one in that list and talk a bit about how I made this website.

## Hugo!

This website is made using [Hugo](http://gethugo.io).

I was first introduced to Hugo a few months back when I was checking out the personal website of a very promising applicant to join our development team at [Snap Fashion](https://www.snapfashion.co.uk). I'm always interested in seeing what tools developers use to build their personal websites, as I feel that it is a big indication of what interests them the most. There was something about her website that inspired me to want to do the same for myself - so credit where credit is due: Thanks [PurpleBooth](https://purplebooth.co.uk)!

## Hugo?

> Hugo is a general-purpose website framework. Technically speaking, Hugo is a static site generator. Unlike other systems which dynamically build a page every time a visitor requests one, Hugo does the building when you create your content. Since websites are viewed far more often than they are edited, Hugo is optimized for website viewing while providing a great writing experience.
>
> -- <cite>[The Brainy Bunch Behind Hugo](http://gethugo.io/overview/introduction/#what-is-hugo)</cite>

Sounds cool, right? It is. And it is ridiculously easy to pick up.

## Getting Started

The [Hugo docs](http://gethugo.io/overview/quickstart) have everything you need to get started, but I'll talk through what I did to show you exactly how easy it was for me to get to the point of publishing this post on a live website.

### Step 1: Installation

I installed with Homebrew by running:

    $ brew update && brew install hugo

### Step 2: Create a Site

I could then create the skeleton for a new website by running:

    $ hugo new site ~/Sites/my-hugo-website

### Step 3: Create a New Post

After navigating to my new website directory I created a new post by running:

    $ hugo new post/ready-set-hugo.md

That's less than a minute of effort and I was already writing content for a brand new website!

### Step 4: Pick a Theme

The Hugo website has a wide variety of themes available on [themes.gethugo.io](http://themes.gohugo.io). I decided to go with the [Hugo Uno](http://themes.gohugo.io/hugo-uno) theme for starters, which I grabbed from Github by running:

    $ git clone git@github.com:SenjinDarashiva/hugo-uno.git ./themes/hugo-uno

### Step 5: Have a Peek

With a theme installed I could then run Hugo server to take a look at my brand spanking new website by running:

    $ hugo server --theme=hugo-uno --buildDrafts

This command compiles the drafts and then hosts the website locally on an unused port. Hugo will tell you what web address you can visit to access your website once it finishes compiling (which is near instantaneous).

Behold!

{{< figure src="/images/ready-set-hugo/hugo-website-preview.png" alt="My glorious work in progress!" >}}

### Step 6: Hugo's Watching You Wazowski... Always Watching...

With the Hugo server up and running I kept editing this post, and Hugo simply kept an eye out for any updates, automatically compiling any new changes and instantly showing them to me within my web browser like magic.

### Step 7: Hit Publish

When I finished up writing I then published the blog post by running:

    $ hugo undraft content/post/ready-set-hugo.md

### Step 8: Configure It Out

So the blog post was dated, published and ready to put live! Before putting the website live though I wanted to replace all that default stuff such as the site name, description and URL with my own stuff. All this required was for me to open up the `config.toml` file in the base directory and populate it with the following information:

    baseurl = "http://richardtoner.github.io"
    languageCode = "en-gb"
    title = "Richard Toner"

    [params]
      description = "A Welshy in London"
      author = "Richard Toner"
      github = "richardtoner"

I also changed the default background image by adding an image to `./images/background-cover.jpg`.

To see what other default stuff you can change, just take a look at the theme's README.

### Step 9: My Generation

The only Hugo-shaped thing left to do at this point was to generate the static content, which I did by running:

    $ hugo --theme=hugo-uno

### Step 10: Put It Somewhere People Can See It

The command I ran in the last step placed all the static content in `./public`, so I just needed to plop the contents of the directory somewhere where people could see it. I personally chose to host it on [GitHub Pages](https://pages.github.com/), which was as easy as committing all of the public directory contents to my `richardtoner.github.io` repository and pushing.

***

## Summary

Hugo is a breeze to get up and running with.

I found it refreshing to approach a new website implementation and having to dedicate very little thought at the technical implementation and design. The majority of my focus has been on **the content**, which is the most important facet of a website of this nature.

I plan to explore some of the more advanced features of Hugo soon. I will undoubtedly want to customise this theme or create my own, so I'll probably describe that process in a future blog post.

If you got this far - thanks for reading my first ever blog post! Hopefully this will be the first of many!

***

## The Like List

So this little section is directly inspired by Ryan O'Neal aka [Sleeping At Last](http://www.sleepingatlast.com), a brilliant and prolific musician from Illinois who has nailed down the art of a good newsletter.

Ryan runs a conceptual music subscription service called **"Atlas"**, where he releases a song every few weeks complete with individual digital artwork, lyrics and the story behind the writing process of each song. He signs off each email with a list of the things he currently loves, and I look forward to it with each email. We have a great cross-over of interests, but the list also acts as a time capsule that I think serves purpose to him as well as his fans as a reminder of what he was surrounded by at the time of putting together that piece of art. I don't really consider this post to be a piece of art, but I bloody love a good list!

So here it is:

### **Food:** Olia Hercules

A highly talented Ukrainian chef with a love for everything fermented. We were fortunate to attend her event **Fermented & Wild**, a celebration feast of fermented food and natural wines. I would not be surprised if they organised more of these in the future, so it's worth giving her a follow on Instagram and keeping your eyes peeled if you're privy to pickles!

{{< instagram id="BCkte9bFKqy" hidecaption="true" >}}

### **Games:** Rocket League

Remember that episode of Top Gear where they played football with cars and it looked like the best thing ever? Well if you throw in some insane physics, a spherical bomb and turbo-powered cars, you are left with Rocket League. It is as awesome as it sounds. Check out the madness in the video below.

{{< youtube 2C9LxNlzeUM >}}

### **Music:** yndi halda - Under Summer

The wait is over! The long-awaited sophomore release from yndi halda has been 10 years in the making and holds true to the theory that good things come to those that wait. Under Summer is an hour-long musical journey over 4 tracks of beautiful introspective movements that swell to tidal wave-like crescendos. Prepare to get swept away and hit play on the Spotify player below:

{{< spotify "spotify:album:0ECiAUBuKpQ6sKaKUFFtlu" >}}

### **Travel:** Bristol

What better way to enjoy an album that you've been anticipating for a decade than to take a walk through the city that you first remember falling in love with the band? Bristol has carved a very special place in my heart from the University days, and it was great to experience something so new in a place so familiar.
