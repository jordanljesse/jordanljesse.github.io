---
layout: post
title: "Managing multiple Ruby versions"
date: 2017-09-18 23:20:20 -0500
comments: true
categories: general ruby tools
published: true
---

The other day I decided to dust off this Octopress blog that I had started back in the Spring of this year to find that my `rake` tasks weren't running properly. After a brief search of the web it seemed that outdated versions of Ruby were to blame. However, I still need to maintain these older versions of Ruby for other projects I'm working on. With that in mind, I set about learning how to manage multiple versions of Ruby on my Mac and stumbled across [rbenv](https://github.com/rbenv).
<!-- more -->

First I'll go over why I chose to use rbenv over similar tools like RVM and then get into how to install and use rbenv. The main reasons I choose to go with rbenv are:

- it's _light_ compared to RVM
- I can set *application-specific Ruby versions*
- *no configuration file!*
- easier to get set up and back to work

What rbenv does is essentially create a sandboxed Ruby environment for our project in which we get to control which version of Ruby is run, separately from the version that may be the default for our system. To start using rbenv you'll want to have Homebrew installed and up to date. After making sure that Homebrew is up to date you're ready to install rbenv! You can see that rbenv also installs [ruby-build](https://github.com/rbenv/ruby-build), a plugin that allows us to install multiple versions of Ruby and enables rbenv to specify which version to use for the current project.
```bash
$ brew update
$ brew install rbenv ruby-build
```

When the above completes, we're ready to install our desired version(s) of Ruby by running:
```
$ rbenv install 2.4.2
```

We'll also need to run the following command to install the shims required for all the Ruby executables that rbenv is aware of. You'll want to run the `rehash` command each time you install a new version of Ruby or a gem that provides commands.
```
$ rbenv rehash
```

After restarting our terminal we should be able to specify which version of Ruby we'd like to run in our project by `cd`-ing into the root folder of the project and running the following command:
```
$ rbenv local 2.4.2
```

You can verify the current active Ruby version by running either of the following commands:
```
$ rbenv version
```

And that's it! We're now able to install and manage multiple versions of Ruby on a per-project basis with minimal fuss.