# JavaScript Objects

| Learning Objectives |
| :--- |
| Create JavaScript Objects |
| Use JS Objects to Model Real World Objects |

## Roadmap

1. Intro to Objects
2. Creating Objects in JavaScript
3. Designing Objects
4. Lab
5. After Hours

### 1. Intro to Objects

#### Object Oriented Programming (OOP)

As web developers, we practice Object Oriented Programming techniques.

With OOP, our programs are crafted from objects, which have data and behavior, and are used to model real world objects.  During the program's execution, these objects interact with each other to accomplish the programming goal.

Virtually all OOP languages use what's known as a class-based approach where new objects are created from _classes_ that are used to construct new objects. JavaScript is the only OOP language in wide use that uses a prototype-based style of OOP where new objects are based upon the _prototype_ of other objects, not a class. 

#### JavaScript Objects

_>_

JavaScript objects contain a collection of zero or more unordered _properties_.

_Properties_ consist of a __key__ (sometimes also referred to as _name_) and a __value__. Together these are called __key:value__ pairs. Within the JS object, the _key_ and _value_ are separated by a colon, and the properties themselves separated by a comma.

The _value_ of a property can be of any type, including other the primitive types, arrays, objects and even functions.

When a property's value is a function, that particular property is often referred to as a _method_.

The properties holding data, are often referred to as _attributes_. 

_methods_ and _attributes_ are both _properties_.

Objects in JavaScript are dynamic - their properties can be changed, added & removed during runtime.

### 2. Creating Objects in JavaScript

Today, we're going to look at the two most common ways to create objects in JavaScript.

#### Object Literal Syntax

When we need to create a one-off object that does not need to be based upon another object, we often create that object using an _object literal_:

```javascript
var house = {
	bedrooms: 4,
	baths: 3,
	color: 'purple'
};
```

__Observations / Questions?__

#### Accessing Properties

Before continuing on to the second method to create objects, we are going to take a look at how to access the values of an object's properties.

