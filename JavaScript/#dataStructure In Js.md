#### - The Array:
- we can access the array by its arr.length func.
- we can use an array notation by []
- __.push()__ adds Element to the end of array.
- .__unshift()__ adds Element to the beginning of array.
- ._pop()_ Removes 1 element at a time from the end of arr and we can also return it at a var.
- ._shift()_ Removes 1  element at a time from the beginning of arr and we can also return it at a var.
- #####  .splice() removes any number of elements from anywhere in the array: 
	- it takes 3 parameters  but we will focus on two: 1-index , 2-Number of elements to delete and also return them in another array if you want to.
	- the third parameter is used to add one or more elements to the array at at same index example : 
	```js
	const numbers = [10, 11, 12, 12, 15];
	const startIndex = 3;
	const amountToDelete = 1;
	numbers.splice(startIndex, amountToDelete, 13, 14);
	console.log(numbers);
	```
- ### .slice() copy or extract given number of elements to new array:
	-It takes two parameters : 1- The first to begin extraction. 2- indext at which end extraction which is not taken ex:
```js
let weatherConditions = ['rain', 'snow', 'sleet', 'hail', 'clear'];

let todaysWeather = weatherConditions.slice(1, 3);
// it will not take hail.
```
- ####  Like .slice we got in Es6 a way to copy all the elements in array to another by (...) spread operator ex:
```js
let thisArray = [true, true, undefined, false, null];
let thatArray = [...thisArray];
```
#####  - we can also merge two arrays or add any array to the my arr by Spread Operator ex:
```js
let thisArray = ['sage', 'rosemary', 'parsley', 'thyme'];

let thatArray = ['basil', 'cilantro', ...thisArray, 'coriander'];
```
- .indexOf() to know the presence of an element in array ex:
```js
let fruits = ['apples', 'pears', 'oranges', 'peaches', 'pears'];

fruits.indexOf('dates');
fruits.indexOf('oranges');
fruits.indexOf('pears');
```
### - iterating In Array:
##### 1. For loop: it is the most flexible way and offers us the greatest control ex : 
```js
function greaterThanTen(arr) {
  let newArr = [];
  for (let i = 0; i < arr.length; i++) {
    if (arr[i] > 10) {
      newArr.push(arr[i]);
    }
  }
  return newArr;
}

greaterThanTen([2, 12, 8, 14, 80, 0, 1]);
```
---
- we can make nested arrays ex :
```js
let nestedArray = [
//lvl2
  ['deep'],
  [ //lvl3
    ['deeper'], ['deeper'] 
  ],
  [
    [ //lvl4
      ['deepest'], ['deepest']
    ],
    [
      [ //lvl5
        ['deepest-est?']
      ]
    ]
  ]
];
```
#### - .filter(): it takes function and return the return of it.

---
#### Objects :
1. Objects are collections of key value pairs their keys are called properties ex:
```js
const tekkenCharacter = {
  player: 'Hwoarang',
  fightingStyle: 'Tae Kwon Doe',
  human: true
};
```
2. we can add property by doint .property = what ever we want.
3. another way to add propert by ['Hair color'] = msln.
4. we can use both but we use bracket notation when there is spaces or when using variable ex:
```js
const eyes = 'eye color';

tekkenCharacter[eyes] = 'brown';
```
5. we can make nested objects as follows : 
```js
let nestedObject = {
  id: 28802695164,
  date: 'December 31, 2016',
  //data is an object of object.
  data: {
    totalUsers: 99,
    online: 80,
    onlineStatus: {
      active: 67,
      away: 13,
      busy: 8
    }
  }
};
```
6. to access a nested object from prev ex:
```js
nestedObject.data.onlineStatus.busy = 10;
```
7. we use the bracket notation in dynamic allocation of data by it's properties or keys ex: byshof lw mwgooda wla l2.
```js
let selectedFood = getCurrentFood(scannedItem);
let inventory = foods[selectedFood];
```
8. we use the **Delete** keyword to delete property.
#### 9. .hasOwnProperty() & in : they are used to check for a property ex:
```js
// returns true or false.
users.hasOwnProperty('Alan');
'Alan' in users;
```
10. We Can Iterate Through The keys in for in loop ex:
```js
for (let user in users) {
  console.log(user);
}
```
##### 11. We can get The Object Keys by using __Object.keys(obj)__ it takes object as argument and return arr of strings.S
