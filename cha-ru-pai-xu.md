### 插入排序（找最小值）

> 执行n-1轮，每轮循环中，从后边的元素开始和前边的元素相比，如果后边比前边的小则交换，这个交换后的值继续和前边比较，直到不小于，进入下轮循环，以此往复。。。n - 1轮升序排列

```js
let arr = [29, 10, 19, 9, 33];
for(let i = 0; i < arr.length - 1; i++) {
    for(let j = i + 1; j > 0; j--) {
        // j - 1：和前一个相比
        if(arr[j] < arr[j - 1]) {
            let temp = arr[j];
            arr[j] = arr[j - 1];
            arr[j - 1] = temp
        }
    }
    console.log(arr)
}
```

时间复杂度：O\(n^2\)  
空间复杂度：O\(n\)