Lets check out the object above, however, instead of using console as we did in the previous lesson, lets use one of the "code playground" called [JSBin](http://jsbin.com/?js,console).

After copying and pasting in our _house_ object, click the [Run] button to execute the code. Now we can click in JSBin's console window and access our _house_ object.

Lets access the _baths_ property using _dot notation_:

```javascript
house.baths;
```

The number `3` should have printed out.

To access the same property using _bracket notation_, type:

```javascript
house['baths'];
```

So, there's two methods of accessing the properties of an object.<br>__Which of the two notations should we use?__

Well, _dot notation_ is more performant and the preferred method because it is more clear and concise.

However, there is a distinct advantage _bracket notation_ has that can come in handy. __Does anyone know what it is?__

<br>
<br>

The advantage is that you can __dynamically__ access properties at runtime using a string variable that contains the name of the property you want to access and use that inside the brackets:

```javascript
var prop = 'baths';
console.log(house[prop]); // 3
```

__Practice: Create an object that represents a concert ticket using _object literal_ syntax__

#### Creating Objects with a Constructor Function

You've seen how to create objects using object literals.  However, often your program will need to create tens, hundreds, or even more of the same type of object. _Constructor Functions_ to the rescue! 

In essence, constructor functions are like factories - factories designed to produce multiple instances of the same type of object.  A constructor function for our _house_ object would look like this:

```javascript
function House(numBaths, numBedrooms, color) {
	this.baths = numBaths;
	this.bedrooms = numBedrooms;
	this.color = color;
}

var house = new House(3, 4, 'purple');
```

__What observations can you make about this code?__ (other than the fact that purple might not be the best choice for the color of a house)

<br>
<br>

- The identifier of the constructor function is capitalized, more specifically, _Upper Camel Case_.
- Other than the way we name and use them, constructor functions are just functions.
- Our parameter names don't have to match the names of our properties.  Those argument placeholders, aka parameters, become local variables inside of the function.
- The `this` keyword represents our newly created object that JS passes automatically passes into the function for us.  The JS engine knows to do this when we call a function with the `new` keyword in front of it.
- No `return` is necessary - the new object, that we added properties to, is automatically returned.

__Practice: Create a constructor function that creates _concert ticket_ objects that that you created earlier using object literal syntax__

#### Discovering an Object's Properties

There may come a time that our program needs to know what properties exist on an object.

JavaScript has a built-in object called `Object`. `Object` serves as the default constructor function for creating new objects, but it also has several helper methods attached to it. One of them is the `keys()` method.

Using the `Object.keys()` method is one of the ways we can discover the names of the properties of an object.  It accepts a single argument, an object, and will return that object's property names in an array.

__Pair up and write JavaScript in JSBin to do the following:__

- Create a _person_ object with an object literal, giving it a _name_, _age_, _isCool_ attributes, and a _sayHello_ method.
- Loop through the _person_ object's properties and `console.log` the properties _key_ and _value_.

  Hint: What was the method we learned used in the previous lesson to iterate over an array's elements?

### 3. Designing Objects

Object Oriented Programming allows developers to represent the problem being solved by coding objects that model real world objects that interact with each other.

Using OOP makes our code easier to understand, less brittle, and more maintainable. It also allows us to more easily reuse code.

One of the key principles of OOP, known as _encapsulation_, is that an object should only contain data and behavior related to that particular type of object. For example, you would never have a _color_ property or a _honk_ method in an object that represents a bank account, would you?

Another pillar of OOP is known as _composition_. This concept refers to adding functionality to an object by having it contain other objects.  For example, our House object could have an `address` property with a value set to an Address object.

#### Lets redesign our House object

Let's make our _house_ object a little more "real world" by:

1. Removing the `color` property.
2. Adding a `sold` property that defaults to a value of `false`.
3. Adding a `sell` method that will set the `sold` property to true and `console.log` out the message "I've been sold!"

##### Step 1

This one's easy!  Simply remove the `color` property so that our constructor now looks like this:

```javascript
function House(numBaths, numBedrooms) {
	this.baths = numBaths;
	this.bedrooms = numBedrooms;
}
```
Don't forget to remove `color` from the parameter list.

##### Step 2

Lets add our `sold` property. However, we don't want to add it to our parameter list because we always want it to default to `false`.

```javascript
function House(numBaths, numBedrooms) {
	this.baths = numBaths;
	this.bedrooms = numBedrooms;
	this.sold = false;
}
```

##### Step 3

You're about to create you first method in an object!  Lets do this!

```javascript
function House(numBaths, numBedrooms) {
	this.baths = numBaths;
	this.bedrooms = numBedrooms;
	this.sold = false;
}

House.prototype.sell = function() {
	this.sold = true;
};
```

What's this `prototype` thingy? You will learn more about them soon enough. For now, just know that every object, including  functions, have a `prototype` property that is itself an object. And because it's an object, we can dynamically add properties to it - in this case, a method.

__Why not just assign the function to a property inside of the constructor function?__

<br>
<br>


If we put the function inside each object, it would work, however, there would be a copy of the `sell` function with every object - not too efficient. By putting the method on the prototype object, we will only have one copy of the `sell` function in memory, regardless of how many houses we create!

Lastly, note that the `this` keyword in this context refers to the instance of the object itself.

__Create an instance of a House in JSBin, check its properties, and call its `sell` method. Be sure to re-check the value of the `sold` property after invoking the `sell` method.__

Sweet!

### 3. Lab

Pair up with a code partner and...

Add an `address` property to our House constructor, that is itself an object with `street`, `city`, `state` and `zip` properties.

Then create a new _House_, passing in an object literal for the _address_ argument.

This works, but since an _address_ is something that are likely to create multiple instances of, lets create of an Address constructor.  

Then, use the constructor function to instantiate an _address_ object and pass it in as the _addrress_ argument to the House constructor.

### 4. Homework / After Hours

Design and create a `Car` constructor function for a car object that:

- Has a `make` property
- Has a `model` property
- Has a `year` property
- Has a `color` property
- Has a `mileage` property
- Has a `honk` method that `console.logs` "Beep, beep!".
- Has a `drive` method that will accept an argument of the number of miles to add to the `mileage`. Ensure that the argument is not negative - it's illegal to roll back odometers!

Create several car objects passing in different values as arguments, call their methods and examine their properties.












