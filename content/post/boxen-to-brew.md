+++
date = "2016-03-28T11:30:26+01:00"
draft = false
title = "Boxen to Brew"

+++

## Automate All The Things!

One of the most painful tasks in development can be configuring a workstation by hand. It's funny how reading this back seems utterly ridiculous, yet little over a year ago this is exactly what I was doing. This became more complex and time consuming as our development team grew in size, so we decided to sort it out in a few key steps:

1. All developers to use the same workstations (MacBook Pros).
2. All workstations to be kept up-to-date with the latest OS X releases.
3. All dependencies for company projects to be installed using Boxen.

## What's in the Boxen!?

[Boxen](https://github.com/boxen/our-boxen#our-boxen) is an open-source tool for automating and managing Macs. It was developed by GitHub, primarily as a tool for themselves to get new starters up and running in about 30 minutes with a single command.

We first adopted Boxen in early 2015, but it has been kicking around since [February 2013 when it was open sourced](https://github.com/blog/1345-introducing-boxen). It proved to be exactly what we needed to align our workstations, and we found it easy enough to customise using Puppet for our own project and personal manifests.

The first few uses were magical. It felt so good to just run a single command and come back 30 minutes later to a fully configured workstation. However, the cracks began to show as new versions of OS X were introduced. With so many dependencies on so many open source Puppet modules, it was inevitable that some of these dependencies would be less supported than others. The builds began failing and I found myself spending more time fixing Boxen than enjoying the benefits of it.

It also didn't inspire confidence to allow my team to keep using a tool that [even the maintainers had abandoned ship on](https://github.com/boxen/our-boxen/issues/783).

{{< figure src="/images/boxen-to-brew/whats-in-the-box.gif" alt="What's in the Box(en)!?" >}}

It was time for a change.

## Boxen Be Gone!

There were no obvious contenders to replace Boxen when I first began the hunt for an alternative. It was only when I took a step back and looked at the component parts of Boxen that I realised I was already sitting on a potential replacement. Boxen uses [Homebrew](http://brew.sh/) as its primary package manager and the [Homebrew Cask](https://caskroom.github.io/) extension for most application installations. Although Puppet was the conductor, orchestrating all of the configuration tasks, it seemed like Homebrew and Homebrew Cask were the ones doing the heavy lifting.

So I found me a brand new conductor in the [Homebrew Bundle](https://github.com/Homebrew/homebrew-bundle) extension.

Homebrew Bundle allows you to create a Brewfile, where you can list all of your dependencies, and just requires you to run a single command to get Homebrew to go and download them all.

Once I had our replacement lined up, it was time to bid farewell to Boxen.

## Nuke

It’s best to take a note of anything that was installed by Boxen and use this to distinguish which packages and applications you’ll need when you make the jump to Homebrew.

To uninstall (almost) everything Boxen-related you need to run the following in your terminal:

    $ cd /opt/boxen/repo; ./script/nuke —all —force

Amazingly the flags `—all` and `—force` don’t actually remove everything that was installed by Boxen so you may have to go sniffing around for any leftovers.

## Something Tasty Is Brewing

Remember that bit where I said you should take note of anything that was installed by Boxen? This is where that comes in handy! My list of requirements as a web developer was as follows:

-   Atom
-   Bash completions for Git / Vagrant
-   Git
-   MySQL Workbench
-   Node 0.12
-   Vagrant
-   VirtualBox

The next step is to translate this list in to a Brewfile. This is essentially a list of Homebrew commands, so you can easily work these out by just reading up on how you would individually install each of these packages. Here is what my list translates to:

    tap 'caskroom/cask'
    tap 'homebrew/completions'
    brew 'bash-completion'
    brew 'git'
    brew 'homebrew/completions/vagrant-completion'
    brew 'homebrew/versions/node012'
    cask 'atom'
    cask 'mysqlworkbench'
    cask 'vagrant'
    cask 'virtualbox'

To be able to run this file we need to first install Homebrew and the Homebrew Bundle extension, which can be done by running the following in your terminal:

    $ /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
    $ brew tap Homebrew/bundle

You then just need to navigate to the directory that your Brewfile is sitting in and run:

    $ brew bundle

That's it! Everything in your Brewfile should be installed and you're up and running on a new development workstation.

## Mo' Automation, Mo' Fun

The Brewfile I created above serves more as a personal manifest than a project based one, so the next step is to create a Brewfile for each project.

You can also remove a few of the manual tasks by rolling all of those terminal commands in to a shell script, much like what I've done with my [setup script in my personal dotfiles repository](https://github.com/richardtoner/dotfiles/blob/master/bin/setup).

This approach has worked wonders for our development team in the last few months and installation times on new workstations are as little as a couple of minutes, as we avoid installing all of the additional packages and applications that Boxen enforced by default.

It is also incredibly rewarding to know that any new dependencies will be installed without having to cross my fingers that Boxen will be able to cope. Homebrew always copes, and that fact alone makes Homebrew a winner in my books.

***

## The Like List

### **Food:** Rossa Pistachio Gelato

My newfound obsession with pistachio flavoured ice cream has drifted in to dangerous territory with the discovery of Rossa's pistachio gelato... Our local Spar supermarket in Walthamstow stocks it and it may very well be the eighth wonder of the world. Their website unfortunately isn't the most informative in listing stockists, but if you like pistachio ice cream then my hyperbole should be enough to encourage you to sniff it out! Find out more over at [www.rossaicecream.com](http://www.rossaicecream.com/).

{{< figure src="/images/boxen-to-brew/rossa-gelato.jpg" alt="Rossa Gelato" >}}

### **Music:** The Menzingers - On The Impossible Past

I'm still a bit confused by how I've slept on this album for the last 4 years. [Absolutepunk.net](http://absolutepunk.net/) is undoubtedly my most-visited music website and this album was given the highest praise by being announced as the staff's [#1 album of 2012](http://www.absolutepunk.net/showthread.php?t=2971122). It is deserving of that praise as well, as it is a glorious nostalgia-tinged collection of punk anthems that go against the grain of conventional song structures and vocal deliveries. See what all the fuss is about for yourself by hitting play below:

{{< spotify "spotify:album:4Jh3PDPicP3QwWpktQS7Yh" >}}

### **Travel:** St George's Gardens, London

In 2002 Time Out magazine declared St George's Gardens one of London's best kept secrets. It is now 2016 and it is still one of London's best kept secrets. I altered my commute to work to try and introduce some green space on my walk from Kings Cross to Holborn, and this is certainly the highlight of my morning. It is only small, but it makes up for size with beauty, especially when you catch it on a sunny morning. Find it [here](https://goo.gl/maps/XWF6BeWSKtM2).

{{< figure src="/images/boxen-to-brew/st-georges-gardens-london.jpg" alt="St George's Gardens" >}}
