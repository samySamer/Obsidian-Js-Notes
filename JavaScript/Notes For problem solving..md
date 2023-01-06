1. in Regex we can use ?=to see if something is followed by something i need ex : 
```js
function spinalCase(str) {

  return str.split(/\W|_|(?=[A-Z])/).map(item=>item.toLowerCase()).join('-');

}

console.log(spinalCase("AllThe-small Things"))

spinalCase('This Is Spinal Tap');
```
- here i used ?= to see if there is any capital letters so i can split the strings before the capitals.
---
### When wanting to remove duplicates we can use : 
#### 1. Set:
- The **`Set`** object lets you store unique values of any type, whether [primitive values](https://developer.mozilla.org/en-US/docs/Glossary/Primitive) or object references.
 ex:
```js
  return [...new Set(newArr)];
```
2. Using filter :
```js //see the index of each value and if it is equal to the index of loop remove it.
newArr.filter((item,pos,arr) => {
   return arr.indexOf(item)==pos;
   }
```
---
### Fibonacci Odd numbers :
1. so this was a very odd one to think about but lets start : 
	1. when we think about fibonacci we go like this : 1,1,2,3,5,8 and so on
	2. so i thought of making an array starting with these first ones then pushing every sum to it one by one like : 1+1 =2 then 2+1=3 and so on in a loop as follows :
```js
let fib=[1,1]; // making pair
  let c=0;
  let sum=0;
  let z=0;
  while(c<num)//looping to do the fib
  {
    fibsums=fib[c]+fib[c+1];//getting the sum for each iteration
    if(sum<=num)
    {
      fib.push(fibsums);//adding the new sum in the array like [1,1,2,3,5,8]
    }
    c++;
  }
```
	3. then after the loop filtering the array from the even numbers by using filter and modoulous:

```js
	  let x= fib.filter(item=>item%2 !==0);
```
	4. after that i got them all in one array so i got two choices going for traditional for loop or going for a map so i have gone for the easier one by using map:
```js
	  x.map(item=>z+=item);
```
	5. and that's it the final code :
```js
function sumFibs(num) {
  let fib=[1,1];
  let c=0;
  let sum=0;
  let z=0;
  while(c<num)
  {
    fibsums=fib[c]+fib[c+1];
	 if(sum<=num)
    {
    fib.push(sum);
    }
    c++;
  }
  let x= fib.filter(item=>item%2 !==0);
  x.map(item=>z+=item);
  return z;
}

```
### Prime numbers :
1.
```js
function sumPrimes(num) { // Helper function to check primality 
function isPrime(num) 
{ for (let i = 2; i <= Math.sqrt(num); i++)
{ if (num % i == 0) return false; } 
 return true; }
// Check all numbers for primality
let sum = 0; 
for (let i = 2; i <= num; i++) 
{ if (isPrime(i))
sum += i; 
}
return sum; 
}
```
---
### least common multiple:
```js
function smallestCommons(arr) {
  const [min, max] = arr.sort((a, b) => a - b);
  const range = Array(max - min + 1).fill(0).map((_, i) => i + min);
    console.log(range);
  let lcm = (a,b)=> a*b/gcd(a,b);
  let gcd = (a,b)=>{
    if(!b)
    return a;
    return gcd(b,a%b);
  }
  return range.reduce((mult,curr)=>lcm(mult,curr)) ;
}
console.log(smallestCommons([1,5]));
smallestCommons([1,5]);
```
---
### SteamRoller : 
- this problem we have a function that contains alot of arrays containing arrays so when we think about something contain something we go for recursion so i first searched for something to know if it is object or array and if array we recurse as follows : 
```js
function steamrollArray(arr) {
  let x=[];
  for(let i=0;i<arr.length;i++)
  {
    if(Array.isArray(arr[i]))
    {
       x= x.concat(steamrollArray(arr[i]));
    }else
    x=x.concat(arr[i]);
  }
  return x;
}

steamrollArray([1, [2], [3, [[4]]]]);
```
---
### Roman Numeral Converter : 
- so lets start first i had to think of a way to get through each number and add it if its bigger so i make an object to look for each one key by its value : 
```js
 let look={'M':1000,'CM':900, 'D':500,'CD':400,'C':100,'XC':90,'L':50,'XL':40,'X':10,'IX':9,'V':5,'IV':4,'I':1};
```
- we needed to look for each char with its value so we made a for in loop to look for it and looking for the num if its bigger than the largest number then we do another loop looking for it and then minus it like this : 
```js
for(let i in look)
 {
   if(num>=look[i])
   {
     while(num>=look[i])
     {
       x+=i;
       num-=look[i];
     }
   }
 }
```
- and that's it we return then x .
- the whole code : 
```js
function convertToRoman(num) {
  let x='';

 let look={'M':1000,'CM':900, 'D':500,'CD':400,'C':100,'XC':90,'L':50,'XL':40,'X':10,'IX':9,'V':5,'IV':4,'I':1};

 for(let i in look)
 {
   if(num>=look[i])
   {
    while(num>=look[i])
     {
       x+=i;
       num-=look[i];
     }
   }
 }
 return x;
}
```
---
### Project Caeser Cipher : 
- This project want us to do A Rot 13 decoder so i started as follows :
	1. What is rot 13 ?
		- it is simply an encoding way at which if the Char we have from the first 13 numbers we +13
		- if the char we have from the second 13 numbers we - 13.
	2. after knowing what is rot 13 so i started to think of it as follows first we need to turn the chars to numbers so i can use their asciis to add the number to its ascii so i used **.charCodeAt** it simply turns the string chars to ascii code numbers and it takes 1 char at once so i did it in a loop :
```js
for(let i=0;i<str.length;i++)
  {  
   decode.push(str.charCodeAt(i));
  }
```
---
	3. after that i started to do another loop if to see the numbers smaller than 78 to Add 13 to them and the ones bigger than 13 to minus 13 from it but then i got a very weird erorr in my head what about the spaces and dashes so to make it more specific i used from the start of chars to the end of chars as follows:
```js
for(let i=0;i<decode.length;i++)
{
  if(decode[i]<78 &&decode[i]>=65)
  {
    decode[i]= decode[i]+13;
  }
  else if(decode[i] >=78 && decode[i] <=90)
  {
    decode[i]-=13;
  }
```
---
	4. lastly i returned them to characters again by using map to loop on them and **String.fromCharCode** and joined them:
```js
  return decode.map((item)=>String.fromCharCode(item)).join('');
```
The whole code : 
```js
function rot13(str) {
  let decode =[]
  for(let i=0;i<str.length;i++)
  {
    decode.push(str.charCodeAt(i));
  }
for(let i=0;i<decode.length;i++)
{
  if(decode[i]<78 &&decode[i]>=65)
  {
    decode[i]= decode[i]+13;
    }
  else if(decode[i] >=78 && decode[i] <=90)
  {
    decode[i]-=13;
  }
}  
  return decode.map((item)=>String.fromCharCode(item)).join('');
}
```
---
### Telephone Number Validator:
- So this time we got a problem to see if the following number is going to be a telephone number so i did it with regex lets start:
	1. so we got the following test cases :
```js
555-555-5555  
(555)555-5555  
(555) 555-5555  
555 555 5555  
5555555555  
1 555 555 5555
```
---
	2. first thing got in my mind 