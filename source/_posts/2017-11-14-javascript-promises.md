---
layout: post
title: "JavaScript Promises"
date: 2017-11-14 23:46:52 -0500
comments: true
categories: school
published: false
---


What is a promise? Why would we want to use promises in JavaScript? Promises are a relatively new addition to JavaScript and were included in [ECMAscript6](http://es6-features.org/#Constants). Let's dig into promises!<!--more-->

# What is a promise?
Let's answer that first question: what is a promise? A promise is simply the result of an asynchronous operation - it is an object that may produce a single value some time in the future. That value could be one of two things: either the result of our completed asynchronous operation or the reason why the operation failed. Additionally, a promise has only three states: pending, fulfilled, and rejected.

###### Promise States
- pending: neither fulfilled or rejected
- fulfilled
- rejected

While a promise is 'pending' it may resolve to either of the other two states, however once a promise has resolved its state is fixed and will not change. A promise that is not pending is called *settled*, and a settled promise is immutable.  

It's worth noting that promises can use callback functions to handle a fulfilled value or reason for being rejected(and commonly do). This is accomplished by using the `.then()` method, which happens to be the primary API for promises.