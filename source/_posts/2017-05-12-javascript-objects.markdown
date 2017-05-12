---
layout: post
title: "intro to javascript objects"
date: 2017-05-12 10:10:43 -0500
comments: true
categories: javascript
published: true
---
To understand how functions and other objects work in Javascript it's important to first understand objects. What makes an object, how are they used, and what can we do with them? Let's tackle a few of these questions!
<!-- more -->

### Objects
Almost everything in Javascript is an object as the language is an object-based programming language(compared to an object-*oriented* language an object-*based* language lacks inheritance and subtyping). The first important takeaway is that an object is a collection of *properties* and that properties themselves are key/value pairs. When a property's value is a function, that property is then referred to as a *method* and can be used by(or "called on") the object that it is attached to. Additionally, while there are many predefined objects in the browser you can also create your own objects, complete with unique properties and methods. But how do we use these properties and methods?

### Properties & Methods
Objects and their properties/methods can be accessed by using *dot notation*. It's also important to note that object names and property names are case-sensitive in Javascript.  
```javascript
objectName.propertyName;
```

Additionally, properties can be accessed by the use of *bracket notation*, which yields the same results as the line of code above.  
```javascript
objectName['propertyName'];
```

In Javascript, any valid string can be used as a property name - even an empty string - however if a property name is not considered a valid identifier(such as a string that contains a space, hyphen, or begins with a number) it can only be accessed using bracket notation. Bracket notation is also useful for passing in dynamically generated property names and property names that are not determined until the program is run. Properties can also be referenced by using strings stored in variables:  
```javascript
var propertyName = "make";
myCar[propertyName] = "Chevy";

propertyName = "model";
myCar[propertyName] = "Impala";
```

When it comes to methods, calling them is similar to calling properties, except that methods contain a pair of parentheses at the end for accepting arguments(much like a function because it *is* a function). It looks like this:  
```javascript
objectName.methodName(argument);
```

To pull it all together, here is what it looks like to create a new object with a method that accepts an argument and what happens when the method is called:  
```javascript
var dog = new Object();
dog.speak = function(ownerName) {
    return "Woof! Good morning" + ownerName + "!";
}

dog.speak("Dave");  // prints "Woof! Good morning Dave!"
```

### Wrap up
 I highly recommend giving this [excellent article](http://eloquentjavascript.net/06_object.html) a read if you want a more thorough(and entertaining!) history of objects. Also, I would be remiss if I didn't remind you that I myself am still learning this stuff and while I do my best to pick up best practices and incorporate them into my thinking, this post will probably be revised as I better organize my understanding of objects. All that to say, read this with an open mind and a grain of salt ;-)

##### Sources
- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Working_with_Objects
- https://en.wikipedia.org/wiki/Object-based_language
- https://en.wikipedia.org/wiki/Object-oriented_programming