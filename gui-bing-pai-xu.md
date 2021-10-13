### 归并排序

> 分治策略

```js
let arr = [29, 10, 19, 9, 33];
let rec = (arr) => {
    if(arr.length <= 1) {
        return arr
    }
    let midPoint = Math.floor(arr.length / 2);
    let left = arr.slice(0, midPoint);
    let right = arr.slice(midPoint);
    console.log('111', left, right, arr)
    let sortLeft = rec(left);
    let sortRight = rec(right);
    console.log('222', sortLeft, sortRight, arr);
    let temp = [];
    while(sortLeft.length && sortRight.length) {
        if(sortLeft[0] < sortRight[0]) {
            temp.push(sortLeft.shift());
        }else {
            temp.push(sortRight.shift());
        }
    }
    console.log('temp: ', temp, sortLeft, sortRight, temp.concat(sortLeft, sortRight));
    return temp.concat(sortLeft, sortRight);
}
rec(arr)
```



