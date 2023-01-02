- First the Regex doesn't need " " it only need /regex/ to be made.
- **.Test** it is used to know if the regex u're using is in the string u're giving
syntax :
```Js
let testStr= "freeCodeCamp";
let testRegex = /Code/;
testRegex.test(testStr);
```

- if u use /code/ this will only get u code c small not CODE or Code
- using **|** or operator to find more things in the regex:
```JS:
/yes|no|maybe/;
```
- **.match** it is used to get a match of regex and examples:
```js
"Hello, World!".match(/Hello/);
let ourStr = "Regular expressions";
let ourRegex = /expressions/;
ourStr.match(ourRegex);
```
- to put two flags in same regex bnktbhom gmb b3d ex: ig.
- **wild Card Character _(.)_** :it is used to match any char 
ex:
```js
let humStr = "I'll hum a song";
let hugStr = "Bear hug";
let huRegex = /hu./;
huRegex.test(humStr);
huRegex.test(hugStr);
```
- if you put a pattern in \[\]  then u're using **Character classes** which allow u to define a group of characters ex:
```js
let bigStr = "big";
let bagStr = "bag";
let bugStr = "bug";
let bogStr = "bog";
let bgRegex = /b[aiu]g/;
bigStr.match(bgRegex);
bagStr.match(bgRegex);
bugStr.match(bgRegex);
bogStr.match(bgRegex);
```
- defining ranges by using [-] - in [] used to define range chars or numbers ex:
```js
let catStr = "cat";
let batStr = "bat";
let matStr = "mat";
let bgRegex = /[a-e]at/;
catStr.match(bgRegex);
batStr.match(bgRegex);
matStr.match(bgRegex);
```
another ex combining two ranges:
```js
let jennyStr = "Jenny8675309";
let myRegex = /[a-z0-9]/ig;
jennyStr.match(myRegex);
```
- **negated char set** _(^)_ : it is used to match the opposite of it ex:
`/[^aeiou]/gi` 
it will not match the vowels.
- __(+)__: it matches __one or more__ if one after the other it will be in the same string if not then in two different strings like \[aa\] or \[a,a\]
- __(\*)__ :it matches *zero or more* times
- __(?)__ :it matches zero or __at most 1__ 
- __(^)__: outside of a set it is used to find something at **the beginning** ex:
```js
let firstString = "Ricky is first and can be found.";
let firstRegex = /^Ricky/;
firstRegex.test(firstString);
let notFirst = "You can't find Ricky now.";
firstRegex.test(notFirst);
```
- __($)__: Used to search for chars at the end ex:
```js
let theEnding = "This is a never ending story";
let storyRegex = /story$/;
storyRegex.test(theEnding);
let noEnding = "Sometimes a story will have to end";
storyRegex.test(noEnding);
```
- __\w__ :  it is a shortcut for __\[A-Za-z0-9_\]__
- __\W__ : it is a shortcut for   __\[^A-Za-z0-9_\]__
- __\d__ :it is a shortcut for __\[0-9\]__ 
- __\D__ :it is a shortcut for __\[^0-9\]__ 
- __\s__: search for _whitespaces_.
- __\S__: search for **Non-Spaces** : `[^ \r\t\f\n\v]`.
- __{}__ quantity identifiers: it is used to match range of repetition of char ex:
```js
let A4 = "aaaah";
let A2 = "aah";
let multipleA = /a{3,5}h/;
multipleA.test(A4);
multipleA.test(A2);
```
that woud return true for A4 and false for A2.
- U can also use quantity Identifiers to match only lower number of patterns or only higher number of patterns. ex:
```js
let A4 = "haaaah";
let A2 = "haah";
let A100 = "h" + "a".repeat(100) + "h";
let multipleA = /ha{3,}h/;
multipleA.test(A4);
multipleA.test(A2);
multipleA.test(A100);
```
- we can also specify exact number by giving only one number of repetitions.
- __.repeat__: is used to repeat string for number of times u need.
- LookAheads: 
	1. Positive (?=...): search if the elements in the ... is there but not match it
	2. Negative (?!...): search if the elements in the ... is not there and also don't match it.
- (|) : used to check for more than one regex with same chars but with different other chars
```js
let testStr = "Pumpkin";
let testRegex = /P(engu|umpk)in/;
testRegex.test(testStr);
```
- Capture group: makes u use a regex and repeat it as long as you want by using \1 for once and \2 for twice and so on ex:
```js
let repeatRegex = /(\w+) \1 \1/;
repeatRegex.test(repeatStr); // Returns true
repeatStr.match(repeatRegex); // Returns ["row row row", "row"]
```
- Search and __.replace__: it takes two parameters(regex,to be changed with).
```js
let wrongText = "The sky is silver.";
let silverRegex = /silver/;
wrongText.replace(silverRegex, "blue");
"Code Camp".replace(/(\w+)\s(\w+)/, '$s2 $s1');
```
it will be Camp code
- to remove white spaces from start and end we get the regex and then replace it with " ".
#### Flags in regex:
1. **i** -> used to ignore case.
2. g -> used to extract pattern more than once ex:
```js
let repeatRegex = /Repeat/g;
testStr.match(repeatRegex);
```
3. 

