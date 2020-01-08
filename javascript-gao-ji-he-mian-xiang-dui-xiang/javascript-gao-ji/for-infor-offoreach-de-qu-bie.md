# for in、for of、forEach的区别

### for in 

```javascript
一、
var obj  = {
  2: 'aaa',
  c: 333,
  1: 'bbb',
  a: 111,
  3: 'ccc',
  d: 222
}

obj.b = "ddd"

for(let item of obj){
  console.log('of````````', item)
}
//Uncaught TypeError: obj[Symbol.iterator] is not a function


for(let i in obj){
  console.log('in````````', i, obj[i])
}
// in```````` 1 bbb
// in```````` 2 aaa
// in```````` 3 ccc
// in```````` c 333
// in```````` a 111
// in```````` d 222
// in```````` b ddd
```

### for of

### forEach



