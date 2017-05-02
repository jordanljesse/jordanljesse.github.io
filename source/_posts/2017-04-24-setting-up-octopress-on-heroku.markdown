---
layout: post
title: "setting up octopress on github pages"
date: 2017-04-24 23:37:21 -0500
comments: true
categories: blogging, octopress
published: false
---

Recently I decided that Wordpress is too bloated for my blogging needs and decided to install Octopress instead. Here is a short guide on how to get started blogging with Octopress, both to help guide you and to help me remember how I got here ;-)
### Initial Setup
1. fork a copy of Octopress to your own github account
2. clone your forked repo of Octopress to your new blog folder `clone git@github.com:jordanljesse/octopress.git my-cool-new-blog`
3. run `gem install bundler`
4. run `bundle install` to install all of the dependencies for Octopress
5. if you get an SSL error after running `bundle install`, simply `vim Gemfile` to open up the Gemfile in the vim editor and remove the "s" from "https" on the first line
6. running `rake install` will install the default Octopress theme
7. run `rake setup_github_pages` to configure Octopress to push your blog to Github Pages
8. 