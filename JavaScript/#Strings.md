## In strings we can split strings to arrays by splitter spaces or anything.
### we Can join them again using .join();
### so if you want an arr to = other u got two ways
1. copy by slice();
2. copy with for in loop.
---

### String.From CharCode():
- used to change ascii to char.
The **`String.fromCharCode()`** static method returns a string created from the specified sequence of UTF-16 code units.
- we can also use it to turn from binary by using parse int as follows :
```js
letters[i] =String.fromCharCode(parseInt(bin[i],2));
```
---
###  CharCodeAt():
used to change char to ascii.
The **`charCodeAt()`** method returns an integer between `0` and `65535` representing the UTF-16 code unit at the given index.

---
to look for something in object in array:
```js
return str.split('')
.map(entity=>html[entity]||entity)
.join('');
}
```
