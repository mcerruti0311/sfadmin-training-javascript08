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

### Breaking Down OOP
Think of an Object as a macro enabled spreadsheet.  Where the object is the
spreadsheet, and methods are the macros.  The properties of an object are
equal to the fields.  Each instance is a record. A template would be like a form
used to enter data.

### Object Creation
#### Declare a direct instance of an object
``` JavaScript
myNewObject = new Object();
```
Now add a property to the myNewObject

``` JavaScript
myNewObject.info = 'I am a shiny new object';
```

Now define an function and attach it to `myNewObject` as one of the object's
methods.

``` JavaScript
function myFunc() {
    alert(this.info);
};
myNewObject.showInfo = myFunc;
```

To call the new method, you simply use the now familiar dot notation:

`myNewObject.showInfo();`

### Using the this keyword
Note the use of the this keyword in the previous function definition.

When you use `this` inside a function (or method), the keyword `this` refers to
the function’s parent object.

Upon the first declaration of the function myFunc(), its parent is the global
object; that is, the window object. The window object does not have a property
called info, so if you were to call the myFunc() function directly, an error
would occur.

However, you go on to create a method called showInfo of myNewObject and you
assign myFunc() to that method:

myNewObject.showInfo = myFunc;

In the context of the showInfo() method, myNewObject is the parent object, so this.info refers to the property myNewObject.info.

### Anonymous Functions
There is a more convenient and elegant way to assign a value to your object’s showInfo method, without having to create a separate, named function and then later assign it by name to the required method. Instead of this code:
``` JavaScript
function myFunc() {
        alert(this.info);
    };
myNewObject.showInfo = myFunc;

you could simply have written the following:

myNewObject.showInfo = function() {
    alert(this.info);
}
```
Because you haven’t needed to give a name to your function prior to assigning it, this technique is referred to as using an anonymous function.

By using similar assignment statements you can add as many properties and methods as you need to your instantiated object.

** Tip **

```
JavaScript offers a further way to create a direct instance of an object; the
technique uses JSON (JavaScript Object Notation). It isn’t covered here, as we
explore JSON in detail in Hour 10, “Meet JSON.”
```

### Using a Constructor Function
Directly creating an instance of an object is fine if you think you’ll only need one object of that type. Unfortunately, if you need to create another instance of the same type of object, you’ll have to go through the same process again—creating the object, adding properties, defining methods, and so on.

** Tip **
```
An object with only one global instance is sometimes called a singleton object.
These objects are useful sometimes; for example, a user of your program might have only one associated userProfile object, perhaps containing his or her user name, URL of last page viewed, and similar properties.
```
A better way to create objects that will have multiple instances is by using an object constructor function. An object constructor function creates a kind of “template” from which further objects can be instantiated.

Take a look at the following code. Instead of using `new Object()`, you first declare a function, `myObjectType()`, and in its definition you can add properties and methods using the this keyword.

``` JavaScript
function myObjectType(){
    this.info = 'I am a shiny new object';
    this.showInfo = function(){
        alert(this.info);  // show the value of the property info
    }
     this.setInfo = function (newInfo) {
        this.info = newInfo; // overwrite the value of the property info
    }
}
```
In the preceding code you added a single property, `info`, and two methods: `showInfo`, which simply displays the value currently stored in the `info` property, and `setInfo`. The `setInfo` method takes an argument, `newInfo`, and uses its value to overwrite the value of the info property.

### Instantiating an Object
You can now create as many instances as you want of this object type. All will have the properties and methods defined in the `myObjectType()` function. Creating an object instance is known as instantiating an object.

Having defined your constructor function, you can create an instance of your object simply by using the constructor function:

`var myNewObject = new myObjectType();`

** Note **
```
Note that this syntax is identical to using new Object(), except you use your purpose-designed object type in place of JavaScript’s general-purpose Object(). In doing so, you instantiate the object complete with the properties and methods defined in the constructor function.
```
Now you can call its methods and examine its properties:
``` JavaScript
var x = myNewObject.info // x now contains 'I am a shiny new object'
myNewObject.showInfo();  // alerts 'I am a shiny new object'
myNewObject.setInfo("Here is some new information");  // overwrites the info
property
```
Creating multiple instances is as simple as calling the constructor function as many times as you need to:

`var myNewObject1 = new myObjectType();`
`var myNewObject2 = new myObjectType();`

### Using Constructor Function Arguments
There is nothing to stop you from customizing your objects at the time of
instantiation, by passing one or more arguments to the constructor function.
In the following code, the definition of the constructor function includes one
argument, `personName`, which is assigned to the `name` property by the
constructor function. As you instantiate two objects, you pass a name as an
argument to the constructor function for each instance.

``` JavaScript
function Person(personName){
    this.name = personName;
    this.info = 'I am called ' + this.name;
    this.showInfo = function(){
        alert(this.info);
    }
}
var person1 = new Person('Adam');
var person2 = new Person('Eve');
```
### Extending and Inheriting Objects Using prototype
A major advantage of using objects is the capability to reuse already written
code in a new context. JavaScript provides a means to modify objects to include
new methods and/or properties or even to create brand-new objects based on ones
that already exist.

These techniques are known, respectively, as extending and inheriting objects.

#### Extending Objects
What if you want to extend your objects with new methods and properties after
the objects have already been instantiated? You can do so using the keyword
prototype. The `prototype` object allows you to quickly add a property or
method that is then available for all instances of the object.

** Tip **

You can define the constructor function to accept as many or as few arguments
as you want:

``` JavaScript
function Car(Color, Year, Make, Miles) {
    this.color = Color;
    this.year = Year;
    this.make = Make;
    this.odometerReading = Miles;
    this.setOdometer = function(newMiles) {
         this.odometerReading = newMiles;
    }
var car1 = new Car("blue", "1998", "Ford", 79500);
var car2 = new Car("yellow", "2004", "Nissan", 56350);
car1.setOdometer(82450);
```


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
