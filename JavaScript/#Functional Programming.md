#### First what is Functional Programming ?
It is A way of programming like OOP but it only __Depends__ On Functions 
`INPUT -> PROCESS -> OUTPUT`
It is using 3 things : 
1. Isolated Functions : Nothing depend on other.
2. Pure Functions : The samy input always the same output.
3. Functions Limited side effect : any changes to the state of the program outside function are carefully controlled.
---
#### Second Some terminologies :
1. Callbacks : are the functions that are passed to another one Example: filter()=> the call back function tell us how to filter array.
2. First class functions: all the functions that can be passed to variable that can be call back functions or that returned from another functions.
3. All Js Functions are **First class Functions**.
4. Higher order functions : functions that takes functions as arguments or return functions as return value.
5. lambda functions =>are functions  passed in to or returned from another function.
---
#### Imperative programming :
**it is Giving the pc some statments to perform a task**.
- Often the statements change the state of the program, like updating global variables. A classic example is writing a `for` loop that gives exact directions to iterate over the indices of an array.
---
- Splice Changes in the data of array even if it's in a function , while slice doesn't so we use slice more in Functional programming.
- What splice does called mutation and the outcome of it is called side effect.
- in functional programming like we said it should be Pure functions with no side effects.
- if we don't have a global variable we can use arguments to make it easier for us to change and alternate it without side effects.
---
### Map Method : 
It is used to iterate on array items and returning new array contains the resulting of the callback function ex: 
```js
const users = [
  { name: 'John', age: 34 },
  { name: 'Amy', age: 20 },
  { name: 'camperCat', age: 10 }
];

const names = users.map(user => user.name);
console.log(names);
```
map implementations : 
``` js
Array.prototype.myMap = function(callback) {
  const newArray = [];
  // Only change code below this line
  for(let i=0;i<this.length;i++)
  {
    newArray.push(callback(this[i],i,this));
  }
// Only change code above this line
  return newArray;
};
```
---
#### .filter():
 - calls a function on each element of an array and returns a new array containing only the elements for which that function returns a truthy value.
 - .filter Implementation :
 ```js
 Array.prototype.myFilter = function(callback) {
  const newArray = [];
  // Only change code below this line
  for(let i=0;i<this.length;i++){
    if(callback(this[i],i,this))
    {
      newArray.push(this[i]);
    }
  }
  console.log(newArray);
  // Only change code above this line
  return newArray;
};
```
---
#### .slice():
1. Slice method returns copy of certain or all elements of the array: 
	it's arguments : 1. index of begin 
	2. the index that it will end in (it's not inclusive).
ex:
```js
const arr = ["Cat", "Dog", "Tiger", "Zebra"];
const newArray = arr.slice(1, 3);
```
2. when trying to remove somethin from array use Slice not Splice as splice mutate the array while slice doesn't.
---
#### .Concat():
- Concat joins items end to end (non Mutating) ex:
```js
[1, 2, 3].concat([4, 5, 6]);
```
- u can use it instead of push.
---
#### .Reduce():
- The `reduce` method allows for more general forms of array processing, and it's possible to show that both `filter` and `map` can be derived as special applications of `reduce`.
- It's Call back function consists of 4 arguments:
	1. accumulator : which gets assigned.
	2. The current element being processed.
	3. the index of that element.
	4. the array of reduce.
ex : 
```js
const users = [
  { name: 'John', age: 34 },
  { name: 'Amy', age: 20 },
  { name: 'camperCat', age: 10 }
];

const sumOfAges = users.reduce((sum, user) => sum + user.age, 0);
console.log(sumOfAges);
```
---
#### .Sort():
- The `sort` method sorts the elements of an array according to the callback function.
- if not givin a call back function it sort according to unicode order.
ex :
```js
function ascendingOrder(arr) {
  return arr.sort(function(a, b) {
    return a - b;
  });
}

ascendingOrder([1, 5, 2, 3, 4]); // return 1 2 3 4 5
```
-  If `compareFunction(a,b)` returns a value less than 0 for two elements `a` and `b`, then `a` will come before `b`. If `compareFunction(a,b)` returns a value greater than 0 for two elements `a` and `b`, then `b` will come before `a`. If `compareFunction(a,b)` returns a value equal to 0 for two elements `a` and `b`, then `a` and `b` will remain unchanged.
- it __mutates__ array.
---
#### .Split() :
- it splits method to array of strings.
- it takes argument as a delimiter.
- ex : 
```js
const str = "Hello World";
const bySpace = str.split(" ");

const otherString = "How9are7you2today";
const byDigits = otherString.split(/\d/);
```
- strings are immutable so its easy so split it .
---
#### .Join():
- it is used to join elements of an array to create a string.
- it takes argument as a delimiter that is used to separate arr elements in string.
- ex : 
```js
const arr = ["Hello", "World"];
const str = arr.join(" ");
```
---
#### .every():
- The `every` method works with arrays to check if _every_ element passes a particular test.
- it returns boolean value if all are true else false ex:
```js
const numbers = [1, 5, 8, 0, 10, 11];

numbers.every(function(currentValue) {
  return currentValue < 10; // return false.
});
```
---
#### .some():
- The Some method works with arrays to check if any element passes a particular test
- It returns a Boolean value - `true` if any of the values meet the criteria, `false` if not.
- ex :
```js
const numbers = [10, 50, 8, 220, 110, 11];

numbers.some(function(currentValue) {
  return currentValue < 10; // return true
});
```
---
#### Currying : 
The arity of a function is the number of arguments it requires. Currying a function means to convert a function of N arity into N functions of arity 1.
ex : 
```js
function unCurried(x, y) {
  return x + y;
}
//first way
function curried(x) {
  return function(y) {
    return x + y;
  }
}
//second way
const curried = x => y => x + y

curried(1)(2)
```
---
#### .includes ():
it is a function used to know if an array includes something.