---
layout: post
title: "Indexed DB"
date: 2017-12-04 09:58:12 -0500
comments: true
categories: www general
published: false
---


- IndexedDB(IDB) is a database that is accessible using JavaScript and allows developers to store large amounts of data on the client(instead of the server).
- Benefits of using IDB instead of remote storage include network resilience(apps working even when the internet is flaky) and privacy(user's data isn't leaving their machine and being stored on somebody else's server).
- IDB is avaialbe in all major browsers including Chrome, Firefox, Safari, Opera, and Edge(even IE 10 & 11, with limitations of course).
- persistent data is store in the browser and associated with the browsing profile
- IDB vs relational database: IDB stores objects in an ObjectStore; relational database stores rows in a table
- IDB is NOT a relational database
- IDB is asynchronous and relies on transactions to maintain the integrity of data
- debugging support for IDB is available in Chrome, Firefox, Safari, and Opera, however it is *not* available in Edge(yet)
- enables web application to be accessible offline(yey!)
