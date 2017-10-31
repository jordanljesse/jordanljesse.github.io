---
layout: post
title: "Dirty Checking vs. VDOM"
date: 2017-10-31 14:50:12 -0500
comments: true
categories: www general
published: true
---


What is the difference between updating the DOM using dirty checking and VDOM manipulation? Is one more efficient than the other? What the heck *is* the DOM? Let's try to answer these questions!<!--more-->

### What is the DOM?
To understand the differences between dirty checking and VDOM manipulation we first need to understand what the DOM is and isn't.

##### The DOM is:
- a programming interface for HTML and XML documents
- an object-oriented representation of the HTML we wrote made up of nodes and objects
- automatically created from the HTML we wrote by the browser

##### The DOM is not:
- the actual HTML we wrote
- the markup we see when we choose 'view source' on a page
- always the same as our HTML(browsers sometimes fix invalid markup behind the scenes)

The DOM can be manipulated and edited using a scripting language like JavaScript including libraries and frameworks such as jQuery, Angular, and React. In fact, the DOM actually has its own API for interacting with other bits of code. Much of what is thought of as a "JavaScript thing" is actually a DOM API feature that allows us to interact with the DOM.

### Dirty Checking
Dirty checking is when our code checks all of the node's data at regular intervals for changes, like a loop(because it *is* a loop). It's an inefficient way to update DOM elements as it requires recursively traversing every single node in the DOM to see if the node's data is "dirty"(it's been changed). Compared to "Observable Checking", where the individual components are responsible for listening to when changes take place in the state and communicating those changes, dirty checking is slow. A good example of this slowness would be updating a `li` in an unordered list: when dirty checking discovers the updated `li` it will actually re-render the entire unordered list; a very ineffecient operation.

### The Virtual DOM
The virtual DOM, or VDOM, is an abstraction of the DOM that is lightweight and can be updated without affecting the actual DOM. It has all of the same nodes, objects, and properties as the real DOM except without the ability to write to the screen. It's worth noting that a new VDOM is created after every re-render of the UI. When using React a snapshot is made of the VDOM before applying any updates and this snapshot is used to compare against an updated VDOM. By comparing and contrasting the VDOM snapshot with the updated VDOM React is able to update only those elements that have been changed. Unlike the dirty checking example previously mentioned, VDOM manipulation will only update the node that's been changed *without* having to update it's parent element or containing list. This is what makes VDOM manipulation faster and more efficient than dirty checking.
