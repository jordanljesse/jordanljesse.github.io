---
layout: post
title: "Getting Started With Regular Expressions"
date: 2017-11-14 11:02:07 -0500
comments: true
categories: javascript general
published: true
---


Regular expressions, commonly referred to as "regex" or "regexp", are a special kind of text string used for describing a search pattern for string data. Put simply, regular expressions find patterns in strings. Neat huh? This post will cover how to use regular expressions, considerations when using special characters, and character classes.<!--more-->

Regular expressions are both confusing and powerful, and understanding them will definitely aid us in our programming endeavors. The concept of regular expressions originated in 1956 after [Stephen Cole Kleene](https://en.wikipedia.org/wiki/Stephen_Cole_Kleene), an American mathematician, created a formal description of _regular language_ using his own mathematical notation called _regular sets_. Regular expressions are used to power search engines, text editor "find and replace" features, and even [lexical analysis](https://en.wikipedia.org/wiki/Lexical_analysis). However, we're going to focus on regular expressions in the context of programming with JavaScript, and as such we'll be using regular expressions with the string methods `search`, `replace`, `match`, and `split`. Additionally, we're able to use regular expressions with the `test` and `exec` methods built into the `RegExp` object.

### Using Regular Expressions
There are two ways to write regular expressions: as a _regular expression literal_ or by using the `RegExp` object constructor. The simplest regular expression would consist of a single character and find the first occurrence of that character in a string. Both of the regular expressions in the example below contain the same search pattern. 
```javascript
var reg1 = new RegExp("a");     // regex object; compiled at runtime
var reg2 = /a/;                 // regex literal; compiled when script loads

var str = "Jack loves to eat at In-N-Out";

console.log(str.replace(reg1, "")); // "Jck loves to eat at In-N-Out" 
```
Regular expression literals are compiled when the script that invokes them loads, whereas regex objects are compiled at run time. So how do we choose which regex syntax to use? If our regex pattern is going to remain _constant_ then using a regex literal can help improve performance. Conversely, if our regex pattern is going to _change_ or be pulled in from an external source(like user input) then we want to use the `RegExp` object consructor.

### Special Characters
It's worth noting that there are some special considerations when it comes to using certain characters with the regular expression literal syntax. Because the regex pattern ends with a forward slash, any forward slash that we want to be _part of the search pattern_ needs to be escaped with a backslash. Additionally, there are 12 characters that have special meanings in regular expressions and as such they also need to be escaped with a backslash if we want to use them as literals in a regex pattern:

- `?` question mark
- `+` plus sign
- `$` dollar sign
- `*` asterisk
- `/` backslash
- `.` period
- `|` pipe
- `^` caret
- `(` opening parenthesis
- `)` closing parenthesis
- `[` opening square bracket
- `{` opening curly brace

### Character Classes/Sets
A character class(also referred to as a set) is a way to search for a specific character or set of characters out of various combinations of characters within a string. Say we wanted to find both American and British spellings of the word 'grey' using a regex pattern, we could construct our pattern using character classes as follows:
```javascript
function isGrayOrGrey(string){
    var regex1 = /gr[ae]y/;

    return string.match(regex1); // returns array with match as first element
}

isGrayOrGrey("gray");  // ["gray"]
isGrayOrGrey("grey");  // ["grey"]
```
It's worth noting that the order of characters in a character class doesn't matter. Additionally, you can invert/negate a character class by inserting a caret after the opening square bracket, resulting in a regex pattern that finds any character that is _not_ in the character class. In the example below, the function `noZAfterA` returns an array with the matched regex pattern as its first element. The regex pattern `a[^z]` matches the `ap` in `apple` but it does _not_ match `mocha`; this is because there is no character after the 'a' for our pattern to match.
```javascript
function noZAfterA(string){
    var regex = /a[^z]/;
    return string.match(regex);
}
noZAfterA("apple");  // ["ap"]
noZAfterA("azure");  // null
noZAfterA("mocha");  // null
```

### Conclusion
Regular expressions ought to be part of every programmer's toolkit and having a solid understanding of regex patterns and how to use them can empower us to search, filter, and validate(among other things) all manner of string data. In _Intermediate Regular Expressions_ we will dig into more advanced regex patterns that include repeating patterns, shorthand for character classes, and using anchors to mark positions within a string.