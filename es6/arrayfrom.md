### Array.from\(\)：将一个\*_类数组对象_\*或\*_可遍历对象_\*转换成真正的\*_数组_\*

> 类数组/伪数组：按照索引存储数据，且有**length**属性的对象

* 将**类数组**对象转换为真正的数组
* ```js
  let arrayLike = {
      0: 'tom', 
      1: '65',
      2: '男',
      3: ['jane','john','Mary'],
      'length': 4
  }
  let arr = Array.from(arrayLike)
  // ["tom", "65", "男", ['jane','john','Mary']]

  // ES5的写法
  // [].slice.call(arrayLike)
  ```
* 函数内部的**arguments对象**转为真正的对象

* ```js
  function foo () {
      var args = Array.from(arguments)
  }
  ```
* 将**Set结构**的数组转为真正的数组

* ```js
  let set = new Set([1, 2, 3, 2])
  let arr1 = Array.from(set)
  // [1, 2, 3]

  //可以传第二个参数，类似于数组的map方法，对里边对每一项进行处理
  console.log(Array.from(set, item => item + 1))
  // [2, 3, 4]
  ```
* 将**字符串**转换为数组

* ```js
  const str = Array.from('abbcd')
  // ["a", "b", "b", "c", "d"]
  ```
* Array.from的第二个参数：函数，类似于数组的map\(\)方法

* ```js
  Array.from([1, 2, 3, 4], x => x * x)
  // [1, 4, 9, 16]

  //等同于
  Array.from(arrayLike).map(x => x * x)
  ```

  ```js
  Array.from({length: 3}, x => 'jack')
  ```



