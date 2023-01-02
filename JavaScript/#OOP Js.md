### Objects is Js:
1. They are used as that of real world objects giving them properties and behavior like real life ex : 
```js
let duck = {
  name: "Aflac",
  numLegs: 2
};
```
2. to call the object we use dot notation like :
 ```js
console.log(duck.name);
```
3. We Can make Function in object and it's called _Method_ ex:
```js
let duck = {
  name: "Aflac",
  numLegs: 2,
  sayName: function() {return "The name of this duck is " + duck.name + ".";}
};
duck.sayName();
```
4. we use __this__ so that we don't need to change the object name every where and make it more reusable ex:
```js
let duck = {
  name: "Aflac",
  numLegs: 2,
  sayName: function() {return "The name of this duck is " + this.name + ".";}
};
```
5. creating constructor for Js (like BluePrints )& starts with Capital ex:
```js
function Bird() {
// it uses This to set properties of variables.
  this.name = "Albert";
  this.color = "blue";
  this.numLegs = 2;
}
```
6. To Create object from constructor we do as follow: 
 ```js
 // all the object's items will have the same properties
let blueBird = new Bird();
```
7. we can make constructor with parameters  as follows:
```js
function Bird(name, color) {
  this.name = name;
  this.color = color;
  this.numLegs = 2;
}
//so we can put object easily like this:
let Birdod = new Bird("hamada","azr2");
```
8. Using **instanceof** to know the type of object: 
```js
let crow = new Bird("Alexis", "black");

crow instanceof Bird; //it will return true.
```
9.WE can loop and get all the owned properties by hasOwnProperty() ex:
```js
let ownProps = [];

for (let property in duck) {
  if(duck.hasOwnProperty(property)) {
    ownProps.push(property);
  }
}
console.log(ownProps);
/* Will return name , numLegs*/
```
10.  Use Prototype Properties to Reduce Duplicate Code as follow:
```js
Bird.prototype.numLegs = 2;
```
11. to iterate on all properties of prototype and of constructor :
```js
let ownProps = [];
let prototypeProps = [];

for (let property in duck) {
  if(duck.hasOwnProperty(property)) {
    ownProps.push(property);
  } else {
    prototypeProps.push(property);
  }
}
console.log(ownProps); //name
console.log(prototypeProps); //numlegs.
```
---
#### Constructor property: 
1. we can use (object.constructor === object) to know which instance of is it.
2. WE can add functions and properties to the constructor at the same time : 
```js
Bird.prototype = {
  numLegs: 2, 
  eat: function() {
    console.log("nom nom nom");
  },
  describe: function() {
    console.log("My name is " + this.name);
  }
};
```
3. When Making the prototype the constructor property will not be the same as it will return false bec that overwrite it so to make it back to normal we do as follows:
```js
Bird.prototype = {
//type this:
  constructor: Bird,
  numLegs: 2,
  eat: function() {
    console.log("nom nom nom");
  },
  describe: function() {
    console.log("My name is " + this.name); 
  }
};
```
####  while The instanceof will be working perfectly without any wrong thing.
---
#### Prototyping: 
- all objects in js have a prototype and also the prototype itself is an object.
- .prototype.IsPrototypeOf() : shows if the object is from the constructor ex:
```js
Bird.prototype.isPrototypeOf(duck); // return true.
```
- The Prototype Father is called : Object so Bird and duck are Sub types for Object and they are like sons and grand sons ex: 
```js
Object.prototype.isPrototypeOf(Bird.prototype);
// return true.
```
---
#### Inheritance why do we do it?
##### 1. DRY (Don't Repeat yourself).
##### 2. To Make it easier to find code and decrease error.
- we do it as follows :
1. Make New Constructor with the parent class like animal to cat and dog
2. do the function in it ex:
	```js
	function Animal() { };
	
	Animal.prototype = {
	  constructor: Animal, 
	  describe: function() {
	console.log("My name is " + this.name);
	  }
	};
	```
3. And in this animal is called **SuperType**.
##### 3. how do we Inherit this function?
	1.we do object of the supertype as follows :
```js
let animal = Object.create(Animal.prototype);
```
	2. we use Object.Create to : 
		1. To get away from disadvantages of new and how complex it is.
		2. we are making it more like Prototype not normal object have same Recipes.
	3. TO Inherit it we use :
```js
ChildObject.prototype = Object.create(ParentObject.prototype);
```
4. When inheriting Like we said all the Animal constructor properties are inherited and this cause that if you didn't give the subtype it's constructor it will also be the same of the supertype so we use this:
```js
//To give it constructor detail manually.
Bird.prototype.constructor = Bird;
duck.constructor
```
5. We can even give the Subtypes it's own unique functions by giving them in their Prototype ex : 
```js
ChildObject.prototype.methodName = function() {...};
```
#### Overridings : 
1. we override it as follows :
```js
function Animal() { }
Animal.prototype.eat = function() {
  return "nom nom nom";
};
function Bird() { }

Bird.prototype = Object.create(Animal.prototype);

Bird.prototype.eat = function() {
  return "peck peck peck";
};
```
2. __How does Js Works in Overriding ?__ 
	1.  `duck` => Is `eat()` defined here? No.
	2.  `Bird` => Is `eat()` defined here? => Yes. Execute it and stop searching.
	3.  `Animal` => `eat()` is also defined, but JavaScript stopped searching before reaching this level.
	4.  Object => JavaScript stopped searching before reaching this level.
3. When the Childs are not related and we want to share method we Use Object Mixin as follows : 
```js
let flyMixin = function(obj) {
  obj.fly = function() {
    console.log("Flying, wooosh!");
  }
};

let bird = {
  name: "Donald",
  numLegs: 2
};

let plane = {
  model: "777",
  numPassengers: 524
};
// this will add the .fly func to both bird and plane.
flyMixin(bird);
flyMixin(plane);
```
---
#### Change the variable Privacy : 
1. We use closure to Make the variable from public to private as follows : 
```js
function Bird() {
  let hatchedEgg = 10;

  this.getHatchedEggCount = function() { 
    return hatchedEgg;
  };
}
let ducky = new Bird();
ducky.getHatchedEggCount();
```
2. from what u see in example when we make variable(not using this.) and put value to it it becomes private.
---
#### IIFE => Immediately invoked function expression to make it we do as follows :
```js
(function () {
  console.log("Chirp, chirp!");
})();
```
#### WE can use IIFE in Modules (packages) as follows :
1. we make the IIFE func return the two functions or how many functions 
```js
let motionModule = (function () {
  return {
    glideMixin: function(obj) {
      obj.glide = function() {
        console.log("Gliding on the water");
      };
    },
    flyMixin: function(obj) {
      obj.fly = function() {
        console.log("Flying, wooosh!");
      };
    }
  }
})();
```
2. if we want to call the function or add it to a constructor we have we do :
```js
motionModule.glideMixin(duck);
duck.glide();
```
___
