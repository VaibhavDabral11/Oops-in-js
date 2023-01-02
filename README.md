# **Oops in Js** 
## constructor in js
```
function Dog() {
   this.name = "Raja";
   this.color ="red";
   this.numLegs = 4 ;
}
let hound = new Dog();
```

* Constructors are defined with a capitalized name to distinguish them from other functions that are not constructors.
* Constructors use the keyword this to set properties of the object they will create. Inside the constructor, this refers to the new object it will create.
* Constructors define properties and behaviors instead of returning a value as other functions might.
Notice that the new operator is used when calling a constructor. This tells JavaScript to create a new instance of Dog called hound. Without the new operator, this inside the constructor would not point to the newly created object, giving unexpected results. Now hound has all the properties defined inside the Bird constructor:

```
blueBird.name;
blueBird.color;
blueBird.numLegs;
```
## Extend Constructors to Receive Arguments

```
function Dog( name , color) {
  this.name = name;
  this.color = color;
  this.numLegs = 4;

}

let terrier = new Dog("gumb", "black" )

```
Here the value of the property passed as a parameter of the constructor dog . Then pass in the values as arguments to define each unique dog into the Dog constructor: ``` let terrier = new Dog("gumb", "black" ) ``` This gives a new instance of Dog with name and color properties set to gumb and black, respectively. The numLegs property is still set to 4. The cardinal has these properties:                           

```
terrier.name
terrier.color
terrier.numLegs
```

## Verify an Object's Constructor with instanceof

Anytime a constructor function creates a new object, that object is said to be an instance of its constructor. JavaScript gives a convenient way to verify this with the instanceof operator. instanceof allows you to compare an object to a constructor, returning true or false based on whether or not that object was created with the constructor. Here's an example:

```
let Bird = function(name, color) {
  this.name = name;
  this.color = color;
  this.numLegs = 2;
}

let crow = new Bird("Alexis", "black");

crow instanceof Bird;
```
This instanceof method would return true.

If an object is created without using a constructor, instanceof will verify that it is not an instance of that constructor:
```
let canary = {
  name: "Mildred",
  color: "Yellow",
  numLegs: 2
};

canary instanceof Bird;
```

This instanceof method would return false.

## Understand Own Properties

```
function Bird(name) {
  this.name = name;
  this.numLegs = 2;
}

let canary = new Bird("Tweety");
let ownProps = [];
// Only change code below this line 
for (let property in canary){
  if(canary.hasOwnProperty(property)) {
    ownProps.push(property);
  }
}
console.log(ownProps)
```
### Output
```
[ 'name', 'numLegs' ]
```
name and numLegs are called own properties, because they are defined directly on the instance object. That means that canary  has its own separate copy of these properties. In fact every instance of Bird will have its own copy of these properties. 

## Use Prototype Properties to Reduce Duplicate Code 
```
function Dog(name) {
  this.name = name;
}

Dog.prototype.numLegs = 4;

// Only change code above this line
let beagle = new Dog("Snoopy");

```
This may not be an issue when there are only two instances, but imagine if there are millions of instances. That would be a lot of duplicated variables.

## Iterate Over All Properties
```
function Dog(name) {
  this.name = name;
}

Dog.prototype.numLegs = 4;

let beagle = new Dog("Snoopy");

let ownProps = [];
let prototypeProps = [];

// Only change code below this line
for (let property in beagle) {
  if(beagle.hasOwnProperty(property)) {
    ownProps.push(property);
  } else {
    prototypeProps.push(property);
  }
}

console.log(ownProps);
console.log(prototypeProps);

```
### Output:

```
[ 'name' ]
[ 'numLegs' ]
```
## 
