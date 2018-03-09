# sfadmin-training-javascript08
## Object-Oriented Programming
As your programs become more complex, you need to use coding techniques that
help you to maintain control and ensure that your code remains efficient,
readable, and maintainable. In this hour you learn the basics of object-oriented
programming (OOP), an important technique for writing clear and reliable code
that you can reuse over and over.

## What You'll Learn in This Hour:
* What object-oriented programming is
* Two ways to create objects
* Instantiating an object
* Extending and inheriting objects using prototype
* Accessing object methods and properties
* Using feature detection

## Summary
In this hour you learned about object-oriented programming (OOP) in JavaScript,
starting with the basic concepts behind OOP, and how it can help your code
development, especially for more complex applications.

You learned a way to directly instantiate an object and add properties and
methods to it. You then learned to create an object constructor function, from
which you can instantiate multiple similar objects.

You also learned about the prototype keyword, and how it can be used to extend
objects or create new objects via inheritance.

## Q&A

**Q. Should I always write object-oriented code?**

A. It’s a matter of personal preference. Some coders prefer to always think in
terms of objects, methods, and properties, and write all their code with those
principles in mind. Others feel that, particularly for smaller and simpler
programs, the level of abstraction provided by OOP is too much, and that
procedural coding is OK.

**Q. How would I use my objects in other programs?**

A. An object’s constructor function is quite a portable entity. If you link into
your page a JavaScript file containing an object constructor function, you have
the means to create objects and use their properties and methods throughout
your code.

## Exercises

1. Write a constructor function for a Card object with properties of suit
(diamonds, hearts, spades, or clubs) and face (ace, 2, 3 ...king). Add methods
to set the values of suit and face.
Can you include a shuffle method to set the suit and face properties to
represent a random card from the deck? (Hint: Use the Math.random() method
described in Hour 4, “DOM Objects and Built-in Objects.”)

2. Extend JavaScript’s Date object using the prototype keyword to add a new
method, getYesterday(), that returns the name of the previous day to that
represented by the Date object.
