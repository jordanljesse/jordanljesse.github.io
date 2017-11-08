---
layout: post
title: "Collections in C#"
date: 2017-11-07 11:47:34 -0500
comments: true
categories: .NET C#
published: true
---

When you want to keep track of a group of objects in C#, you can do so by either creating arrays of objects or collections of objects. Collections offer a more flexible way of storing and referencing groups of objects compared to the fixed size and data type of arrays. The following is a brief overview of a few of the collections available in C# and their properties.<!--more-->


### Array
- fixed size
- single datatype
- accessed using square brackets
```csharp
int[] numbers = new int[5];

numbers[0] = 1;
numbers[1] = 2;
numbers[2] = 3;

foreach (int n in numbers)
{
    Console.WriteLine(n); // 1, 2, 3, 0, 0
}
```

### List
- variable size
- single datatype
- provides methods for searching, sorting, and modifying data
```csharp
List<int> numbers = new List<int>();

numbers.Add(100);
numbers.Add(101);
numbers.Insert(0, 99); // add 99 to start of List

foreach (int n in numbers)
{
    Console.WriteLine(n); // 99, 100, 101
}
```

### Queue
- first in first out(FIFO)
```csharp
Queue<int> numbers = new Queue<int>();

numbers.Enqueue(5);
numbers.Enqueue(6);
numbers.Enqueue(7);

while (numbers.Count > 0)
{
    int n = numbers.Dequeue; // removes things from the queue during iteration
    Console.WriteLine(n); // 5, 6, 7
}
```

### Stack
- first in last out(LIFO)
```csharp
Stack<int> numbers = new Stack<int>();
```

### Set
- data structure that does not allow duplicates
```csharp
var numbers = new int[] { 101, 102, 103, 101, 104};

HashSet<int> seen = new HashSet<int>();

foreach (int n in numbers)
{
    if (seen.Add(n)) 
    {
        Console.WriteLine($"{n} is new.");
    }
    else 
    {
        Console.WriteLine($"Already saw {n}.");
    }
}
// 101 is new.
// 102 is new.
// 103 is new.
// Already saw 101.
// 104 is new.
```

### Dictionary
- all about key/value pairs
- organized by key
- not good for searching right to left(looking up names by phone numbers)
```csharp
Dictionary<string, string> phoneNumbers = new Dictionary<string, string>();

phoneNumbers.Add("Dan", "555-310-2345");
phoneNumbers.Add("Joe", "345-234-2340");
phoneNumbers.Add("Johnny", "123-432-9834");

Console.WriteLine(phoneNumbers["Dan"]); // 555-310-2345
Console.WriteLine(phoneNumbers["Steven"]); // throws an exception
```

### ArrayList
- do not use
- lots of extra pointers
- relatively slow
- no specific size
- stores everything as an object
- defeats purpose of strong-typing
- equivalent of a JavaScript array(undesirable in C#)
```csharp
    ArrayList arrList = new ArrayList();
    arrList.Add(100);
    arrList.Add(101);
    arrList.Add("hello");

    int n = arrList[0]; // Cannot implicitly convert type 'object' to 'int'
    int n = (int)arrList[0]; // n = 100
```

### HashTable
- do not use
- legacy
- similar to ArrayList except key/value pairs instead of indexed
```csharp
    Hashtable ht = new Hashtable();

    ht.Add("Dan", "555-234-2478");
    ht.Add("123", "555-234-2478");
```