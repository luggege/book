### 冒泡排序

> 执行n-1轮，每一轮的第一个元素和后边的每一个元素比较，若前者大于后者则交换，每一轮最小的排在数组的最前边

![](/assets/maopao.gif)

```js
let arr = [1, 5, 2, 4, 3];
for(let i = 0; i < arr.length - 1; i++) {
    // console.log('i:', i, '--->', arr[i]);
    for(let j = i + 1; j < arr.length; j++) {
        // console.log('j', j, arr[j])
        if(arr[i] > arr[j]) {
            let temp;
            temp = arr[i];
            arr[i] = arr[j];
            arr[j] = temp;
        }
    }
    console.log(arr)
}
```

时间复杂度：O\(n^2\)  
空间复杂度：O\(n\)

