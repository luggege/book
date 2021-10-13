### 插入排序

> 每轮循环中，从后边的元素开始和前边的元素相比，如果后边比前边的小则交换位置，这个交换后的值继续和前边比较，直到不小于，进入下轮循环，以此往复。。。n - 1轮升序排列

```js
let arr = [29, 10, 19, 9, 33];
for(let i = 0; i < arr.length - 1; i++) {
    for(let j = i + 1; j > 0; j--) {
        if(arr[j] < arr[j - 1]) {
            let temp = arr[j];
            arr[j] = arr[j - 1];
            arr[j - 1] = temp
        }
    }
    console.log(arr)
}
```



