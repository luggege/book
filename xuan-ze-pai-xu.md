### 选择排序

> 每轮循环中将第一个设为最小值，和之后的每一个元素相比，标记出最新的最小值下标，该轮结束后和第一个值交换，n - 1轮后升序排序

```js
let arr = [29, 10, 19, 9, 33];
for(let i = 0; i < arr.length - 1; i++) {
    let minIndex = i;
    for(let j = i + 1; j < arr.length; j++) {
        if(arr[j] < arr[minIndex]) {
            minIndex = j;
        }
    }
    let temp = arr[i];
    arr[i] = arr[minIndex];
    arr[minIndex] = temp;
    console.log(arr)
}
```



