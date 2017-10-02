---
layout: post
title: "Backup Strategy"
date: 2017-09-30 22:18:25 -0500
comments: true
categories: general productivity
published: true
---

If you're like me, then you probably store a lot of precious data on your digital devices: family photos, videos, music, fun projects, work projects, notes, and the like. When(it's *definitely* when, not if) we experience a device failure/loss, the last thing we want to worry about is whether the data we've accumuated over the years, our digital life, is safe or not. Here is the backup strategy I use to make sure that when a computer fails it's a minor inconvenience instead of a major headache(or heartache).
<!-- more -->

### The 3-2-1 Rule
There is a rule for reliable digital backups called [*The 3-2-1 Rule*](http://#) and it goes like this: for our data to be properly backed up it needs to exist in *three* places, on *two* seperate mediums, and with at least *one* backup offsite. So if we have a copy of our data on our laptop, an external hard drive, and in the cloud we can be pretty confident that our data is safe. Let's dig into the tools to get this done!

### Local Versioned Backups
The first, and perhaps easiest to implement, backup we should make is a local versioned backup of our data. The _"local"_ in local versioned backup means that the data exists locally, physically near us, and not offsite on some remote server or cloud service(Dropbox, iCloud, etc.). The _"versioned"_ part means that our data is backed up incrementally and different versions of our data are maintained. A good use case for this would be if we have a project we're working on and the files get corrupted, or we make a change that we're not happy with and want to restore the project to an earlier version. With local versioned backups, we can do this!

One of the easiest ways to maintain local versioned backups of our data on a Mac is to use Apple's own [Time Machine](http://#) software, which is included with every Mac. We open up `System Preferences`, select `Time Machine`, check the box labeled `Back Up Automatically`, and click on `Select Disk` to choose which disk we would like to use with Time Machine. It's important to note that the disk we choose should _NOT_ be our Mac's startup disk - it should be a seperate disk. This is so that if our Mac were to fail or get lost our local versioned backup would remain intact, keeping our data safe. It's worth mentioning that Time Machine only backs up our *data*(photos, videos, music, notes, etc.), _not_ our applications or settings, which is where our second backup comes in.

### Local Bootable Backups
A local bootable backup is like the previous backup, except with two major differences: it backs up our *entire* hard drive including data, apps, and settings, and we can use it to boot up our computer. The _"bootable"_ in local bootable backup means that we can take the drive that contains our backup, plug it into another computer, and boot from it. It is a clone of our system in its entirety. One of the shortcomings of this type of backup is that if we make a change to a project that we don't like or a file gets messed up, those changes will get backed up to the local bootable backup as well. That is exactly why we keep a versioned backup *in addition to* a bootable backup. 

For a bootable backup I use and highly recommend the application [*Carbon Copy Cloner*](http://#) by Bombich Software. After installing Carbon Copy Cloner, we select which disk we would like the application to use as a backup(again, one that is *seperate* from our startup disk), the schedule for our backup(I recommend daily), and click on the `clone` button.

### Offsite Backups
An offsite backup of our data is data that is literally *offsite* - it is located far away from our devices and backup drives. This is typically used as a worst case scenario backup, like if our house were subject to flood, fire, or theft. It would be nice to know that if we were unfortunate enough to lose everything that all of our data would be safe somewhere, and with an offsite backup this is possible.

For most poeple, one of the easiest ways to maintain an offsite backup is to use a service who's mission is to keep our data backed up safely. Services like [Backblaze](http://#) can back up our entire computer to their servers(the cloud) and restore those files at our request.

For the more technically inclined, I use and recommend [Arq](http://#) configured to back up our data to AWS Glacier servers, which have relatively low storage fees. Arq is essentially Time Machine for the cloud - it creates versioned backups of our data stored on Amazon's servers. As long as we have an internet connection our files are constantly being backed up to the cloud. However, unlike local backups, we will need to be connected to the internet to restore our files.