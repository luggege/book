### Array.from\(\)将一个类对象或可遍历对象转换成真正的数组

```js
1. 将类数组对象转换为真正的数组
let arrayLike = {
    0: 'tom', 
    1: '65',
    2: '男',
    3: ['jane','john','Mary'],
    'length': 4
}
let arr = Array.from(arrayLike)
// ["tom", "65", "男", ['jane','john','Mary']]

2. 将Set结构的数组转为真正的数组
let set = new Set([1, 2, 3, 2])
let arr1 = Array.from(set)
// [1, 2, 3]

可以传第二个参数，类似于数组的map方法，对里边对每一项进行处理
console.log(Array.from(set, item => item + 1))
// [2, 3, 4]

3. 将数组转换为数组
const str = Array.from('abbcd')
// ["a", "b", "b", "c", "d"]

4. Array.from参数是一个真正的数组
console.log(Array.from([1, 2, 3, 3]))
// [1, 2, 3, 3]
```



