# for in、for of、forEach的区别

### for in 

#### 只遍历可循环属性

#### 循环的输出顺序问题

先遍历整数属性（按照升序），其他属性按照创建顺序遍历

```javascript
1、Object
var obj  = {
  2: 'aaa',
  c: 333,
  1: 'bbb',
  a: 111,
  3: 'ccc',
  d: 222
}

obj.b = "ddd"

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

for(let item of obj){
  console.log('of````````', item)
}
//Uncaught TypeError: obj[Symbol.iterator] is not a function

2、Array
var arr = [0, null, 1, undefined, 2, 3];

for(var item in arr){
  console.log('in`````', item)
  // ["0", "1", "2", "3", "4", "5"]
}

for(var item of arr){
   console.log('of`````', item)
  // [0, null, 1, undefined, 2, 3]
}

3、String
var str = 'aaabbbccc'

for(let item in str){
  console.log('in`````', item)
}
// in````` 0
// in````` 1
// in````` 2
// in````` 3
// in````` 4
// in````` 5
// in````` 6
// in````` 7
// in````` 8

for(let item of str){
  console.log('of`````', item)
}
// of````` a
// of````` a
// of````` a
// of````` b
// of````` b
// of````` b
// of````` c
// of````` c
// of````` c
```

### for of

### forEach



