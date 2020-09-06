# 删除数组多项值

问题：删除数组中的某两项值

```javascript
var arr = [1, 2, 3, 4, 5];
for(var i = 0; i < arr.length; i++){
    console.log('arr.length`````', arr.length);
    console.warn('i``````````````', i);
    console.log('arr[i]`````````', arr[i]);
    if(arr[i] === 2 || arr[i] === 3){
        arr.splice(i, 1);
    }
    console.log(arr);
}
-----------结果-----------
[Log] arr.length````` – 5
[Warning] i`````````````` – 0
[Log] arr[i]````````` – 1
[Log] [1, 2, 3, 4, 5] (5)
[Log] arr.length````` – 5
[Warning] i`````````````` – 1
[Log] arr[i]````````` – 2
[Log] [1, 3, 4, 5] (4)
[Log] arr.length````` – 4
[Warning] i`````````````` – 2
[Log] arr[i]````````` – 4
[Log] [1, 3, 4, 5] (4)
[Log] arr.length````` – 4
[Warning] i`````````````` – 3
[Log] arr[i]````````` – 5
[Log] [1, 3, 4, 5] (4)
```

结果：数组中为3的那一项并没有删掉

分析：for循环的（i &lt; arr.length）的**长度length**在删掉为2的那一项后**改变**为4，下一轮中的i此时已变为2，而arr\[2\]是4，成功避开为3的那一项，因此并没有被遍历到被删掉。

解决：**倒序遍历数组**，防止因删掉数组中的某一项后，继续用下标查找**漏遍历**某一项

```javascript
var arr = [1, 2, 3, 4, 5];
for(var i = arr.length - 1; i >= 0; i--){
    console.log('arr.length`````', arr.length);
    console.warn('i``````````````', i);
    console.log('arr[i]`````````', arr[i]);
    if(arr[i] === 2 || arr[i] === 3){
        arr.splice(i, 1);
    }
    console.log(arr);
}
-----------结果-----------
[Log] arr.length````` – 5
[Warning] i`````````````` – 4
[Log] arr[i]````````` – 5
[Log] [1, 2, 3, 4, 5] (5)
[Log] arr.length````` – 5
[Warning] i`````````````` – 3
[Log] arr[i]````````` – 4
[Log] [1, 2, 3, 4, 5] (5)
[Log] arr.length````` – 5
[Warning] i`````````````` – 2
[Log] arr[i]````````` – 3
[Log] [1, 2, 4, 5] (4)
[Log] arr.length````` – 4
[Warning] i`````````````` – 1
[Log] arr[i]````````` – 2
[Log] [1, 4, 5] (3)
[Log] arr.length````` – 3
[Warning] i`````````````` – 0
[Log] arr[i]````````` – 1
[Log] [1, 4, 5] (3)
```

### forEach、map、some、every、filter

```js
1.forEach没有返回值，不能跳出循环
[1, 4, 9, 16].forEach((value, key, array) => {
    console.log(value, key, array)
})

2.map有返回值
[1, 4, 9, 16].map(x => x*2)
// [2, 8, 18, 32]

[1, 4, 9, 16].some((value, key, array) => {
    return value > 4
})
// true

[1, 4, 9, 16].every((value, key, array) => {
    return value > 4
})
// false

[1, 4, 9, 16].filter((value, key, array) => {
    return value > 4
})
//[9, 16]
```



