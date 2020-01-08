# for in、for of、forEach的区别

### for in 

1. 只遍历可循环属性
2. 循环的输出顺序问题：先遍历**整数**属性（按照**升序**），其他属性按照创建顺序遍历
3. 对于数组中的属性（如：test： testing），只有for-in循环才能打印出这种键值对

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
var arr = [0, , null, 1, undefined, 2, 3]

arr.test = 'testing'

for(var item in arr){
  console.log('in`````', item, arr[item])
  // ["0", "2", "3", "4", "5", "6", "test"]
   
  // 0 0
  // 2 null
  // 3 1
  // 4 undefined
  // 5 2
  // 6 3
  // test testing
}

for(var item of arr){
   console.log('of`````', item)
  // [0, undefined, null, 1, undefined, 2, 3]  
}

arr.forEach(element => {
  console.log('forEach```````', element)
  // [0, null, 1, undefined, 2, 3] 
})

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

1. for-of不会跳过，默认为undefined。
2. for-in、forEach遇数组空项会跳过，for-in循环遇数组空项key值发生变化

### forEach

1. 不能使用break，continue跳出循环，不同于for-in、for-of



